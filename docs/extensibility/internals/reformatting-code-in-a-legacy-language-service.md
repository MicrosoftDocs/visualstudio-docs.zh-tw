---
title: 在舊版語言服務中重新格式化程式碼 |Microsoft Docs
description: 瞭解如何啟用 Visual Studio 舊版語言服務的原始程式碼重新格式化支援。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0198ef145c3fbf6d0edcc6a95954794597fce0b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875584"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>在舊版語言服務中將程式碼重新格式化

在原始程式碼中，可以藉由正規化縮排和空白字元的使用來重新 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 格式化。 這可能包括在每一行的開頭插入或移除空格或索引標籤、在各行之間加入新行，或以空格取代空格或定位字元。

> [!NOTE]
> 插入或刪除換行字元可能會影響中斷點和書簽等標記，但新增或移除空格或索引標籤不會影響標記。

使用者可以從 [**編輯**] 功能表上的 [ **Advanced** ] 功能表選取 [**格式選取**] 或 [**格式化檔**]，以啟動重新格式化作業。 當插入程式碼片段或特定字元時，也可以觸發重新格式化作業。 例如，當您在 c # 中輸入右大括弧時，相符的左大括弧和右大括弧之間的所有內容都會自動縮排到適當的層級。

當 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 將 **格式選取** 或 **格式檔** 命令傳送至語言服務時， <xref:Microsoft.VisualStudio.Package.ViewFilter> 類別會呼叫 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> 類別中的方法 <xref:Microsoft.VisualStudio.Package.Source> 。 若要支援格式設定，您必須覆寫 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> 方法，並提供您自己的格式化程式碼。

## <a name="enabling-support-for-reformatting"></a>啟用重新格式化的支援

若要支援格式 `EnableFormatSelection` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 設定， `true` 當您註冊 VSPackage 時，的參數必須設定為。 這會將 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> 屬性設定為 `true` 。 方法會傳回 <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> 這個屬性的值。 如果傳回 true，則 <xref:Microsoft.VisualStudio.Package.ViewFilter> 類別會呼叫 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> 。

## <a name="implementing-reformatting"></a>執行重新格式化

若要執行重新格式化，您必須從類別衍生類別 <xref:Microsoft.VisualStudio.Package.Source> ，並覆寫 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> 方法。 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>物件會描述要格式化的範圍，而 <xref:Microsoft.VisualStudio.Package.EditArray> 物件會保存對範圍所做的編輯。 請注意，這個範圍可以是整份檔。 不過，由於可能會有多個對範圍進行的變更，因此所有變更在單一動作中都應該是可還原的。 若要這樣做，請將所有變更包裝在 <xref:Microsoft.VisualStudio.Package.CompoundAction> 物件中 (請參閱本主題中的「使用 CompoundAction 類別」一節) 。

### <a name="example"></a>範例

下列範例會確保選取範圍中的每個逗號之後都有一個空格，除非逗點後面接著一個索引標籤或在行尾。 刪除行最後一個逗號之後的尾端空白。 請參閱本主題中的「使用 CompoundAction 類別」一節，以瞭解如何從方法呼叫這個方法 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> 。

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

## <a name="using-the-compoundaction-class"></a>使用 CompoundAction 類別

在程式碼區段上完成的所有重新格式化，在單一動作中都應該是可還原的。 您可以使用類別來完成這項作業 <xref:Microsoft.VisualStudio.Package.CompoundAction> 。 這個類別會將文字緩衝區上的一組編輯作業包裝成單一的編輯作業。

### <a name="example"></a>範例

以下是如何使用類別的範例 <xref:Microsoft.VisualStudio.Package.CompoundAction> 。 如需此方法的範例，請參閱本主題中「實設定格式的支援」一節中的範例 `DoFormatting` 。

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
