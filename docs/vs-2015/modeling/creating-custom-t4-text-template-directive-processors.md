---
title: 建立自訂 T4 文字範本指示詞處理器 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, custom directive processors
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d97b87289be6f6fb685fe9f1b4e5ee4309bd0431
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485107"
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>建立自訂 T4 文字範本指示詞處理器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[建立自訂 T4 文字範本指示詞處理器](https://docs.microsoft.com/visualstudio/modeling/creating-custom-t4-text-template-directive-processors)。  
  
*文字範本轉換流程*採用*文字範本*做為輸入並產生文字檔做為輸出的檔案。 *文字範本轉換引擎*控制項與文字範本轉換主應用程式和一個或多個文字範本的程序和引擎互動*指示詞處理器*完成程序。 如需詳細資訊，請參閱 <<c0> [ 文字範本轉換流程](../modeling/the-text-template-transformation-process.md)。  
  
 若要建立自訂指示詞處理器，您可以建立繼承 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 或 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 的類別。  
  
 在這兩者之間的差異在於<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>實作最小值是從使用者取得參數，以及產生程式碼產生範本輸出檔所需的介面。 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 實作要求/提供設計模式。 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 會處理兩個特殊的參數，`requires`和`provides`。  比方說，自訂指示詞處理器可能會接受檔案名稱，不讓使用者開啟和讀取檔案，而然後將檔案的文字儲存在變數中名為`fileText`。 子類別<xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>類別可能需要從使用者檔案名稱的值`requires`參數，而用來儲存文字做為值的變數名稱`provides`參數。 此處理器會開啟並讀取檔案並再將檔案的文字儲存在指定的變數。  
  
 您可以呼叫自訂指示詞處理器中的文字範本之前[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，您必須註冊它。  
  
 如需如何新增登錄機碼的詳細資訊，請參閱[部署自訂指示詞處理器](../modeling/deploying-a-custom-directive-processor.md)。  
  
## <a name="custom-directives"></a>自訂指示詞  
 自訂指示詞看起來像這樣：  
  
 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" … #>`  
  
 當您想要從文字範本存取外部資料或資源時，您可以使用自訂指示詞處理器。  
  
 不同的文字範本可以共用單一的指示詞處理器所提供的功能，因此指示詞處理器會提供因素的程式碼方法，以供重複使用。 內建`include`指示詞很類似，因為您可以用它來分離出來的程式碼，並在不同的文字範本之間共用。 差異在於任何功能，`include`指示詞提供固定的不接受參數。 如果您想要提供給文字範本的通用功能，並允許將參數傳遞的範本，您必須建立自訂指示詞處理器。  
  
 可能是自訂指示詞處理器的一些範例：  
  
-   傳回從資料庫可接受的使用者名稱和密碼做為參數的資料指示詞處理器。  
  
-   開啟和讀取檔案的指示詞處理器會接受檔案名稱，做為參數。  
  
### <a name="principal-parts-of-a-custom-directive-processor"></a>主體組件的自訂指示詞處理器  
 若要開發的指示詞處理器，您必須建立繼承的類別<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>或<xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>。  
  
 最重要`DirectiveProcessor`必須實作的方法如下所示。  
  
-   `bool IsDirectiveSupported(string directiveName)` -傳回`true`如果指示詞處理器可以處理具名指示詞。  
  
-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` -範本引擎會呼叫這個方法，每個項目範本中的指示詞。 結果應該儲存您的處理器。  
  
 所有呼叫 ProcessDirective() 之後範本化引擎會呼叫這些方法：  
  
-   `string[] GetReferencesForProcessingRun()` -傳回範本程式碼所需的組件名稱。  
  
-   `string[] GetImportsForProcessingRun()` -傳回可用的命名空間中的範本程式碼。  
  
-   `string GetClassCodeForProcessingRun()` -傳回方法、 屬性和範本程式碼可以使用其他宣告的程式的碼。 若要這樣做最簡單的方式是建置包含 C# 或 Visual Basic 程式碼的字串。 若要讓您指示詞處理器能夠呼叫使用任何 CLR 語言的範本，您可以為 CodeDom 樹狀結構建構陳述式，然後傳回 序列化範本所使用的語言中的樹狀結構的結果。  
  
-   如需詳細資訊，請參閱 <<c0> [ 逐步解說： 建立自訂指示詞處理器](../modeling/walkthrough-creating-a-custom-directive-processor.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [部署自訂指示詞處理器](../modeling/deploying-a-custom-directive-processor.md)  
 說明如何註冊自訂指示詞處理器。  
  
 [逐步解說：建立自訂指示詞處理器](../modeling/walkthrough-creating-a-custom-directive-processor.md)  
 描述如何建立自訂指示詞處理器、 如何進行註冊，並測試指示詞處理器，以及如何格式化為 HTML 輸出檔案。



