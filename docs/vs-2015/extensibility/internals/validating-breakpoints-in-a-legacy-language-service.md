---
title: 舊版語言服務中驗證中斷點 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f3fbfd2ca8ec3377d8c7d97e38fb4669a2d2042b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498850"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>在舊版語言服務中驗證中斷點
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[舊版語言服務中的 驗證中斷點](https://docs.microsoft.com/visualstudio/extensibility/internals/validating-breakpoints-in-a-legacy-language-service)。  
  
中斷點會指出以偵錯工具正在執行時，應該在特定時間點停止程式執行。 使用者可以將中斷點放在原始程式檔，任何行，因為編輯器並不知道什麼可替代中斷點的有效位置。 啟動偵錯工具時，所有標記的中斷點 （稱為暫止中斷點） 繫結至執行中的程式中的適當位置。 在相同的時間驗證中斷點，以確保它們可以將有效的程式碼位置來標示。 例如，註解上的中斷點無效，因為在原始程式碼中該位置沒有程式碼。 偵錯工具會停用無效的中斷點。  
  
 語言服務知道所顯示的原始程式碼，因為它可以在偵錯工具啟動前驗證中斷點。 您可以覆寫<xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>方法來傳回指定中斷點的有效位置的範圍。 仍在啟動偵錯工具時，但是無效的中斷點會通知使用者而不需等待偵錯工具載入時，會驗證中斷點位置。  
  
## <a name="implementing-support-for-validating-breakpoints"></a>實作支援的驗證中斷點  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>方法指定之中斷點的位置。 您的實作必須決定位置有效，以及指出這是傳回識別的程式碼的文字範圍相關聯的行位置中斷點。  
  
-   傳回<xref:Microsoft.VisualStudio.VSConstants.S_OK>位置是否有效，或<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>如果不是有效。  
  
-   如果中斷點是有效的文字範圍會反白顯示中斷點以及。  
  
-   如果中斷點是無效的則會在狀態列中出現錯誤訊息。  
  
### <a name="example"></a>範例  
 此範例示範如何實作<xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>方法呼叫的剖析器來取得程式碼的範圍 （如果有的話），在指定的位置。  
  
 這個範例假設您已新增`GetCodeSpan`方法，以<xref:Microsoft.VisualStudio.Package.AuthoringSink>類別，會驗證文字範圍，並傳回`true`如果它是有效的中斷點位置。  
  
```csharp  
using Microsoft VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,  
                                                       int line,  
                                                       int col,  
                                                       TextSpan[] pCodeSpan)  
        {  
            int retval = VSConstants.S_FALSE;  
            if (pCodeSpan != null)  
            {  
                // Initialize span to current line by default.  
                pCodeSpan[0].iStartLine = line;  
                pCodeSpan[0].iStartIndex = col;  
                pCodeSpan[0].iEndLine = line;  
                pCodeSpan[0].iEndIndex = col;  
            }  
  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.CodeSpan,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        TextSpan span = new TextSpan();  
                        if (sink.GetCodeSpan(out span))  
                        {  
                            pCodeSpan[0] = span;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)

