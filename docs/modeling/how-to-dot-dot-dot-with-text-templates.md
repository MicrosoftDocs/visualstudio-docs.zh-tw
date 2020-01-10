---
title: 如何 ... 使用文字範本
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7ecabc00f37cb199f203bcd71a1b72bdbfbe1a4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594652"
---
# <a name="how-to--with-text-templates"></a>如何 ... 使用文字範本
Visual Studio 中的文字模板提供了一種實用的方式來產生任何種類的文字。 您可以使用文字模板，在執行時間將文字產生為應用程式的一部分，並在設計階段，產生您的某些專案程式碼。 本主題摘要說明最常詢問的「如何? ...？」 問題.

 在本主題中，前面加上專案符號的多個答案都是替代建議。

 如需文字模板的一般簡介，請參閱程式[代碼產生和 T4 文字模板](../modeling/code-generation-and-t4-text-templates.md)。

## <a name="how-to-"></a>作法

### <a name="generate-part-of-my-application-code"></a>產生部分應用程式代碼
 我在檔案或資料庫中有設定或*模型*。 我的程式碼中有一或多個部分相依于該模型。

- 從文字模板產生一些程式碼檔案。 如需詳細資訊，請參閱[使用 T4 文字模板產生設計階段程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)，以及[開始撰寫範本的最佳方式為何？](#starting)。

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>在執行時間產生檔案，將資料傳遞至範本
 在執行時間，我的應用程式會產生包含混合標準文字和資料的文字檔（例如報表）。 我想要避免撰寫數百個 `write` 語句。

- 將執行時間文字模板加入至您的專案。 此範本會在您的程式碼中建立類別，您可以將它具現化並用來產生文字。 您可以在函式參數中傳遞資料給它。 如需詳細資訊，請參閱[使用 T4 文字模板產生執行時間文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。

- 如果您想要從僅在執行時間提供的範本產生，您可以使用標準文字模板。 如果您要撰寫 Visual Studio 的延伸模組，您可以叫用文字模板化服務。 如需詳細資訊，請參閱叫[用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。 在其他內容中，您可以使用文字模板化引擎。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>。

     使用 \<#@parameter# > 指示詞，將參數傳遞至這些範本。 如需詳細資訊，請參閱[T4 參數](../modeling/t4-parameter-directive.md)指示詞。

### <a name="read-another-project-file-from-a-template"></a>從範本讀取另一個專案檔
 若要從與範本相同的 Visual Studio 專案讀取檔案：

- 將 `hostSpecific="true"` 插入至 `<#@template#>` 指示詞。

     在您的程式碼中，使用 `this.Host.ResolvePath(filename)` 來取得檔案的完整路徑。

### <a name="invoke-methods-from-a-template"></a>從範本叫用方法

如果方法已經存在，例如在 .NET 類別中：

- 使用 \<#@assembly# > 指示詞來載入元件，並使用 \<#@import# > 來設定命名空間內容。 如需詳細資訊，請參閱[T4 Import](../modeling/t4-import-directive.md)指示詞。

   如果您經常使用同一組元件和匯入指示詞，請考慮撰寫指示詞處理器。 在每個範本中，您可以叫用指示詞處理器，這可以載入元件和模型檔案，並設定命名空間內容。 如需詳細資訊，請參閱[建立自訂 T4 文字模板](../modeling/creating-custom-t4-text-template-directive-processors.md)指示詞處理器。

如果您要自行撰寫方法：

- 如果您要撰寫執行時間文字模板，請撰寫與您的執行時間文字模板同名的部分類別定義。 將其他方法新增至這個類別。

- 撰寫類別功能控制區塊 `<#+ ... #>`，您可以在其中宣告方法、屬性和私用類別。 編譯文字模板時，會將它轉換成類別。 標準控制區塊 `<#...#>` 和文字會轉換成單一方法，而類別功能區塊則會插入為個別的成員。 如需詳細資訊，請參閱[文字模板控制區塊](../modeling/text-template-control-blocks.md)。

   定義為類別功能的方法也可以包含內嵌的文字區塊。

   請考慮將類別功能放在個別的檔案中，讓您可以 `<#@include#>` 到一個或多個範本檔案中。

- 在個別元件（類別庫）中寫入方法，並從您的範本呼叫它們。 使用 `<#@assembly#>` 指示詞載入元件，並 `<#@import#>` 以設定命名空間內容。 請注意，為了在進行偵錯工具時重建元件，您可能必須停止並重新啟動 Visual Studio。 如需詳細資訊，請參閱[T4 文字模板](../modeling/t4-text-template-directives.md)指示詞。

### <a name="generate-many-files-from-one-model-schema"></a>從一個模型架構產生許多檔案
 如果您經常從具有相同 XML 或資料庫架構的模型產生檔案：

- 請考慮撰寫指示詞處理器。 這可讓您使用單一自訂指示詞來取代每個範本中的多個元件語句和匯入語句。 指示詞處理器也可以載入和剖析模型檔案。 如需詳細資訊，請參閱[建立自訂 T4 文字模板](../modeling/creating-custom-t4-text-template-directive-processors.md)指示詞處理器。

### <a name="generate-files-from-a-complex-model"></a>從複雜的模型產生檔案

- 請考慮建立特定領域語言（DSL）來代表模型。 這可讓您更輕鬆地撰寫範本，因為您使用的類型和屬性會反映模型中的元素名稱。 您不需要剖析檔案或流覽 XML 節點。 例如：

     `foreach (Book book in this.Library) { ... }`

     如需詳細資訊，請參閱[使用特定領域語言消費者入門](../modeling/getting-started-with-domain-specific-languages.md)和[從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。

### <a name="get-data-from-visual-studio"></a>從 Visual Studio 取得資料
 若要使用 Visual Studio 中提供的服務，請設定 `hostSpecific` 屬性，並載入 `EnvDTE` 元件。 例如：

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

### <a name="execute-text-templates-in-the-build-process"></a>在組建進程中執行文字模板

- 如需詳細資訊，請參閱[在組建流程中產生程式碼](../modeling/code-generation-in-a-build-process.md)。

## <a name="more-general-questions"></a>更多一般問題

### <a name="starting"></a>開始撰寫文字模板的最佳方式為何？

1. 撰寫所產生檔案的特定範例。

2. 藉由插入 `<#@template #>` 指示詞，以及載入輸入檔或模型所需的指示詞和程式碼，將它轉換成文字模板。

3. 以運算式和程式碼區塊逐漸取代檔案的各個部分。

### <a name="what-is-a-model"></a>什麼是「模型」？

- 您的範本所讀取的輸入。 它可以在檔案或資料庫中。 它可能是 XML、Visio 繪圖或特定領域語言（DSL），或是 UML 模型，或者可以是純文字。 它可以散佈在數個檔案中。 通常一個以上的範本會讀取一個模型。

     「模型」一詞的含意是，它代表您業務的某些層面，而不是所產生的程式碼或其他檔案。 例如，它可能代表您所產生軟體將監督的通訊網路計畫。

### <a name="what-is-the-benefit-of-using-text-templates"></a>使用文字模板的優點為何？
 一般來說，您會從一個模型產生多個程式碼或其他檔案。 模型所呈現的需求比產生的程式碼更直接。 它會省略「執行詳細資料」，並根據需求（而不是程式碼）來撰寫。 當需求變更時-就像平常一樣，您可以更輕鬆且更可靠地更新模型，而不是程式碼的不同部分。

 因此，從敏捷式開發方法的角度來看，程式碼產生是一項重要的工具。

### <a name="what-best-practices-are-there-for-text-templates"></a>文字模板的「最佳作法」是什麼？

- 如需詳細資訊，請參閱[撰寫 T4 文字模板的指導方針](../modeling/guidelines-for-writing-t4-text-templates.md)。

### <a name="what-is-t4"></a>什麼是「T4」？

- 這裡所述 Visual Studio 文字模板功能的另一個名稱。 先前的版本（尚未發行）是「文字模板轉換」的縮寫。
