---
title: 撰寫 T4 文字模板的指導方針 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 04dd3fc4-10e8-488a-bdea-4d615f50f063
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d1e15a8c00a0614d020defd2df7b06665289a8b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666056"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>撰寫 T4 文字範本的方針
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中產生程式碼或其他應用程式資源，這些一般指導方針可能會很有説明。 它們不是固定規則。

## <a name="guidelines-for-design-time-t4-templates"></a>設計階段 T4 範本的指導方針
 設計階段 T4 範本是在設計階段于您的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案中產生程式碼的範本。 如需詳細資訊，請參閱[使用 T4 文字模板產生設計階段程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。

 產生應用程式的變數層面。
程式碼產生最適用于可能會在專案期間變更的應用程式層面，或在應用程式的不同版本之間變更。 將這些變數層面與更多不變的層面分開，讓您可以更輕鬆地判斷必須產生的內容。 例如，如果您的應用程式提供網站，請從定義流覽路徑的邏輯中，將提供的標準頁面，分開至另一個頁面。

 將一個或多個來源模型中的變數層面編碼。
「模型」（model）是一個檔案或資料庫，每個範本都會讀取該檔案，以取得所要產生之程式碼的變數部分的特定值。 模型可以是資料庫、您自己設計的 XML 檔案、圖表或特定領域的語言。 一般來說，一個模型是用來在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案中產生許多檔案。 每個檔案都是從個別的範本產生。

 您可以在專案中使用一個以上的模型。 例如，您可能會定義在網頁之間導覽的模型，以及針對頁面版面配置的個別模型。

 將模型專注于使用者的需求和詞彙，而不是在您的實上。
例如，在網站應用程式中，您會預期模型參考網頁和超連結。

 在理想的情況下，請選擇一種形式的簡報，以符合模型所代表的資訊類型。 例如，透過網站的導覽路徑模型可以是方塊和箭號的圖表。

 測試產生的程式碼。
使用手動或自動化測試，確認產生的程式碼會如使用者所需運作。 避免從產生該程式碼的相同模型產生測試。

 在某些情況下，可以直接在模型上執行一般測試。 例如，您可以撰寫測試，以確保網站中的每個頁面都可以透過導覽從任何其他網頁來到達。

 允許自訂程式碼：產生部分類別。
除了產生的程式碼之外，允許您手動撰寫的程式碼。 程式碼產生配置無法考慮可能會發生的所有可能的變化，是不尋常的。 因此，您應該預期會新增或覆寫某些產生的程式碼。 如果產生的資料是在 .NET 語言中，例如 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 或 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]，則兩種策略特別有用：

- 產生的類別應該是部分的。 這可讓您將內容新增至產生的程式碼。

- 類別應該成對產生，一個繼承自另一個。 基類應該包含所有產生的方法和屬性，而衍生的類別應該只包含這些函數。 這可讓您的右手寫程式碼覆寫任何產生的方法。

  在其他產生的語言（例如 XML）中，請使用 `<#@include#>` 指示詞，來製作手寫和產生內容的簡單組合。 在較複雜的情況下，您可能必須撰寫後置處理步驟，將產生的檔案與任何手寫檔合併。

  將常見的資料移入 include 檔案或執行時間範本，以避免在多個範本中重複相似的文字和程式碼區塊，請使用 `<#@ include #>` 指示詞。 如需詳細資訊，請參閱[T4 Include](../modeling/t4-include-directive.md)指示詞。

  您也可以在不同的專案中建立執行時間文字模板，然後從設計階段範本呼叫它們。 若要這麼做，請使用 `<#@ assembly #>` 指示詞來存取個別的專案。

  請考慮將大型程式碼區塊移至不同的元件。
  如果您有大型的程式碼區塊和類別功能區塊，將部分程式碼移至您在個別專案中編譯的方法可能會很有用。 您可以使用 `<#@ assembly #>` 指示詞來存取範本中的程式碼。 如需詳細資訊，請參閱[T4 Assembly](../modeling/t4-assembly-directive.md)指示詞。

  您可以將方法放在範本可以繼承的抽象類別中。 抽象類別必須繼承自 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>。 如需詳細資訊，請參閱[T4 Template](../modeling/t4-template-directive.md)指示詞。

  產生程式碼，而不是設定檔撰寫變數應用程式的一種方法，就是撰寫可接受設定檔的一般程式碼。 以這種方式撰寫的應用程式非常有彈性，而且可以在商務需求變更時重新設定，而不需要重建應用程式。 不過，這種方法的缺點是，應用程式的執行效能會比更特定的應用程式還少。 此外，它的程式碼會更難以閱讀和維護，部分原因是它一定會處理最泛型的類型。

  相較之下，在編譯之前產生變數部分的應用程式可以是強型別。 這可讓您更輕鬆且更可靠地撰寫手寫程式碼，並將其與軟體產生的部分整合。

  若要取得程式碼產生的完整優點，請嘗試產生程式碼，而不是設定檔。

  使用產生的程式碼資料夾將範本和產生的檔案放在名為 [**產生**的程式碼] 的專案資料夾中，以清楚指出這些不是應該直接編輯的檔案。 如果您建立自訂程式碼來覆寫或加入至產生的類別，請將這些類別放在名為**Custom code**的資料夾中。 一般專案的結構如下所示：

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

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>執行時間（前置處理過的） T4 範本的指導方針
 將一般材質移至繼承的範本：您可以使用繼承，在 T4 文字模板之間共用方法和文字區塊。 如需詳細資訊，請參閱[T4 Template](../modeling/t4-template-directive.md)指示詞。

 您也可以使用包含執行時間範本的 include 檔案。

 將大型的程式碼主體移至部分類別。
