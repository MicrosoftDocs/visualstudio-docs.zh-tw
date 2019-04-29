---
title: 舊版語言服務中的 [自動變數] 視窗的支援 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7fdff9237ef30884d5bfaad424edfffec62a8f58
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62908411"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>舊版語言服務中對自動變數視窗的支援
**自動變數**視窗會顯示運算式，例如變數和正在偵錯程式暫停 （可能是因為中斷點或例外狀況） 時，會在範圍內的參數。 運算式可以包含變數，本機或全域和已變更的區域範圍中的參數。 **自動變數**視窗也可以包含類別、 結構或其他類型的具現化。 運算式評估工具可以評估的任何項目可能顯示在**自動變數**視窗。

 Managed 的 package framework (MPF) 不提供直接的支援，如**自動變數**視窗。 不過，如果您覆寫<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>方法中，您可以傳回的運算式，以顯示在清單 **[自動變數]** 視窗。

## <a name="implementing-support-for-the-autos-window"></a>實作自動變數 視窗的支援
 您只需要以支援**自動變數**視窗為實作<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>方法中的<xref:Microsoft.VisualStudio.Package.LanguageService>類別。 您的實作必須決定指定的位置，在來源檔案中，運算式應該會出現在**自動變數**視窗。 方法會傳回一份其中每個字串代表單一運算式的字串。 傳回值<xref:Microsoft.VisualStudio.VSConstants.S_OK>指出清單是否包含運算式，而<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>指出已沒有任何運算式來顯示。

 實際傳回的運算式是變數或參數出現在程式碼中的該位置的名稱。 這些名稱會傳遞給運算式評估工具，若要取得的值和類型，然後顯示在**自動變數**視窗。

### <a name="example"></a>範例
 下列範例示範實作<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>方法，取得一份來自運算式<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法使用剖析原因<xref:Microsoft.VisualStudio.Package.ParseReason>。 每個運算式會包裝成`TestVsEnumBSTR`實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>介面。

 請注意，`GetAutoExpressionsCount`並`GetAutoExpression`方法就是自訂的方法上`TestAuthoringSink`物件，並已新增以支援此範例。 它們代表新增至哪一個運算式中的一種方式`TestAuthoringSink`剖析器的物件 (藉由呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>方法) 可以存取外部剖析器。

```csharp
using Microsoft.VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override int GetProximityExpressions(IVsTextBuffer buffer,
                                                    int line,
                                                    int col,
                                                    int cLines,
                                                    out IVsEnumBSTR ppEnum)
        {
            int retval = VSConstants.E_NOTIMPL;
            ppEnum = null;
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
                                                              ParseReason.Autos,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        retval = VSConstants.S_FALSE;
                        int spanCount = sink.GetAutoExpressionsCount();
                        if (spanCount > 0) {
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();
                            for (int i = 0; i < spanCount; i++)
                            {
                                TextSpan span;
                                sink.GetAutoExpression(i, out span);
                                string expression = src.GetText(span.iStartLine,
                                                                span.iStartIndex,
                                                                span.iEndLine,
                                                                span.iEndIndex);
                                bstrList.AddString(expression);
                            }
                            ppEnum = bstrList;
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