---
title: 在舊版語言服務中驗證中斷點 |Microsoft Docs
description: 瞭解如何在舊版語言服務中覆寫 ValidateBreakpointLocation 方法，以在偵錯工具啟動前驗證中斷點。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d48db7397e2f9a5921315036bea15551fb7baa9
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488020"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>在舊版語言服務中驗證中斷點
中斷點表示程式執行在偵錯工具中執行時，應該會在特定的時間點停止。 使用者可以在原始程式檔中的任何一行上放置中斷點，因為編輯器不知道組成中斷點的有效位置。 當偵錯工具啟動時，所有標示的中斷點 (稱為暫止中斷點) 都會系結至執行程式中的適當位置。 同時驗證中斷點，以確保它們會標示有效的程式碼位置。 例如，批註上的中斷點無效，因為原始程式碼中的位置沒有任何程式碼。 偵錯工具會停用不正確中斷點。

 由於語言服務知道所顯示的原始程式碼，因此可以在啟動偵錯工具之前驗證中斷點。 您可以覆寫 <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> 方法，以傳回指定中斷點有效位置的範圍。 當偵錯工具啟動時，中斷點位置仍會進行驗證，但使用者會收到無效中斷點的通知，而不會等候偵錯工具載入。

## <a name="implementing-support-for-validating-breakpoints"></a>執行驗證中斷點的支援

- <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>方法會提供中斷點的位置。 您的執行必須決定位置是否有效，並藉由傳回文字範圍來指出，此範圍會識別與中斷點的行位置相關聯的程式碼。

- <xref:Microsoft.VisualStudio.VSConstants.S_OK>如果位置有效，則傳回; 如果無效，則傳回 <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> 。

- 如果中斷點有效，則會反白顯示文字範圍和中斷點。

- 如果中斷點無效，狀態列中會出現一則錯誤訊息。

### <a name="example"></a>範例
 這個範例會示範方法的執行 <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> ，這個方法會呼叫剖析器來取得程式碼範圍 (如果指定位置有任何) 的話。

 此範例假設您已將方法新增 `GetCodeSpan` 至 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 類別，以驗證文字範圍，並在 `true` 它是有效的中斷點位置時傳回。

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
- [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)
