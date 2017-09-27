---
title: "驗證舊版語言服務中的中斷點 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 2a87c22948e710a3b95ee7f79b31626794dc7708
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>驗證舊版語言服務中的中斷點
中斷點會指出偵錯工具中正在執行時，應該在特定時間點停止執行程式。 使用者可以在原始程式檔中的任一行上放置中斷點，因為編輯器並不知道何者構成中斷點的有效位置。 啟動偵錯工具時，所有標記 （稱為暫止中斷點） 的中斷點繫結至執行中的程式中的適當位置。 在同一時間中斷點驗證，以確保它們標示的有效的程式碼位置。 例如，註解上的中斷點無效，因為在原始程式碼中該位置沒有程式碼。 偵錯工具會停用無效的中斷點。  
  
 由於語言服務知道要顯示的原始程式碼，它可以驗證中斷點後，才會啟動偵錯工具。 您可以覆寫<xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>方法以傳回指定有效的位置，中斷點的範圍。 仍在啟動偵錯工具時，但不會等待載入偵錯工具通知使用者的無效的中斷點時，會驗證中斷點的位置。  
  
## <a name="implementing-support-for-validating-breakpoints"></a>實作支援驗證的中斷點  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>方法指定之中斷點的位置。 您的實作必須決定位置有效，以及指出這是傳回的程式碼識別的文字範圍相關聯的行位置中斷點。  
  
-   傳回<xref:Microsoft.VisualStudio.VSConstants.S_OK>位置是否有效，或<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>如果不正確。  
  
-   如果中斷點是有效的文字範圍會反白顯示中斷點以及。  
  
-   如果中斷點是無效的則會在 [狀態] 列中出現錯誤訊息。  
  
### <a name="example"></a>範例  
 這個範例會示範實作<xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>呼叫以取得程式碼的範圍 （如果有的話） 剖析器的指定位置的方法。  
  
 這個範例假設您已經加入`GetCodeSpan`方法<xref:Microsoft.VisualStudio.Package.AuthoringSink>類別，會驗證文字範圍，並傳回`true`如果它是有效的中斷點位置。  
  
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
