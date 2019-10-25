---
title: 在舊版語言服務中驗證中斷點 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e7c46473610c96779d0c54e06e82cf884216b13b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722015"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>在舊版語言服務中驗證中斷點
中斷點表示在偵錯工具中執行程式時，應該在特定時間點停止。 使用者可以將中斷點放在原始程式檔中的任何一行，因為編輯器並不知道構成中斷點的有效位置。 當偵錯工具啟動時，所有標示的中斷點（稱為暫止中斷點）都會系結到執行中程式中的適當位置。 同時，系統會驗證中斷點以確保它們會標示有效的程式碼位置。 例如，批註上的中斷點無效，因為原始程式碼中的該位置沒有任何程式碼。 偵錯工具會停用不正確中斷點。

 由於語言服務知道要顯示的原始程式碼，因此它可以在啟動偵錯工具之前驗證中斷點。 您可以覆寫 <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> 方法，以傳回指定中斷點有效位置的範圍。 當偵錯工具啟動時，中斷點位置仍然會經過驗證，但使用者會收到不正確中斷點通知，而不等候偵錯工具載入。

## <a name="implementing-support-for-validating-breakpoints"></a>執行驗證中斷點的支援

- <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> 方法會提供中斷點的位置。 您的執行必須決定位置是否有效，並藉由傳回文字範圍來指出這一點，這會識別與中斷點的行位置相關聯的程式碼。

- 如果位置有效，則傳回 <xref:Microsoft.VisualStudio.VSConstants.S_OK>，如果無效，則傳回 <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>。

- 如果中斷點有效，則會反白顯示文字範圍和中斷點。

- 如果中斷點無效，狀態列中會出現錯誤訊息。

### <a name="example"></a>範例
 這個範例會示範呼叫剖析器以取得指定位置的程式碼範圍（如果有的話）的 <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> 方法的執行。

 這個範例假設您已在驗證文字範圍的 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 類別中加入 `GetCodeSpan` 方法，並傳回 `true` （如果它是有效的中斷點位置）。

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

## <a name="see-also"></a>請參閱
- [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)