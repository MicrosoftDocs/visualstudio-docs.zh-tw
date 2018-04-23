---
title: 在舊版語言服務的程式碼重新格式化 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 392afbafc2ce15dbf7ee347efdf24ce1f7fe2301
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>重新格式化舊版語言服務中的程式碼

在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]原始程式碼可以重新格式化的正規化使用縮排和空格。 這可能包括插入或移除空格或在每一行開頭的索引標籤、 加入新行之間的行，或使用 tab 鍵或索引標籤，以空格取代空格。  
  
>**注意：**插入或刪除新行字元可能會影響標記，例如中斷點和書籤，但加入或移除空格或定位點不會影響標記。  
  
使用者可以選取啟動重新格式化作業**格式選取**或**格式化文件**從**進階**功能表**編輯**功能表。 插入程式碼片段或特殊字元時，也會觸發重新格式化作業。 例如，當您輸入右括號在 C# 中，相符的左大括號與右大括弧之間的所有項目是自動縮排至適當的層級。
  
當[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]傳送**格式選取**或**格式化文件**命令語言服務，<xref:Microsoft.VisualStudio.Package.ViewFilter>類別會呼叫<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>方法中的<xref:Microsoft.VisualStudio.Package.Source>類別。 若要支援的格式必須覆寫<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>方法並提供您自己的格式化程式碼。  
  
## <a name="enabling-support-for-reformatting"></a>啟用支援重新格式化  

若要支援的格式，`EnableFormatSelection`參數<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>必須設為`true`當您註冊您的 VSPackage。 這會設定<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A>屬性`true`。 <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>方法會傳回這個屬性的值。 如果為 true，傳回<xref:Microsoft.VisualStudio.Package.ViewFilter>類別會呼叫<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>。  
  
## <a name="implementing-reformatting"></a>實作重新格式化

若要實作重新格式化，您必須衍生自<xref:Microsoft.VisualStudio.Package.Source>類別並覆寫<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>方法。 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>物件描述要格式化的範圍和<xref:Microsoft.VisualStudio.Package.EditArray>物件會保存在範圍上進行的編輯。 請注意，此範圍可以是整份文件。 不過，因為有可能會為範圍的多個變更，所有變更都應該可在單一動作中回復。 若要這樣做，換行中的所有變更<xref:Microsoft.VisualStudio.Package.CompoundAction>物件 （請參閱本主題中的 < 使用 CompoundAction 類別 > 一節）。

### <a name="example"></a>範例  

下列範例會確保單一空格每一個逗號後面中沒有選取項目，除非逗號後面接著一個索引標籤或行結尾。 之後會刪除列中的最後一個逗號後, 端空格。 請參閱 < 若要查看如何呼叫這個方法是從本主題的 < 使用 CompoundAction 類別 > 一節<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>方法。  

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
 
所有重新格式化完成的程式碼區段應該可在單一動作中回復。 這可以透過<xref:Microsoft.VisualStudio.Package.CompoundAction>類別。 這個類別會包裝成單一的編輯作業文字的緩衝區上的編輯作業的一組。  
  
### <a name="example"></a>範例

以下是如何使用的範例<xref:Microsoft.VisualStudio.Package.CompoundAction>類別。 請參閱本主題的範例 「 實作支援的格式 」 一節中範例`DoFormatting`方法。  
  
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

[舊版語言服務功能](legacy-language-service-features1.md)