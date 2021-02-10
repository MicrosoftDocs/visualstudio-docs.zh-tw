---
title: 撰寫 T4 文字範本的方針
description: 瞭解當您在 Visual Studio 中產生程式碼或其他應用程式資源時，會很有説明的一般方針。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5418013898f24b15cf51926022d974d23f4a7215
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966353"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>撰寫 T4 文字範本的方針

如果您要在 Visual Studio 中產生程式碼或其他應用程式資源，這些一般指導方針可能會很有説明。 它們不是固定規則。

## <a name="guidelines-for-design-time-t4-templates"></a>Design-Time T4 範本的指導方針

設計階段 T4 範本是在設計階段于 Visual Studio 專案中產生程式碼的範本。 如需詳細資訊，請參閱 [使用 T4 文字模板的設計階段程式碼產生](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。

產生應用程式的變數部分。

程式碼產生最適用于應用程式中可能會在專案期間變更的部分，或在不同版本的應用程式之間變更。 將這些變數部分與其他不變的層面分開，讓您可以更輕鬆地判斷必須產生的內容。 例如，如果您的應用程式提供網站，請將處理函式的標準頁面與定義導覽路徑的邏輯從某個頁面分隔。

將一或多個來源模型中的變數層面編碼。

模型是每個範本都會讀取的檔案或資料庫，以取得要產生之程式碼的變數部分的特定值。 模型可以是您自己的設計、圖表或特定領域語言的資料庫、XML 檔。 通常會使用一個模型來產生 Visual Studio 專案中的許多檔案。 每個檔案都是從個別的範本產生。

您可以在專案中使用一個以上的模型。 例如，您可以定義在網頁之間流覽的模型，以及針對頁面版面配置的個別模型。

將模型專注在使用者的需求和詞彙上，而不是在您的執行中。

例如，在網站應用程式中，您預期模型會參考網頁和超連結。

在理想的情況下，選擇適合模型所代表之資訊類型的簡報形式。 例如，透過網站的導覽路徑模型可以是方塊和箭號的圖表。

測試產生的程式碼。

使用手動或自動化測試來確認產生的程式碼是否如使用者需要一樣運作。 避免從產生程式碼的相同模型產生測試。

在某些情況下，一般測試可以直接在模型上執行。 例如，您可以撰寫測試，以確保網站中的每個頁面都可以藉由流覽任何其他頁面來達成。

允許自訂程式碼：產生部分類別。

除了產生的程式碼之外，還允許您以手動方式撰寫的程式碼。 程式碼產生配置對於可能發生的所有可能的變異而言，是不尋常的。 因此，您應該預期會加入或覆寫某些產生的程式碼。 如果產生的資料是以 .NET 語言（例如 c # 或 Visual Basic）撰寫，則兩種策略特別有用：

- 產生的類別應該是部分的。 這可讓您將內容新增至產生的程式碼。

- 應該成對產生類別，一個繼承自另一個。 基類應該包含所有產生的方法和屬性，而且衍生的類別只應包含這些函式。 這可讓您的手寫程式碼覆寫任何產生的方法。

在其他產生的語言（例如 XML）中，請使用指示詞 `<#@include#>` 來撰寫手寫和產生的內容的簡單組合。 在更複雜的情況下，您可能需要撰寫會將產生的檔案與任何手寫檔合併的後續處理步驟。

將一般材質移至 include 檔或執行時間範本。

若要避免在多個範本中重複相同的文字和程式碼區塊，請使用指示詞 `<#@ include #>` 。 如需詳細資訊，請參閱 [T4 Include](../modeling/t4-include-directive.md)指示詞。

您也可以在個別的專案中建立執行時間文字模板，然後從設計階段範本呼叫這些範本。 若要這樣做，請使用指示詞 `<#@ assembly #>` 來存取個別專案。

考慮將大型的程式碼區塊移至另一個元件。

如果您有大型的程式碼區塊和類別功能區塊，將某些程式碼移至您在個別專案中編譯的方法可能會很有用。 您可以使用指示詞 `<#@ assembly #>` 來存取範本中的程式碼。 如需詳細資訊，請參閱 [T4 元件](../modeling/t4-assembly-directive.md)指示詞。

您可以將方法放在範本可以繼承的抽象類別中。 抽象類別必須繼承自 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> 。 如需詳細資訊，請參閱 [T4 範本](../modeling/t4-template-directive.md)指示詞。

產生程式碼，而非設定檔。

撰寫變數應用程式的其中一個方法是撰寫可接受設定檔案的一般程式碼。 以這種方式撰寫的應用程式非常有彈性，而且可以在商務需求變更時重新設定，而不需要重建應用程式。 不過，這種方法的缺點是，應用程式的執行效能會比更明確的應用程式還低。 此外，它的程式碼也會更難讀取及維護，部分原因是它一直都是處理最泛型的型別。

相較之下，在編譯之前產生變數部分的應用程式可以是強型別。 這可讓您更輕鬆且更可靠地撰寫手寫程式碼，並將其與軟體產生的部分整合。

若要取得程式碼產生的完整優點，請嘗試產生程式碼，而非設定檔。

使用產生的程式碼資料夾。

將範本和產生的檔案放在名為 [產生的程式 **代碼**] 的專案資料夾中，以清楚指出這些檔案不應該直接編輯。 如果您建立自訂程式碼來覆寫或新增至產生的類別，請將這些類別放在名為 **自訂程式碼** 的資料夾中。 一般專案的結構如下所示：

```
MyProject
   Custom Code
      Class1.cs
      Class2.cs
   Generated Code
      Class1.tt
          Class1.cs
      Class2.tt
          Class2.cs
   AnotherClass.cs
```

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Run-Time (前置處理) T4 範本的指導方針

將一般材質移至繼承的範本。

您可以使用繼承，在 T4 文字模板之間共用方法和文字區塊。 如需詳細資訊，請參閱 [T4 範本](../modeling/t4-template-directive.md)指示詞。

您也可以使用包含執行時間範本的 include 檔。

將大型的程式碼主體移至部分類別。

每個執行時間範本都會產生與範本同名的部分類別定義。 您可以撰寫程式碼檔案，其中包含相同類別的另一個部分定義。 您可以用這種方式，將方法、欄位和函式加入至類別。 您可以從範本中的程式碼區塊呼叫這些成員。

這樣做的優點是可以更容易撰寫程式碼，因為 IntelliSense 可供使用。 此外，您可以在簡報和基礎邏輯之間取得更好的分隔。

例如，在 **MyReportText.tt** 中：

`The total is: <#= ComputeTotal() #>`

在 **MyReportText-Methods.cs** 中：

`private string ComputeTotal() { ... }`

允許自訂程式碼：提供延伸點。

考慮在中產生虛擬方法 \<#+ class feature blocks #> 。 這可讓您在許多內容中使用單一範本，而不需要修改。 除了修改範本之外，您還可以建立衍生類別，以提供最少的額外邏輯。 衍生的類別可以是一般程式碼，也可以是執行時間範本。

例如，在 MyStandardRunTimeTemplate.tt 中：

```
This page is copyright <#= CompanyName() #>.
<#+ protected virtual string CompanyName() { return ""; } #>
```

在應用程式的程式碼中：

```
class FabrikamTemplate : MyStandardRunTimeTemplate
{
  protected override string CompanyName() { return "Fabrikam"; }
}
...
  string PageToDisplay = new FabrikamTemplate().TextTransform();
```

## <a name="guidelines-for-all-t4-templates"></a>所有 T4 範本的指導方針

從文字產生中分隔資料收集。

請嘗試避免混合計算和文字區塊。 在每個文字模板中，使用第一個 \<# code block #> 來設定變數，並執行複雜的計算。 從第一個文字區塊到範本或第一個的結尾 \<#+ class feature block #> ，避免出現長的運算式，並避免迴圈和條件，除非它們包含文字區塊。 這種做法可讓您更輕鬆地讀取和維護範本。

請勿使用 `.tt` include 檔。

使用不同的副檔名，例如 [包含檔案] `.ttinclude` 。 請 `.tt` 僅針對您想要處理的檔案做為執行時間或設計階段文字模板。 在某些情況下，Visual Studio `.tt` 會辨識檔案並自動設定其屬性以進行處理。

以固定原型的形式啟動每個範本。

撰寫您要產生之程式碼或文字的範例，並確定它是正確的。 然後，將其副檔名變更為 tt，並以累加方式插入模型來修改內容的程式碼。

請考慮使用具類型的模型。

雖然您可以為模型建立 XML 或資料庫架構，但是建立特定領域語言 (DSL) 可能會很有用。 DSL 的優點是它會產生類別以表示架構中的每個節點，以及用來表示屬性的屬性。 這表示您可以根據商務模型進行程式設計。 例如：

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

請考慮使用模型的圖表。

許多模型都是以文字資料表的形式來呈現和管理，尤其是在非常大的情況下。

不過，對於某些種類的商務需求，請務必瞭解複雜的關聯性和工作流程組合，而圖表是最適合的媒體。 圖表的優點是很容易與使用者和其他專案關係人討論。 藉由從模型產生商務需求層級的程式碼，您可以讓程式碼在需求變更時更有彈性。

您也可以將自己的圖表類型設計為 (DSL) 的特定領域語言。 您可以從 UML 和 Dsl 產生程式碼。 如需詳細資訊，請參閱 [分析和模型化架構](../modeling/analyze-and-model-your-architecture.md)。

## <a name="see-also"></a>另請參閱

- [使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [使用 T4 文字範本在執行階段產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)
