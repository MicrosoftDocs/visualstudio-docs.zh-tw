---
title: 如何。。。使用文字模板 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c55c7a277d3f38b36367008ae6393f58c9c9a2c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671620"
---
# <a name="how-to--with-text-templates"></a>如何 ... 使用文字範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

中的文字模板 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 提供了一種實用的方法來產生任何種類的文字。 您可以使用文字模板在執行時間產生文字，做為應用程式的一部分，並在設計階段產生您的部分專案程式碼。 本主題摘要說明最常被詢問的「如何? ...」 問題。

 在本主題中，有多個前面加上專案符號的答案是替代建議。

 如需文字模板的一般簡介，請參閱程式 [代碼產生和 T4 文字模板](../modeling/code-generation-and-t4-text-templates.md)。

## <a name="how-to-"></a>如何 …

### <a name="generate-part-of-my-application-code"></a>產生應用程式程式碼的一部分
 我在檔案或資料庫中有設定或 *模型* 。 我的程式碼有一或多個部分相依于該模型。

- 從文字模板產生一些程式碼檔案。 如需詳細資訊，請參閱 [使用 T4 文字模板的設計階段程式碼產生](../modeling/design-time-code-generation-by-using-t4-text-templates.md) ，以及 [開始撰寫範本的最佳方式？](#starting)。

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>在執行時間產生檔案，將資料傳遞至範本
 在執行時間，我的應用程式會產生包含混合標準文字和資料的文字檔，例如報表。 我想要避免撰寫數百個 `write` 語句。

- 將執行時間文字模板加入至您的專案。 此範本會在您的程式碼中建立類別，您可以將其具現化並用來產生文字。 您可以在函式參數中將資料傳遞給它。 如需詳細資訊，請參閱 [使用 T4 文字模板的執行時間文字產生](../modeling/run-time-text-generation-with-t4-text-templates.md)。

- 如果您想要從僅可在執行時間使用的範本產生，則可以使用標準文字模板。 如果您要撰寫 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 延伸模組，您可以叫用文字模板服務。 如需詳細資訊，請參閱 [在 VS 延伸模組中叫用文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。 在其他內容中，您可以使用文字模板化引擎。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>。

     使用指示詞 \<#@parameter#> 將參數傳遞至這些範本。 如需詳細資訊，請參閱 [T4 參數](../modeling/t4-parameter-directive.md)指示詞。

### <a name="read-another-project-file-from-a-template"></a>從範本讀取其他專案檔
 從與範本相同的專案讀取檔案 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ：

- 將 `hostSpecific="true"` 插入至 `<#@template#>` 指示詞。

     在您的程式碼中，使用取得檔案的 `this.Host.ResolvePath(filename)` 完整路徑。

### <a name="invoke-methods-from-a-template"></a>從範本叫用方法
 如果方法已存在，例如在標準 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 類別中：

- 使用指示詞 \<#@assembly#> 載入元件，並使用 \<#@import#> 來設定命名空間內容。 如需詳細資訊，請參閱 [T4 匯入](../modeling/t4-import-directive.md)指示詞。

   如果您經常使用一組相同的元件和匯入指示詞，請考慮撰寫指示詞處理器。 在每個範本中，您可以叫用指示詞處理器，這可以載入元件和模型檔案，並設定命名空間內容。 如需詳細資訊，請參閱 [建立自訂 T4 文字模板](../modeling/creating-custom-t4-text-template-directive-processors.md)指示詞處理器。

  如果您要自行撰寫方法：

- 如果您撰寫的是執行時間文字模板，請撰寫與執行時間文字模板同名的部分類別定義。 將其他方法新增至此類別。

- 撰寫類別功能控制區塊， `<#+ ... #>` 您可以在其中宣告方法、屬性和私用類別。 當文字模板經過編譯時，會轉換成類別。 標準控制區塊 `<#...#>` 和文字會轉換成單一方法，而類別功能區塊會插入為個別的成員。 如需詳細資訊，請參閱 [文字模板控制區塊](../modeling/text-template-control-blocks.md)。

   定義為類別功能的方法也可以包含內嵌的文字區塊。

   請考慮將類別功能放在您可以 `<#@include#>` 加入一個或多個範本檔案的個別檔案中。

- 在不同的元件中撰寫方法 (類別庫) ，然後從您的範本呼叫這些方法。 使用指示詞 `<#@assembly#>` 載入元件，並 `<#@import#>` 設定命名空間內容。 請注意，若要在您進行調試時重建元件，您可能必須停止並重新啟動 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 如需詳細資訊，請參閱 [T4 文字模板](../modeling/t4-text-template-directives.md)指示詞。

### <a name="generate-many-files-from-one-model-schema"></a>從一個模型架構產生許多檔案
 如果您經常從具有相同 XML 或資料庫架構的模型產生檔案：

- 請考慮撰寫指示詞處理器。 這可讓您以單一自訂指示詞取代每個範本中的多個 assembly 語句和 import 語句。 指示詞處理器也可以載入和剖析模型檔案。 如需詳細資訊，請參閱 [建立自訂 T4 文字模板](../modeling/creating-custom-t4-text-template-directive-processors.md)指示詞處理器。

### <a name="generate-files-from-a-complex-model"></a>從複雜模型產生檔案

- 請考慮建立特定領域語言 (DSL) 來代表模型。 這可讓您更輕鬆地撰寫範本，因為您使用的類型和屬性會反映模型中的元素名稱。 您不需要剖析檔案或流覽 XML 節點。 例如：

     `foreach (Book book in this.Library) { ... }`

     如需詳細資訊，請參閱 [使用特定領域語言消費者入門](../modeling/getting-started-with-domain-specific-languages.md) ，以及 [從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。

- 請考慮從 UML 模型產生程式碼。 程式碼不需要直接反映 UML。 例如，您不需要針對 UML 模型中的每個類別產生類別。 相反地，您可以使用 UML 類別圖來表示網站，並從每個 UML 類別產生網頁。 選擇最接近您需求的圖表類型。 例如，選擇活動圖來代表任何類型的工作流程。 您可以定義造型，以將應用程式適當的資訊新增至每個專案類型。

     從 UML 模型產生可讓您以圖表形式繪製和編輯模型，但不需要設計您自己的圖表類型，就像使用 DSL 一樣。

     如需詳細資訊，請參閱為 [您的應用程式建立模型](../modeling/create-models-for-your-app.md) ，並 [從 UML 模型產生](../modeling/generate-files-from-a-uml-model.md)檔案。

### <a name="get-data-from-vsprvs"></a>取得資料 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]
 若要使用中提供的服務 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，請設定 `hostSpecific` 屬性並載入 `EnvDTE` 元件。 例如：

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

### <a name="execute-text-templates-in-the-build-process"></a>在組建流程中執行文字模板

- 如需詳細資訊，請參閱 [在組建流程中產生程式碼](../modeling/code-generation-in-a-build-process.md)。

## <a name="more-general-questions"></a>更多一般問題

### <a name="what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a> 開始撰寫文字模板的最佳方式是什麼？

1. 撰寫所產生檔案的特定範例。

2. 藉由插入指示詞 `<#@template #>` ，以及載入輸入檔或模型所需的指示詞和程式碼，將它轉換成文字模板。

3. 使用運算式和程式碼區塊，以漸進方式取代檔案的部分。

### <a name="what-is-a-model"></a>什麼是「模型」？

- 範本讀取的輸入。 它可能在檔案或資料庫中。 它可能是 XML 或 Visio 繪圖，或是特定領域語言 (DSL) 或 UML 模型，也可能是純文字。 它可能會散佈在多個檔案中。 通常有一個以上的範本會讀取一個模型。

     「模型」一詞的含意是它會比產生的程式碼或其他檔案更直接呈現您商務的某個方面。 例如，它可能代表您所產生軟體將監督的通訊網路的規劃。

### <a name="what-is-the-benefit-of-using-text-templates"></a>使用文字模板的優點為何？
 一般來說，您會從一個模型產生多個程式碼或其他檔案。 模型比產生的程式碼更直接表示需求。 它會省略執行詳細資料，並以需求（而不是程式碼）撰寫。 當需求變更時（通常是如此），您可以更輕鬆且更可靠地更新模型，而不是程式碼的不同部分。

 因此，從敏捷式開發方法的角度來看，程式碼產生是一項重要的工具。

### <a name="what-best-practices-are-there-for-text-templates"></a>什麼是文字模板的「最佳作法」？

- 如需詳細資訊，請參閱 [撰寫 T4 文字模板的指導方針](../modeling/guidelines-for-writing-t4-text-templates.md)。

### <a name="what-is-t4"></a>什麼是 "T4"？

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]此處所述文字模板功能的另一個名稱。 先前的版本（尚未發行）是「文字模板轉換」的縮寫。
