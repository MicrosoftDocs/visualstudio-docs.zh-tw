---
title: 撰寫 T4 文字範本的方針
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce316f87e47a7846fc30f480c8e2bf197f38051d
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954242"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>撰寫 T4 文字範本的方針

下列一般指導方針可能會有幫助，如果您要在 Visual Studio 中產生程式碼或其他應用程式資源。 它們不被固定的規則。

## <a name="guidelines-for-design-time-t4-templates"></a>設計階段 T4 範本的指導方針

設計階段 T4 範本是在設計階段產生程式碼在 Visual Studio 專案中的範本。 如需詳細資訊，請參閱 <<c0> [ 使用 T4 文字範本在設計階段的程式碼產生](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。

產生應用程式的變動的層面。

產生程式碼是最適合用於專案期間，可能會變更，或將應用程式的不同版本之間變更的應用程式的這些層面。 好讓您可以更輕鬆地判斷何者得到產生，則您可以分開的更多的非變異層面這些變動層面。 例如，如果您的應用程式提供的一個網站，個別服務定義一個頁面的瀏覽路徑到另一個邏輯從函式的標準分頁。

將編碼的一或多個來源模型中的變動層面。

模型是檔案或以取得要產生的程式碼的變動組件的特定值的每個範本讀取的資料庫。 模型可以是資料庫、 您自己的設計、 圖表或定義域專屬語言的 XML 檔案。 通常，一個模型用來在 Visual Studio 專案中產生許多檔案。 每個檔案是從另一個範本產生。

您可以使用多個模型專案中。 例如，您可以定義網頁和頁面的版面配置的不同模型之間的巡覽的模型。

聚焦模型，在使用者的需求和詞彙，而不是在您的實作。

例如，網站應用程式中，您應該會指向網頁和超連結的模型。

在理想情況下，選擇一種適合此模型代表的資訊種類的簡報。 例如，透過網站的導覽路徑的模型可能是方塊與箭號的圖表。

測試產生的程式碼。

若要確認產生的程式碼的運作，因為使用者需要使用手動或自動化測試。 避免從相同的模型，從中產生的程式碼產生的測試。

在某些情況下，一般測試可以對模型直接。 例如，您可以撰寫測試，以確保從任何其他的瀏覽可在網站中的每一頁。

允許自訂程式碼： 產生部分類別。

可讓您撰寫程式碼以手動方式此外要產生的程式碼。 很少能夠處理可能發生的所有可能變化的程式碼產生配置。 因此，您應該會加入或覆寫某些產生的程式碼。 其中產生的資料是以.NET 語言如C#或 Visual Basic 中，兩種策略時特別有用：

- 產生的類別應該是部分。 這可讓您將內容加入至產生的程式碼。

- 類別應該產生成對，繼承自另一個。 基底類別應該包含所有產生的方法和屬性，而且衍生的類別應該包含建構函式。 這可讓您手動撰寫的程式碼，來覆寫任何產生的方法。

在 XML 等其他產生語言，使用`<#@include#>`指示詞來提供簡單的手動撰寫和產生內容的組合。 在更複雜的情況下，您可能必須撰寫結合所產生的檔案與任何手寫檔案後置處理步驟。

將常見的資料移入 include 檔或執行階段範本。

若要避免重複類似的文字和多個範本中的程式碼的區塊，使用`<#@ include #>`指示詞。 如需詳細資訊，請參閱 < [T4 包含指示詞](../modeling/t4-include-directive.md)。

您可以也建置在個別的專案中，執行階段文字範本，，然後將它們呼叫從設計階段範本。 若要這樣做，請使用`<#@ assembly #>`指示詞，以存取個別的專案。

請考慮移到不同的組件的大型區塊的程式碼。

如果您有大型的程式碼區塊和類別功能區塊，它可能有助於將有些程式碼移至您在個別的專案編譯的方法。 您可以使用`<#@ assembly #>`指示詞，以存取範本中的程式碼。 如需詳細資訊，請參閱 < [T4 組件指示詞](../modeling/t4-assembly-directive.md)。

您可以將方法放在樣板可以繼承的抽象類別。 抽象類別必須繼承自<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>。 如需詳細資訊，請參閱 < [T4 範本指示詞](../modeling/t4-template-directive.md)。

產生程式碼，不是組態檔。

寫入變數的應用程式的一個方法是撰寫可接受組態檔的一般程式碼。 以這種方式撰寫的應用程式非常有彈性，並重新設定當業務需求變更，而不需重建應用程式。 不過，這種方法的缺點是，應用程式會執行於更特定的應用程式效能不佳。 此外，其程式碼將會更難讀取與維護，部分原因是它必須永遠會處理大部分的泛型類型。

相反地，其變動的組件會產生之前編譯的應用程式可以是強型別。 這可讓它更容易且更可靠撰寫手動撰寫的程式碼，並將它整合以產生組件的軟體。

若要取得所產生程式碼的完整優點，請嘗試產生程式碼，而不是組態檔案。

使用產生的程式碼的資料夾。

將範本與產生的檔案放在名為專案資料夾**產生的程式碼**，讓它清除這些不應直接編輯的檔案。 如果您建立自訂的程式碼來覆寫或新增至產生的類別，可將這些類別放在名為的資料夾**自訂程式碼**。 一般專案結構看起來像這樣：

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

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>執行階段 （前置處理過的） 的 T4 範本的指導方針

將常見的資料移至 繼承的範本。

您可以使用繼承來共用方法和 T4 文字範本之間的文字區塊。 如需詳細資訊，請參閱 < [T4 範本指示詞](../modeling/t4-template-directive.md)。

您也可以使用包含具有執行階段範本檔案。

將大型程式碼主體移至部分類別中。

每個執行階段範本會產生具有相同名稱做為範本的部分類別定義。 您可以撰寫程式碼檔案，其中包含相同類別的另一個部分定義。 您可以將方法、 欄位和建構函式，加入這種方式中的類別。 從範本中的程式碼區塊，就可以呼叫這些成員。

這麼做的優點是程式碼很容易撰寫的因為 IntelliSense 可供使用。 此外，您可以達到更好的展示層和基礎邏輯之間的分隔。

例如，在**MyReportText.tt**:

`The total is: <#= ComputeTotal() #>`

在  **MyReportText Methods.cs**:

`private string ComputeTotal() { ... }`

允許自訂程式碼： 提供擴充點。

請考慮產生中的虛擬方法\<#+ 類別功能區塊 #>。 這可讓單一的範本，以用於許多內容，而不需修改。 除了修改範本，您可以建構衍生的類別，其提供的最小的額外邏輯。 在衍生的類別可以是任一個規則的程式碼，或執行階段範本。

例如，在 MyStandardRunTimeTemplate.tt:

```
This page is copyright <#= CompanyName() #>.
<#+ protected virtual string CompanyName() { return ""; } #>
```

在應用程式的程式碼：

```
class FabrikamTemplate : MyStandardRunTimeTemplate
{
  protected override string CompanyName() { return "Fabrikam"; }
}
...
  string PageToDisplay = new FabrikamTemplate().TextTransform();
```

## <a name="guidelines-for-all-t4-templates"></a>所有 T4 範本的指導方針

從文字產生不同的資料收集。

請盡量避免混用計算和文字區塊。 在每個文字範本中，使用第一個\<# 程式碼區塊 #> 設定變數，並執行複雜的計算。 從第一個文字區塊的範本或第一個值為\<#+ 類別功能區塊 #>、 避免長的運算式，以及避免迴圈及條件，除非它們包含文字區塊。 這種做法可讓範本更容易閱讀及維護。

請勿使用`.tt`include 檔。

使用不同的檔案名稱副檔名，例如`.ttinclude`include 檔。 使用`.tt`只針對您想要的檔案處理，執行階段或設計階段文字範本。 在某些情況下，Visual Studio 可以辨識`.tt`檔案，並會自動設定其內容以供處理。

以固定的原型中啟動每個範本。

撰寫您要產生，請確定它是正確的程式碼或文字的範例。 然後在變更其副檔名為.tt 和以累加方式插入修改內容，請閱讀此模型的程式碼。

請考慮使用具類型的模型。

雖然您可以針對您的模型建立的資料庫或 XML 結構描述，它可能有助於建立特定領域語言 (DSL)。 DSL 的優點是它會產生代表每個節點在結構描述和屬性，以代表之屬性的類別。 這表示您可以根據商務模型進行程式設計。 例如: 

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

請考慮使用您的模型圖表。

許多模型是最有效地呈現，而且特別是如果它們是非常大，簡稱為文字的資料表，受管理。

不過，某些類型的商務需求，務必要釐清複雜的關聯性和工作流程，集以及圖表是最適合的媒體。 圖表的優點是，它可以輕易地與使用者和其他專案關係人討論。 藉由從層級的商務需求模型產生程式碼，您將讓您的程式碼為更有彈性，在需求變更時。

您也可以做為特定領域語言 (DSL) 來設計您自己的圖表類型。 從 UML 和 Dsl，可以產生程式碼。 如需詳細資訊，請參閱 <<c0> [ 分析架構並製作架構](../modeling/analyze-and-model-your-architecture.md)。

## <a name="see-also"></a>另請參閱

- [使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [使用 T4 文字範本在執行階段產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)