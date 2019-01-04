---
title: 使用自訂主機處理文字範本
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 12c443879ebbe142dde69a713d214c3b79b254ea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865436"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>使用自訂主機處理文字範本

*文字範本轉換*流程採用*文字範本*做為輸入並產生文字檔做為輸出的檔案。 從 Visual Studio 擴充功能，或從 Visual Studio 安裝在電腦上執行的獨立應用程式，您可以呼叫文字轉換引擎。 不過，您必須提供*文字範本化主機*。 這個類別會將範本連接至環境、尋找資源 (例如組件和 Include 檔)，以及處理輸出和錯誤訊息。

> [!TIP]
> 如果您正在撰寫的封裝或執行 Visual Studio 中的延伸模組，請考慮使用文字範本化服務，而不需要撰寫自己的主機。 如需詳細資訊，請參閱 <<c0> [ 叫用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。

> [!NOTE]
> 不建議您在伺服器應用程式中使用文字範本轉換。 除非在單一執行緒中，否則也不建議您使用文字範本轉換。 這是因為文字範本化引擎會重複使用單一 AppDomain 來轉譯、編譯和執行範本。 轉譯過的程式碼並不是安全執行緒。 引擎被設計來循序處理檔案，因為它們是在 Visual Studio 專案中，在設計階段。
>
> 對於執行階段應用程式，請考慮使用前置處理過的文字範本： 請參閱[執行階段使用 T4 文字範本產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。

如果應用程式使用一組在編譯階段固定不變的範本，則使用「前置處理過的範本」會比較簡單。 如果您的應用程式會在其未安裝 Visual Studio 的電腦上執行，您也可以使用該方法。 如需詳細資訊，請參閱 <<c0> [ 執行階段使用 T4 文字範本產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。

## <a name="execute-a-text-template-in-your-application"></a>在您的應用程式中執行文字範本

若要執行文字範本，可以呼叫 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> 的 ProcessTemplate 方法：

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 您的應用程式必須尋找和提供範本，而且必須處理輸出。

 在 `host` 參數中，必須提供實作 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> 的類別。 引擎會回呼這個類別。

 主應用程式必須能夠記錄錯誤、解析組件和 Include 檔的參考、提供可在其中執行範本的應用程式定義域，以及為每個指示詞呼叫適當的指示詞處理器。

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> 定義於**Microsoft.VisualStudio.TextTemplating。\*。0.log dll**，並<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>中定義**Microsoft.VisualStudio.TextTemplating.Interfaces。\*。0.log dll**。

## <a name="in-this-section"></a>本章節內容
 [逐步解說：建立自訂的文字範本主機](../modeling/walkthrough-creating-a-custom-text-template-host.md)示範如何建立自訂文字範本主機，讓 Visual Studio 之外，您可以使用文字範本功能。

## <a name="reference"></a>參考資料
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>

## <a name="related-sections"></a>相關章節

- [文字範本轉換流程](../modeling/the-text-template-transformation-process.md)說明文字轉換的運作方式，以及哪些部分您可以自訂。
- [建立自訂 T4 文字範本指示詞處理器](../modeling/creating-custom-t4-text-template-directive-processors.md)概述文字範本指示詞處理器。