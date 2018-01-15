---
title: "撰寫 T4 文字範本的方針 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f137cea483111e332da6a7f06b924973364f2e28
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="guidelines-for-writing-t4-text-templates"></a>撰寫 T4 文字範本的方針
下列一般指導方針可能有幫助您在產生程式碼或其他應用程式資源[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 它們不被固定的規則。  
  
## <a name="guidelines-for-design-time-t4-templates"></a>設計階段 T4 範本的方針  
 設計階段 T4 範本是範本產生程式碼中的，您[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案的設計階段。 如需詳細資訊，請參閱[設計階段透過使用 T4 文字範本的程式碼產生](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。  
  
 產生的應用程式變數的層面。  
 產生程式碼是最適合這些層面可能會變更專案期間，或將應用程式的不同版本之間變更的應用程式。 使您可以更輕鬆地判斷何者得到產生，則您可以分開更而異的層面這些變數的層面。 例如，如果您的應用程式提供的網站，個別服務定義一頁的導覽路徑到另一個邏輯的函式的標準頁面。  
  
 編碼的一或多個來源模型中的變數層面。  
 模型是檔案或以取得要產生之程式碼的變動部分的特定值的每個範本讀取的資料庫。 模型可以是資料庫、 您自己的設計、 圖表或特定領域語言的 XML 檔案。 一般而言，一個模型用來產生許多檔案中的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案。 每個檔案是從另一個範本產生。  
  
 您可以在專案中使用多個模型。 例如，您可以定義瀏覽不同的網頁和頁面之版面配置的不同模型的模型。  
  
 聚焦至模型，使用者的需求和詞彙，而非您的實作。  
 比方說，在網站應用程式中，您應該會指向網頁和超連結的模型。  
  
 在理想情況下，選擇適合的模型呈現的資訊種類的簡報的表單。 例如，透過網站的導覽路徑的模型可能方塊和箭號的圖表。  
  
 測試產生的程式碼。  
 若要確認產生的程式碼的運作，因為使用者需要使用手動或自動化測試。 避免相同的模型，從中產生的程式碼中產生測試。  
  
 在某些情況下，一般測試可以對模型直接。 例如，您可以撰寫的測試，可確保在網站上的每個頁面，可以從任何其他的巡覽到達。  
  
 允許的自訂程式碼： 產生部分類別。  
 可讓您撰寫程式碼以手動方式另外要產生的程式碼。 它並不常見的程式碼產生配置能夠帳戶可能會產生所有可能變化。 因此，您應該預期要加入或覆寫產生的程式碼的一部分。 產生的資料所在的.NET 語言例如[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]或[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，兩種策略時特別有用：  
  
-   產生的類別應該是部分。 這可讓您將內容加入至產生的程式碼。  
  
-   類別應該產生成對繼承自另一個。 基底類別應包含所有產生的方法和屬性，而衍生的類別應該包含建構函式。 這可讓您手動撰寫的程式碼，來覆寫任何所產生的方法。  
  
 在 XML 等其他產生的語言，使用`<#@include#>`指示詞，即可手動撰寫，並產生內容的簡單的組合。 在更複雜的情況下，您可能必須撰寫可結合任何手寫的檔案產生的檔案的後置處理步驟。  
  
 將常見的資料移入 include 檔或執行階段範本  
 若要避免重複類似的文字和多個範本中的程式碼區塊，請使用`<#@ include #>`指示詞。 如需詳細資訊，請參閱[T4 包含指示詞](../modeling/t4-include-directive.md)。  
  
 您可以也建置個別專案中，執行階段文字範本，然後將它們呼叫從設計階段範本。 若要這樣做，請使用`<#@ assembly #>`指示詞，以存取個別的專案。 如需範例，請參閱["繼承在文字範本 」 Gareth Jones 部落格中](http://go.microsoft.com/fwlink/?LinkId=208373)。  
  
 請考慮將大型區塊的程式碼移到不同的組件。  
 如果您有大型的程式碼區塊和類別功能區塊時，可能很有用的這段程式碼部分移到您在個別的專案編譯的方法。 您可以使用`<#@ assembly #>`指示詞，以存取範本中的程式碼。 如需詳細資訊，請參閱[T4 組件指示詞](../modeling/t4-assembly-directive.md)。  
  
 您可以將方法放在樣板可以繼承的抽象類別。 抽象類別必須繼承自<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>。 如需詳細資訊，請參閱[T4 範本指示詞](../modeling/t4-template-directive.md)。  
  
 產生程式碼，而不是組態檔  
 寫入變數的應用程式的一個方法是撰寫可接受組態檔的一般程式碼。 以這種方式撰寫的應用程式相當富彈性，並可以重新設定，而不需重建應用程式的商務需求變更時。 不過，這種方法的缺點是，應用程式會執行比更特定的應用程式效能不佳。 此外，其程式碼會更難閱讀及維護，部分原因是它必須永遠會處理大部分的泛型類型。  
  
 相反地，其變動的部分會產生編譯前的應用程式可以是強型別。 這使得更簡單且較可靠，撰寫手寫的程式碼，並將它整合到產生的組件的軟體。  
  
 若要取得的程式碼產生的完整優點，請嘗試產生程式碼，而不是組態檔。  
  
 使用產生的程式碼的資料夾  
 將範本與產生的檔案放在專案資料夾，名為**產生的程式碼**，讓它清除這些不應該直接編輯的檔案。 如果您建立自訂程式碼來覆寫或新增至產生的類別，將這些類別在名為資料夾**自訂程式碼**。 典型的專案結構看起來像這樣：  
  
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
  
## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>執行階段 （前置處理過後） 的 T4 範本的方針  
 將常見的資料移至繼承的範本  
 您可以使用繼承共用方法和 T4 文字範本之間的文字區塊。 如需詳細資訊，請參閱[T4 範本指示詞](../modeling/t4-template-directive.md)。  
  
 您也可以使用包含具有執行階段範本檔案。  
  
 將大型主體的程式碼移至部分類別。  
 每個執行階段範本會產生具有相同的名稱作為範本的部分類別定義。 您可以撰寫程式碼檔案，其中包含相同類別的另一個部分定義。 您可以將方法、 欄位和建構函式加入至這種方式中的類別。 這些成員可以從範本中的程式碼區塊呼叫。  
  
 這是程式碼是容易撰寫，，因為 IntelliSense 可這麼做的好處。 此外，您也可以達到更好的分隔展示檔之間的基本邏輯。  
  
 例如，在**MyReportText.tt**:  
  
 `The total is: <#= ComputeTotal() #>`  
  
 在**MyReportText Methods.cs**:  
  
 `private string ComputeTotal() { ... }`  
  
 允許的自訂程式碼： 提供擴充點  
 請考慮產生中的虛擬方法\<#+ 類別功能區塊 #>。 這可讓單一範本用於許多內容，而不需修改。 而不修改的範本，您可以建構在衍生的類別提供的最小的其他邏輯。 在衍生的類別可以是任一個規則的程式碼，或執行階段範本。  
  
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
  
## <a name="guidelines-for-all-t4-templates"></a>所有 T4 範本的方針  
 從文字產生的個別資料收集  
 請試著避免混用計算和文字區塊。 在每個文字範本中，使用第一個\<# 程式碼區塊 #> 來設定變數，並執行複雜的計算。 從範本或第一個值為第一個文字區塊\<#+ 類別功能區塊 #>，請避免長運算式，並避免迴圈和條件，除非它們包含文字區塊。 這種作法可以讓範本容易讀取與維護。  
  
 請勿使用`.tt`include 檔  
 使用不同的檔案名稱副檔名，例如`.ttinclude`include 檔。 使用`.tt`只有您想要的檔案處理為執行階段或設計階段文字範本。 在某些情況下，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]辨識`.tt`檔案，並自動設定其內容以供處理。  
  
 啟動每個範本做為固定的原型。  
 撰寫您想要產生，並確定它是正確的程式碼或文字的範例。 然後將其副檔名變更為.tt 並以累加方式插入程式碼會藉由讀取模型修改內容。  
  
 請考慮使用具類型的模型。  
 雖然您可以建立您的模型資料庫或 XML 結構描述，可能有助於建立網域特定語言 (DSL)。 DSL 的優點是它會產生的類別來代表結構描述和屬性，以表示屬性的每個節點。 這表示您可以藉由程式設計方面的商務模型。 例如:   
  
```  
Team Members:  
<# foreach (Person p in team.Members)   
 { #>   
    <#= p.Name #>   
<# } #>  
```  
  
 請考慮使用您的模型圖表。  
 許多模型最有效的方式會呈現，並管理簡稱為文字的資料表，特別是如果它們是非常大。  
  
 不過，對於某些類型的商業需求，請務必以釐清複雜的關聯性和工作流程集和圖表是最適合的媒體。 圖表有一個優點是容易與使用者及其他專案關係人討論。 藉由從層級的商務需求模型產生程式碼，確定您的程式碼更有彈性在需求變更時。  
  
 您也可以為特定領域語言 (DSL) 來設計您自己的圖表類型。 從 UML 和 Dsl，可以產生程式碼。 如需詳細資訊，請參閱[分析和模組化架構](../modeling/analyze-and-model-your-architecture.md)。  
  
## <a name="see-also"></a>請參閱  
 [使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)   
 [使用 T4 文字範本在執行階段產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)
