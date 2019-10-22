---
title: 建立自訂 T4 文字範本指示詞處理器
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 836e2c24d9f236c7b87dfff60b934221b7645f1b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654074"
---
# <a name="create-custom-t4-text-template-directive-processors"></a>建立自訂 T4 文字範本指示詞處理器

*文字模板轉換*程式會接受*文字模板*檔案做為輸入，並產生文字檔作為輸出。 *文字模板轉換引擎*會控制進程，而引擎會與文字模板轉換主機以及一或多個文字模板指示詞*處理器*互動，以完成此程式。 如需詳細資訊，請參閱[文字模板轉換](../modeling/the-text-template-transformation-process.md)程式。

若要建立自訂指示詞處理器，您可以建立繼承 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 或 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 的類別。

這兩者的差異在於，<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 會執行從使用者取得參數所需的最小介面，並產生產生範本輸出檔的程式碼。 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 會執行需要/提供設計模式。 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 會處理兩個特殊參數，`requires` 和 `provides`。  例如，自訂指示詞處理器可能會接受使用者提供的檔案名、開啟和讀取檔案，然後將檔案的文字儲存在名為 `fileText` 的變數中。 @No__t_0 類別的子類別可能會將使用者的檔案名當做 `requires` 參數的值，以及用來儲存文字做為 `provides` 參數值的變數名稱。 此處理器會開啟並讀取檔案，然後將檔案的文字儲存在指定的變數中。

在 Visual Studio 的文字模板中呼叫自訂指示詞處理器之前，您必須先註冊它。

如需如何新增登錄機碼的詳細資訊，請參閱[部署自訂](../modeling/deploying-a-custom-directive-processor.md)指示詞處理器。

## <a name="custom-directives"></a>自訂指示詞

自訂指示詞如下所示：

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

當您想要從文字模板存取外部資料或資源時，可以使用自訂指示詞處理器。

不同的文字模板可以共用單一指示詞處理器所提供的功能，因此，指示詞處理器會提供方法來讓程式碼重複使用。 內建的 `include` 指示詞很類似，因為您可以用它來分解程式碼，並在不同的文字模板之間共用。 差別在於，`include` 指示詞所提供的任何功能都是固定的，而且不接受參數。 如果您想要將一般功能提供給文字模板，並允許範本傳遞參數，您必須建立自訂指示詞處理器。

自訂指示詞處理器的一些範例如下：

- 指示詞處理器，可從接受使用者名稱和密碼做為參數的資料庫傳回資料。

- 指示詞處理器，用來開啟和讀取接受檔案名稱做為參數的檔案。

### <a name="principal-parts-of-a-custom-directive-processor"></a>自訂指示詞處理器的主體部分

若要開發指示詞處理器，您必須建立繼承自 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 或 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 的類別。

您必須執行的最重要 `DirectiveProcessor` 方法如下所示。

- `bool IsDirectiveSupported(string directiveName)`-如果您的指示詞處理器可以處理指名的指示詞，則傳回 `true`。

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)`-範本引擎會針對範本中每個出現的指示詞，呼叫這個方法。 您的處理器應該儲存結果。

在所有對 ProcessDirective （）的呼叫之後，範本化引擎都會呼叫下列方法：

- `string[] GetReferencesForProcessingRun()`-傳回範本程式碼所需的元件名稱。

- `string[] GetImportsForProcessingRun()`-傳回可在範本程式碼中使用的命名空間。

- `string GetClassCodeForProcessingRun()`-傳回範本程式碼可以使用的方法、屬性和其他宣告的程式碼。 若要這麼做，最簡單的方法就是建立包含C#或 Visual Basic 程式碼的字串。 若要讓您的指示詞處理器能夠從使用任何 CLR 語言的範本呼叫，您可以將語句視為 CodeDom 樹狀結構，然後傳回以範本所使用的語言序列化樹狀結構的結果。

- 如需詳細資訊，請參閱[逐步解說：建立自訂](../modeling/walkthrough-creating-a-custom-directive-processor.md)指示詞處理器。

## <a name="see-also"></a>請參閱

- [部署自訂](../modeling/deploying-a-custom-directive-processor.md)指示詞處理器說明如何註冊自訂指示詞處理器。
- [逐步解說：建立自訂](../modeling/walkthrough-creating-a-custom-directive-processor.md)指示詞處理器描述如何建立自訂指示詞處理器、如何註冊和測試指示詞處理器，以及如何將輸出檔案格式化為 HTML。