---
title: 驗證傳統語言服務中的斷點 |微軟文件
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
ms.openlocfilehash: af09e4f8f2156100bea9267c92ffebeb64ce1aa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704087"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>在舊版語言服務中驗證中斷點
斷點指示程式執行應在調試器中運行時在特定點停止。 用戶可以在源檔中的任何行上放置斷點,因為編輯器不知道什麼是斷點的有效位置。 啟動調試器時,所有標記的斷點(稱為掛起斷點)都綁定到正在運行的程式中的相應位置。 同時驗證斷點,以確保它們標記有效的代碼位置。 例如,註釋上的斷點無效,因為原始碼中該位置沒有代碼。 調試器禁用無效的斷點。

 由於語言服務知道正在顯示的原始程式碼,它可以在啟動調試器之前驗證斷點。 可以重寫<xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>方法以返回指定斷點有效位置的跨距。 啟動調試器時,斷點位置仍被驗證,但使用者會收到無效斷點的通知,而無需等待調試器載入。

## <a name="implementing-support-for-validating-breakpoints"></a>測試對驗證中斷點

- 給出<xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>斷點的位置的方法。 您的實現必須確定該位置是否有效,並通過返回標識與斷點位置的行位置關聯的代碼的文本範圍來指示這一點。

- 如果<xref:Microsoft.VisualStudio.VSConstants.S_OK>位置有效,<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>或者 該位置無效,則返回。

- 如果斷點有效,則文本範圍將與斷點一起突出顯示。

- 如果斷點無效,狀態列中將顯示一條錯誤消息。

### <a name="example"></a>範例
 此範例展示調用解析器以獲取指定<xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>位置的代碼範圍(如果有)的方法的實現。

 本示例假定您向`GetCodeSpan`<xref:Microsoft.VisualStudio.Package.AuthoringSink>類添加了一個方法,該類驗證文本範圍,如果文本`true`範圍 是有效的斷點位置,則返回該方法。

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
