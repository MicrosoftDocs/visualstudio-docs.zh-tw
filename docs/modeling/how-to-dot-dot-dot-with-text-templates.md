---
title: 如何 ... 使用文字範本
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 20dbc5223ddb053355fa5e8076ae66badee688a4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883066"
---
# <a name="how-to--with-text-templates"></a>如何 ... 使用文字範本
Visual Studio 中的文字範本會提供任何類型的產生文字的一種方式。 您可以使用文字範本產生的文字，在執行階段為您的應用程式的一部分，並在設計階段，來產生一些您的專案程式碼。 本主題摘要說明最常詢問"How do I...？ 」 問題。

 本主題中，會加上項目符號的多個答案是替代的建議。

 如需文字範本的一般簡介，閱讀[程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)。

## <a name="how-to-"></a>如何...

### <a name="generate-part-of-my-application-code"></a>產生程式碼的組的件
 我有一個組態或*模型*檔案或資料庫中。 我的程式碼的一或多個組件相依於該模型。

-   從文字範本會產生一些程式碼檔案。 如需詳細資訊，請參閱 <<c0> [ 使用 T4 文字範本在設計階段的程式碼產生](../modeling/design-time-code-generation-by-using-t4-text-templates.md)並[開始撰寫範本的最佳方式為何？](#starting)。

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>在執行階段，將資料傳遞至範本產生檔案
 在執行階段，我的應用程式會產生文字檔案，例如包含混合的標準文字和資料的報表。 我想要避免撰寫數百個`write`陳述式。

-   您可以將執行階段文字範本加入專案。 此範本會建立一個類別，在您程式碼中，您可以具現化，並使用產生的文字。 您可以傳遞給它的資料，在建構函式參數。 如需詳細資訊，請參閱 <<c0> [ 執行階段使用 T4 文字範本產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。

-   如果您想要從只能在執行階段可用的範本產生，您可以使用標準文字範本。 如果您正在撰寫的 Visual Studio 擴充功能，您可以叫用文字範本化服務。 如需詳細資訊，請參閱 <<c0> [ 叫用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。 在其他內容中，您可以使用文字範本化引擎。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>。

     使用\<#@parameter#> 指示詞，以將參數傳遞至這些範本。 如需詳細資訊，請參閱 < [T4 參數指示詞](../modeling/t4-parameter-directive.md)。

### <a name="read-another-project-file-from-a-template"></a>從範本讀取另一個專案檔
 若要從相同的 Visual Studio 專案範本中讀取檔案：

-   將 `hostSpecific="true"` 插入至 `<#@template#>` 指示詞。

     在您的程式碼中，使用`this.Host.ResolvePath(filename)`來取得檔案的完整路徑。

### <a name="invoke-methods-from-a-template"></a>叫用方法，從範本
 如果方法已存在，比方說，在標準[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]類別：

- 使用  \<#@assembly#> 指示詞，以載入組件，並使用\<#@import#> 來設定命名空間內容。 如需詳細資訊，請參閱 < [T4 匯入指示詞](../modeling/t4-import-directive.md)。

   如果您經常使用相同的組件，並匯入指示詞，請考慮撰寫指示詞處理器。 在每個範本中，您可以叫用指示詞處理器，而這可以載入組件和模型檔案，並設定命名空間內容。 如需詳細資訊，請參閱 <<c0> [ 建立自訂 T4 文字範本指示詞處理器](../modeling/creating-custom-t4-text-template-directive-processors.md)。

  如果您要自行撰寫方法：

- 如果您正在撰寫執行階段文字範本，請撰寫執行階段文字範本的名稱相同的部分類別定義。 這個類別中加入額外的方法。

- 撰寫類別功能控制區塊`<#+ ... #>`在方法、 屬性和私用的類別可以宣告它。 文字範本編譯時，會將它轉換為類別。 標準控制區塊`<#...#>`和文字會轉換至單一方法，和類別功能區塊會插入做為個別的成員。 如需詳細資訊，請參閱 <<c0> [ 文字範本控制區塊](../modeling/text-template-control-blocks.md)。

   定義為類別功能也可以包含內嵌的文字區塊的方法。

   請考慮在不同的檔案，您可以將類別功能`<#@include#>`到一或多個範本檔案。

- 在不同的組件 （類別程式庫） 中撰寫方法，並呼叫它們從您的範本。 使用`<#@assembly#>`載入的組件的指示詞和`<#@import#>`來設定命名空間內容。 請注意，若要在偵錯時，請重建組件，您可能必須停止並重新啟動 Visual Studio。 如需詳細資訊，請參閱 < [T4 文字範本指示詞](../modeling/t4-text-template-directives.md)。

### <a name="generate-many-files-from-one-model-schema"></a>從另一個模型結構描述產生許多檔案
 如果您通常會從具有相同的資料庫或 XML 結構描述的模型產生檔案：

-   請考慮撰寫指示詞處理器。 這可讓您將多個組件陳述式和匯入每個使用單一自訂指示詞的範本中的陳述式。 指示詞處理器也可以載入並剖析的模型檔案。 如需詳細資訊，請參閱 <<c0> [ 建立自訂 T4 文字範本指示詞處理器](../modeling/creating-custom-t4-text-template-directive-processors.md)。

### <a name="generate-files-from-a-complex-model"></a>透過複雜的模型產生檔案

-   請考慮建立特定領域語言 (DSL) 來代表此模型。 這讓您更輕鬆地撰寫範本，因為您是使用型別和屬性會反映在模型中項目的名稱。 您沒有要剖析的檔案，或瀏覽 XML 節點。 例如: 

     `foreach (Book book in this.Library) { ... }`

     如需詳細資訊，請參閱 < [Getting Started with 定義域專屬語言](../modeling/getting-started-with-domain-specific-languages.md)並[特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。

### <a name="get-data-from-visual-studio"></a>從 Visual Studio 中取得資料
 若要將提供在 Visual Studio 中設定的服務`hostSpecific`屬性，並載入`EnvDTE`組件。 例如: 

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

### <a name="execute-text-templates-in-the-build-process"></a>在建置程序中執行文字範本

-   如需詳細資訊，請參閱 <<c0> [ 建置流程中的程式碼產生](../modeling/code-generation-in-a-build-process.md)。

## <a name="more-general-questions"></a>更多一般問題

### <a name="starting"></a> 若要開始撰寫文字範本的最佳方式為何？

1.  寫入產生的檔案的特定範例。

2.  將它轉換成文字範本中，插入`<#@template #>`指示詞，指示詞和程式碼所需載入模型的輸入的檔案。

3.  以漸進方式取代檔案的部分運算式和程式碼區塊。

### <a name="what-is-a-model"></a>什麼是 「 模型 」？

-   您的範本所讀取的輸入。 可能是在檔案或資料庫中。 這可能是 XML，或 Visio 繪圖，或特定領域語言 (DSL) 或 UML 模型中，或可能是純文字。 它可以分散到數個檔案。 通常是多個範本讀取一個模型。

     「 模型 」 一詞的含意是業務的，它代表某方面更直接比產生的程式碼或其他檔案。 比方說，它可能會代表您產生的軟體會負責通訊網路的計劃。

### <a name="what-is-the-benefit-of-using-text-templates"></a>使用文字範本的好處是什麼？
 一般而言，您可以從一種模型產生多個程式碼或其他檔案。 模型產生的程式碼比直接呈現需求。 它省略實作詳細資料，並寫入方面的需求，而不是程式碼。 在需求變更-一樣通常-時您就可以更輕鬆且更可靠的程式碼的不同部分比更新模型。

 程式碼產生，因此是從 agile 開發方法的觀點來看的寶貴工具。

### <a name="what-best-practices-are-there-for-text-templates"></a>哪些 「 最佳作法 」 有文字範本？

-   如需詳細資訊，請參閱 <<c0> [ 撰寫 T4 文字範本的指導方針](../modeling/guidelines-for-writing-t4-text-templates.md)。

### <a name="what-is-t4"></a>什麼是 「 T4 」？

-   此處所述的 Visual Studio 文字範本功能的另一個名稱。 舊的版本中，未發行，是 「 文字範本轉換 」 的縮寫。
