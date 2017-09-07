---
title: "建立自訂 T4 文字範本指示詞處理器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, custom directive processors
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 29
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
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
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: a8f56201528b15da04c5861be5c9afdd9a9b379e
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="creating-custom-t4-text-template-directive-processors"></a>建立自訂 T4 文字範本指示詞處理器
*文字範本轉換流程*採用*文字範本*做為輸入和產生的文字檔做為輸出的檔案。 *文字範本轉換引擎*控制項與文字範本轉換主應用程式和一個或多個文字範本互動的處理程序和引擎*指示詞處理器*完成程序。 如需詳細資訊，請參閱[文字範本轉換流程](../modeling/the-text-template-transformation-process.md)。  
  
 若要建立自訂指示詞處理器，您可以建立繼承 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 或 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 的類別。  
  
 在這兩者之間的差異在於<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>實作取得使用者的參數，並產生產生範本輸出檔案的程式碼所需的最低介面。 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>實作要求/提供設計模式。 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>處理特殊的兩個參數，`requires`和`provides`。  例如，自訂指示詞處理器可能會接受來自使用者開啟的檔案名稱讀取的檔案，然後儲存檔案的文字中的變數，名為`fileText`。 子類別<xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>類別可能需要從使用者檔案名稱的值為`requires`參數，以及用來儲存文字做為值的變數名稱`provides`參數。 此處理器會開啟和讀取檔案，然後將檔案的文字儲存在指定的變數。  
  
 在呼叫自訂指示詞處理器中的文字範本之前[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，您必須註冊它。  
  
 如需如何新增登錄機碼的詳細資訊，請參閱[部署自訂指示詞處理器](../modeling/deploying-a-custom-directive-processor.md)。  
  
## <a name="custom-directives"></a>自訂指示詞  
 自訂指示詞看起來像這樣：  
  
 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`  
  
 當您想要從文字範本存取外部資料或資源，您可以使用自訂指示詞處理器。  
  
 不同的文字範本可以共用單一的指示詞處理器所提供的功能，因此指示詞處理器，提供一種因素的程式碼重複使用。 內建`include`指示詞會很類似，因為您可以將程式碼分離出來並共用各不同的文字範本中使用它。 差別在於任何功能，`include`指示詞提供固定的不接受參數。 如果您想要提供文字範本的一般功能，並允許將參數傳遞的範本，您必須建立自訂指示詞處理器。  
  
 可能是自訂指示詞處理器的一些範例：  
  
-   從資料庫可接受使用者名稱和密碼做為參數傳回資料的指示詞處理器。  
  
-   開啟和讀取檔案的指示詞處理器做為參數接受檔案名稱。  
  
### <a name="principal-parts-of-a-custom-directive-processor"></a>主體組件的自訂指示詞處理器  
 若要開發的指示詞處理器，您必須建立繼承的類別<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>或<xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>。  
  
 最重要`DirectiveProcessor`必須實作的方法是，如下所示。  
  
-   `bool IsDirectiveSupported(string directiveName)`-傳回`true`如果具名指示詞可處理指示詞處理器。  
  
-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)`-範本引擎會呼叫這個方法，針對每個範本中的指示詞。 結果應該儲存您的處理器。  
  
 只有將所有呼叫之後，範本化引擎會呼叫這些方法：  
  
-   `string[] GetReferencesForProcessingRun()`-傳回範本程式碼所需的組件的名稱。  
  
-   `string[] GetImportsForProcessingRun()`-傳回可用的命名空間中的範本程式碼。  
  
-   `string GetClassCodeForProcessingRun()`-傳回碼的方法、 屬性和範本程式碼可以使用其他宣告。 若要這樣做最簡單的方式是建立包含 C# 或 Visual Basic 程式碼的字串。 若要讓您指示詞處理器能夠呼叫使用任何 CLR 語言的範本，您為 CodeDom 樹狀結構建構陳述式，然後傳回結果的序列化範本所使用的語言中的樹狀結構。  
  
-   如需詳細資訊，請參閱[逐步解說： 建立自訂指示詞處理器](../modeling/walkthrough-creating-a-custom-directive-processor.md)。  
  
## <a name="in-this-section"></a>本章節內容  
 [部署自訂指示詞處理器](../modeling/deploying-a-custom-directive-processor.md)  
 說明如何自訂指示詞處理器暫存器。  
  
 [逐步解說：建立自訂指示詞處理器](../modeling/walkthrough-creating-a-custom-directive-processor.md)  
 描述如何建立自訂指示詞處理器、 如何註冊和測試指示詞處理器，以及如何格式化為 HTML 的輸出檔。