每個執行時間範本都會產生與範本同名的部分類別定義。 您可以撰寫程式碼檔案，其中包含相同類別的另一個部分定義。 您可以透過這種方式，將方法、欄位和函式新增至類別。 這些成員可以從範本中的程式碼區塊呼叫。

 這麼做的好處是，程式碼比較容易撰寫，因為有 IntelliSense 可供使用。 此外，您還可以在簡報和基礎邏輯之間取得更好的分隔。

 例如，在**MyReportText.tt**中：

 `The total is: <#= ComputeTotal() #>`

 在**MyReportText-Methods.cs**中：

 `private string ComputeTotal() { ... }`

 允許自訂程式碼：提供擴充點請考慮在 \< # + 類別功能區塊 # > 中產生虛擬方法。 這可讓您在許多內容中使用單一範本，而不需要修改。 除了修改範本，您還可以建立衍生類別，以提供最小的額外邏輯。 衍生的類別可以是一般程式碼，或者它可以是執行時間範本。

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
 從文字產生中分隔資料收集會嘗試避免混合計算和文字區塊。 在每個文字模板中，使用第一個 \< # 程式碼區塊 # > 來設定變數，並執行複雜的計算。 從第一個文字區塊向下到範本的結尾，或第一個 \< # + 類別功能區塊 # >，避免長運算式，並避免迴圈和條件，除非它們包含文字區塊。 這種作法可讓範本更容易閱讀和維護。

 不使用包含檔案的 `.tt` 會使用不同的副檔名，例如包含檔案的 `.ttinclude`。 請只針對您想要當做執行時間或設計階段文字模板處理的檔案使用 `.tt`。 在某些情況下，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會辨識 `.tt` 的檔案，並自動設定其屬性進行處理。

 以固定原型的形式啟動每個範本。
撰寫您想要產生的程式碼或文字範例，並確定它是正確的。 然後將其副檔名變更為 tt，並以累加方式插入程式碼，藉由讀取模型來修改內容。

 請考慮使用具類型的模型。
雖然您可以為模型建立 XML 或資料庫架構，但建立特定領域語言（DSL）可能會很有用。 DSL 的優點是它會產生類別來表示架構中的每個節點，以及代表屬性的屬性。 這表示您可以根據商務模型來進行程式設計。 例如:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

 請考慮為您的模型使用圖表。
許多模型最有效率的呈現和管理方式就像是文字資料表，特別是當它們非常大時。

 不過，針對某些類型的商務需求，請務必清楚瞭解一組複雜的關聯性和工作流程，而圖表則是最適合的媒體。 圖表的優點是可以輕鬆地與使用者和其他專案關係人討論。 藉由在商務需求層級產生模型的程式碼，您可以在需求變更時讓程式碼更具彈性。

 UML 類別和活動圖通常可以針對這些用途進行調整。 您也可以將自己的圖表類型設計為特定領域語言（DSL）。 可以從 UML 和 Dsl 產生程式碼。 如需詳細資訊，請參閱[分析和模型化架構](../modeling/analyze-and-model-your-architecture.md)和[分析和模型化架構](../modeling/analyze-and-model-your-architecture.md)。

## <a name="see-also"></a>請參閱
 [使用 t4 文字模板產生設計階段程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)搭配[T4 文字模板產生執行時間文字](../modeling/run-time-text-generation-with-t4-text-templates.md)
