---
title: 在舊語言服務中重新格式化代碼 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd3e83c7299298b16a6fb3178b189479a80e1728
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705916"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>在舊版語言服務中將程式碼重新格式化

在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]原始程式碼中可以通過規範化縮進和空格的使用來調整。 這可能包括在每行的開頭插入或刪除空格或製表符,在行之間添加新行,或者用空格替換空格。

> [!NOTE]
> 插入或刪除換行符可能會影響斷點和書籤等標記,但添加或刪除空格或製表符不會影響標記。

使用者可以通過從 **「編輯」** 選單上**的「進階**」功能表中選擇 **「格式選擇**」或 **「格式文件**」來啟動重新格式化操作。 插入代碼段或特定字元時,也可以觸發重新格式化操作。 例如,在 C# 中鍵入右大括弧時,匹配的打開大括弧和右大括弧之間的所有內容將自動縮進到適當的級別。

將[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**格式選擇**或**格式文件**命令發送到語言<xref:Microsoft.VisualStudio.Package.ViewFilter>服務時, 類別將<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A><xref:Microsoft.VisualStudio.Package.Source>呼叫類別的方法。 要支援格式設定,<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>必須重寫該方法並提供您自己的格式代碼。

## <a name="enabling-support-for-reformatting"></a>開啟對重新格式化的支援

要支援格式設定,`EnableFormatSelection`<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>必須在註冊 VSPackage 時`true`會設定為 。 這會設定<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A>到`true`。 該方法<xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>返回此屬性的值。 當傳回<xref:Microsoft.VisualStudio.Package.ViewFilter>True, 則類別<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>將呼叫 。

## <a name="implementing-reformatting"></a>實現重新格式化

要實現重新格式化,必須從<xref:Microsoft.VisualStudio.Package.Source>類派生一個類並重<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>寫 方法。 物件<xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>描述要格式化的範圍<xref:Microsoft.VisualStudio.Package.EditArray>, 並且物件保留在範圍上所做的編輯。 請注意,此範圍可以是整個文檔。 但是,由於對範圍可能進行了多次更改,因此所有更改都應在單個操作中可逆。 為此,在<xref:Microsoft.VisualStudio.Package.CompoundAction>物件中包裝所有更改(請參閱本主題中的"使用複合操作類"部分)。

### <a name="example"></a>範例

以下範例確保所選內容中的每個逗號之後都有一個空格,除非逗號後跟一個選項卡或位於行尾。 刪除行中最後一個逗號之後的尾隨空格。 請參閱本主題中的"使用複合操作類"部分,瞭解如何從<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>方法調用此方法。

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        private void DoFormatting(EditArray mgr, TextSpan span)
        {
            // Make sure there is one space after every comma unless followed
            // by a tab or comma is at end of line.
            IVsTextLines pBuffer = GetTextLines();
            if (pBuffer != null)
            {
                int    startIndex = span.iStartIndex;
                int    endIndex   = 0;
                string line       = "";
                // Loop over all lines in span
                for (int i = span.iStartLine; i <= span.iEndLine; i++)
                {
                    if (i < span.iEndLine)
                    {
                        pBuffer.GetLengthOfLine(i, out endIndex);
                    }
                    else
                    {
                        endIndex = span.iEndIndex;
                    }
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);

                    if (line.Length > 0)
                    {
                        int index = 0;
                        // Loop over all commas in line
                        while ((index = line.IndexOf(',', index)) != -1)
                        {
                            int spaceIndex = index + 1;
                            // Determine how many spaces after comma
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')
                            {
                                ++spaceIndex;
                            }

                            int      spaceCount      = spaceIndex - (index + 1);
                            string   replacementText = " ";
                            bool     fDoEdit         = true;
                            TextSpan editTextSpan    = new TextSpan();

                            editTextSpan.iStartLine  = i;
                            editTextSpan.iEndLine    = i;
                            editTextSpan.iStartIndex = index + 1;

                            if (spaceIndex == line.Length)
                            {
                                if (spaceCount > 0)
                                {
                                    // Delete spaces after a comma at end of line
                                    editTextSpan.iEndIndex = spaceIndex;
                                    replacementText = "";
                                }
                                else
                                {
                                    // Otherwise, do not add spaces if comma is
                                    // at end of line.
                                    fDoEdit = false;
                                }
                            }
                            else if (spaceCount == 0)
                            {
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')
                                {
                                    // Do not insert space if a tab follows
                                    // a comma.
                                    fDoEdit = false;
                                }
                                else
                                {
                                    // No space after comma so add a space.
                                    editTextSpan.iEndIndex = index + 1;
                                }
                            }
                            else if (spaceCount > 1)
                            {
                                // More than one space after comma, replace
                                // with a single space.
                                editTextSpan.iEndIndex = spaceIndex;
                            }
                            else
                            {
                                // Single space after a comma and not at end
                                // of the line, leave it alone.
                                fDoEdit = false;
                            }
                            if (fDoEdit)
                            {
                                // Add edit operation
                                mgr.Add(new EditSpan(editTextSpan, replacementText));
                            }
                            index = spaceIndex;
                        }
                    }
                    startIndex = 0; // All subsequent lines start at 0
                }
                // Apply all edits
                mgr.ApplyEdits();
            }
        }
    }
}
```

## <a name="using-the-compoundaction-class"></a>使用複合操作類別

在代碼部分上完成的所有重新格式化都應在單個操作中可逆。 這可以使用類<xref:Microsoft.VisualStudio.Package.CompoundAction>來完成。 此類將文字緩衝區上的一組編輯操作包裝為單個編輯操作。

### <a name="example"></a>範例

下面是如何使用<xref:Microsoft.VisualStudio.Package.CompoundAction>類的示例。 有關`DoFormatting`該方法的範例,請參閱本主題中的"實現格式化支援"部分中的範例。

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override void ReformatSpan(EditArray mgr, TextSpan span)
        {
            string description = "Reformat code";
            CompoundAction ca = new CompoundAction(this, description);
            using (ca)
            {
                ca.FlushEditActions();      // Flush any pending edits
                DoFormatting(mgr, span);    // Format the span
            }
        }
    }
}
```

## <a name="see-also"></a>另請參閱

- [舊版語言服務功能](legacy-language-service-features1.md)
