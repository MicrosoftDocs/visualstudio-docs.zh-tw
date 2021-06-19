---
title: 建立自訂 T4 文字範本指示詞處理器
description: 瞭解文字模板轉換流程，以及如何建立自訂 T4 文字模板指示詞處理器。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59644275f17eac197074351a777959bb1826a5de
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389497"
---
# <a name="create-custom-t4-text-template-directive-processors"></a>建立自訂 T4 文字範本指示詞處理器

*文字模板轉換* 程式會將 *文字模板* 檔案作為輸入，並產生文字檔作為輸出。 *文字模板轉換引擎* 會控制進程，而引擎會與文字模板轉換主機和一或多個文字模板指示詞 *處理器* 互動，以完成進程。 如需詳細資訊，請參閱 [文字模板轉換流程](../modeling/the-text-template-transformation-process.md)。

若要建立自訂指示詞處理器，您可以建立繼承 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 或 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 的類別。

這兩者之間的差異在於，會執行 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 從使用者取得參數所需的最小介面，以及產生可產生範本輸出檔的程式碼。 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 會實需要/提供設計模式。 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 處理兩個特殊參數： `requires` 和 `provides` 。  例如，自訂指示詞處理器可能會接受使用者的檔案名、開啟和讀取檔案，然後將檔案的文字儲存在名為的變數中 `fileText` 。 類別的子類別 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 可能會將使用者的檔案名作為參數的值 `requires` ，並將用來儲存文字的變數名稱作為參數的值 `provides` 。 這個處理器會開啟並讀取檔案，然後將檔案的文字儲存在指定的變數中。

從 Visual Studio 中的文字模板呼叫自訂指示詞處理器之前，您必須先註冊它。

如需如何新增登錄機碼的詳細資訊，請參閱 [部署自訂](../modeling/deploying-a-custom-directive-processor.md)指示詞處理器。

## <a name="custom-directives"></a>自訂指示詞

自訂指示詞看起來像這樣：

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

當您想要從文字模板存取外部資料或資源時，可以使用自訂指示詞處理器。

不同的文字模板可以共用單一指示詞處理器所提供的功能，因此指示詞處理器提供了一種方法來將程式碼納入考慮，以供重複使用。 內建的指示詞 `include` 很類似，因為您可以使用它來分解程式碼，並在不同的文字模板之間共用程式碼。 差別在於，指示詞提供的任何功能 `include` 都是固定的，而且不接受參數。 如果您想要提供文字模板的一般功能，並允許範本傳遞參數，您必須建立自訂指示詞處理器。

自訂指示詞處理器的一些範例可能是：

- 指示詞處理器，從接受使用者名稱和密碼做為參數的資料庫傳回資料。

- 指示詞處理器，用來開啟和讀取接受檔案名作為參數的檔案。

### <a name="principal-parts-of-a-custom-directive-processor"></a>自訂指示詞處理器的主要部分

若要開發指示詞處理器，您必須建立繼承自或的類別 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 。

您必須執行的最重要方法如下所示 `DirectiveProcessor` 。

- `bool IsDirectiveSupported(string directiveName)` -如果您的指示詞 `true` 處理器可以處理指名的指示詞，則傳回。

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` -範本引擎會針對範本中的每個指示詞呼叫這個方法。 您的處理器應儲存結果。

所有對 ProcessDirective 的呼叫 () 範本化引擎會呼叫這些方法：

- `string[] GetReferencesForProcessingRun()` -傳回範本程式碼所需的元件名稱。

- `string[] GetImportsForProcessingRun()` -傳回可在範本程式碼中使用的命名空間。

- `string GetClassCodeForProcessingRun()` -傳回範本程式碼可以使用之方法、屬性和其他宣告的程式碼。 若要這麼做，最簡單的方式是建立包含 c # 或 Visual Basic 程式碼的字串。 若要讓您的指示詞處理器可以從使用任何 CLR 語言的範本呼叫，您可以將語句視為 CodeDom 樹狀結構，然後傳回以範本所使用的語言序列化樹狀結構的結果。

- 如需詳細資訊，請參閱 [逐步解說：建立自訂](../modeling/walkthrough-creating-a-custom-directive-processor.md)指示詞處理器。

## <a name="see-also"></a>另請參閱

- [部署自訂](../modeling/deploying-a-custom-directive-processor.md) 指示詞處理器說明如何註冊自訂指示詞處理器。
- [逐步解說：建立自訂](../modeling/walkthrough-creating-a-custom-directive-processor.md) 指示詞處理器說明如何建立自訂指示詞處理器、如何註冊和測試指示詞處理器，以及如何將輸出檔格式化為 HTML。
