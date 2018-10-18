---
title: 舊版語言服務中的程式碼重新格式化 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53cdbc963c7701d0073634ef133c2ef2d54fa9a4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211025"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>在舊版語言服務中將程式碼重新格式化
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]原始程式碼可能被重新格式化的正規化使用縮排和空格。 這可以包括插入或移除空格或在每一行開頭的索引標籤、 新增線條之間的新行或取代空格與定位點或空格的索引標籤。  
  
> [!NOTE]
>  **請注意**插入或刪除新行字元可能會影響標記，例如中斷點和書籤，但新增或移除空格或定位點不會影響標記。  
  
 使用者可以選取啟動重新格式化作業**格式化選取範圍**或是**格式化文件**從**進階**功能表上的**編輯**功能表。 插入程式碼片段或特定的字元時，也會觸發重新格式化作業。 例如，當您輸入右括號，在 C# 中，相符的左大括號和右大括號之間的所有項目會自動縮排到適當的層級。  
  
 當[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]傳送**格式化選取範圍**或**格式化文件**命令語言服務中，以<xref:Microsoft.VisualStudio.Package.ViewFilter>類別會呼叫<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>中的方法<xref:Microsoft.VisualStudio.Package.Source>類別。 若要支援的格式設定，您必須覆寫<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>方法，並提供您自己的格式化程式碼。  
  
## <a name="enabling-support-for-reformatting"></a>啟用重新格式化的支援  
 若要支援的格式設定，`EnableFormatSelection`的參數<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>必須設為`true`當您註冊 VSPackage。 這會設定<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A>屬性設`true`。 <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>方法會傳回這個屬性的值。 它會傳回 true，如果<xref:Microsoft.VisualStudio.Package.ViewFilter>類別會呼叫<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>。  
  
## <a name="implementing-reformatting"></a>實作重新格式化  
 若要實作重新格式化，您必須衍生的類別<xref:Microsoft.VisualStudio.Package.Source>類別並覆寫<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>方法。 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>物件會描述要格式化的範圍和<xref:Microsoft.VisualStudio.Package.EditArray>物件會保存在範圍上所做的編輯。 請注意，此範圍可以是整份文件。 不過，由於有可能是多個範圍所做的變更，所有變更都應該可在單一動作還原。 若要這樣做，換行中的所有變更<xref:Microsoft.VisualStudio.Package.CompoundAction>物件 （請參閱本主題中的 < 使用 CompoundAction 類別 > 一節）。  
  
### <a name="example"></a>範例  
 下列範例會確保單一空格每一個逗號後面中沒有選取範圍，除非逗號後面接著一個索引標籤或行結尾。 在行中的最後一個逗號刪除後後, 端空格。 請參閱 < 使用 CompoundAction 類別 > 一節，以查看如何呼叫這個方法是從本主題中的<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>方法。  
  
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
 所有重新格式化在一段程式碼完成應該是以單一動作還原。 這可以使用來完成<xref:Microsoft.VisualStudio.Package.CompoundAction>類別。 這個類別會包裝成單一的編輯作業上的文字緩衝的編輯作業的一組。  
  
### <a name="example"></a>範例  
 以下是如何使用的範例<xref:Microsoft.VisualStudio.Package.CompoundAction>類別。 請參閱本主題的範例，"實作支援的格式 」 一節中的範例`DoFormatting`方法。  
  
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
 [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)

