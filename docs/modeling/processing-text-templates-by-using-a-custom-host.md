---
title: 使用自訂主機處理文字範本
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f7ecd6508df780f570d10b3d615094fae15209d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591680"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>使用自訂主機處理文字範本

*文字模板轉換*程式會接受*文字模板*檔案做為輸入，並產生文字檔作為輸出。 您可以從 Visual Studio 延伸模組，或從已安裝 Visual Studio 的電腦上執行的獨立應用程式，呼叫文字轉換引擎。 不過，您必須提供*文字模板化主*控制項。 這個類別會將範本連接至環境、尋找資源 (例如組件和 Include 檔)，以及處理輸出和錯誤訊息。

> [!TIP]
> 如果您要撰寫會在 Visual Studio 內執行的封裝或延伸模組，請考慮使用文字模板化服務，而不是撰寫您自己的主機。 如需詳細資訊，請參閱叫[用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。

> [!NOTE]
> 不建議您在伺服器應用程式中使用文字範本轉換。 除非在單一執行緒中，否則也不建議您使用文字範本轉換。 這是因為文字範本化引擎會重複使用單一 AppDomain 來轉譯、編譯和執行範本。 轉譯過的程式碼並不是安全執行緒。 引擎的設計目的是要以序列方式處理檔案，因為它們是在設計階段的 Visual Studio 專案中。
>
> 針對執行時間應用程式，請考慮使用前置處理過的文字模板：請參閱使用[T4 文字模板產生執行時間文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。

如果應用程式使用一組在編譯階段固定不變的範本，則使用「前置處理過的範本」會比較簡單。 如果您的應用程式會在未安裝 Visual Studio 的電腦上執行，您也可以使用該方法。 如需詳細資訊，請參閱[使用 T4 文字模板產生執行時間文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。

## <a name="execute-a-text-template-in-your-application"></a>在您的應用程式中執行文字模板

若要執行文字範本，可以呼叫 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> 的 ProcessTemplate 方法：

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 您的應用程式必須尋找和提供範本，而且必須處理輸出。

 在`host`參數中, 您必須提供可執行 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) 的類別。 引擎會回呼這個類別。

 主應用程式必須能夠記錄錯誤、解析組件和 Include 檔的參考、提供可在其中執行範本的應用程式定義域，以及為每個指示詞呼叫適當的指示詞處理器。

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> 是在 **\*TextTemplating**中定義的，而[ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))是在 .0 中定義的。 **\*. 0 .dll**中。

## <a name="in-this-section"></a>本章節內容
 [逐步解說：建立自訂文字模板主機](../modeling/walkthrough-creating-a-custom-text-template-host.md)示範如何建立自訂文字模板主控制項，讓文字模板功能可在 Visual Studio 外使用。

## <a name="reference"></a>參考資料
 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>相關章節

- [文字模板轉換](../modeling/the-text-template-transformation-process.md)程式會描述文字轉換的運作方式，以及您可以自訂的部分。
- [建立自訂 T4 文字模板](../modeling/creating-custom-t4-text-template-directive-processors.md)指示詞處理器提供文字模板指示詞處理器的總覽。
