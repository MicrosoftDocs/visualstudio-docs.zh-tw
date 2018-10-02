---
title: 從 UML 類別圖產生程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates.TextTransformationDataCollectionEditor
helpviewer_keywords:
- code generation, UML class diagrams
- class diagrams - UML, generating code
- UML diagrams, generating code
ms.assetid: 2790e64d-7728-4c2e-a4dd-4131e795f730
caps.latest.revision: 53
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8874e5aa1c2dcf440c7cfed1cc2ce42c4187bdc1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485015"
---
# <a name="generate-code-from-uml-class-diagrams"></a>從 UML 類別圖產生程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[從 UML 類別圖產生程式碼](https://docs.microsoft.com/visualstudio/modeling/generate-code-from-uml-class-diagrams)。  
  
若要從 Visual Studio 中的 UML 類別圖產生 Visual C#.NET 程式碼，請使用**產生的程式碼**命令。 根據預設，命令會針對您選取的每一個 UML 類型來產生 C# 類型。 您可以修改或複製產生程式碼的文字範本來修改及擴充此行為。 您可以針對模型內的不同封裝中所包含的類型來指定不同的行為。  
  
 **產生的程式碼**命令是特別適合從使用者選取的項目，產生程式碼並產生一個檔案的每個 UML 類別或其他項目。 例如，此螢幕擷取畫面顯示從兩個 UML 類別產生的兩個 C# 檔案。  
  
 或者，如果您想要產生程式碼中產生的檔案沒有 1:1 關聯性 UML 項目時，您可以考慮撰寫文字範本，會叫用**轉換所有範本**命令。 如需有關該方法的詳細資訊，請參閱 <<c0> [ 從 UML 模型產生檔案](../modeling/generate-files-from-a-uml-model.md)。  
  
 ![UML 類別圖表] 和 [產生的 C&#35;類別檔案。](../modeling/media/oob-gencode1.png "oob_GenCode1")  
  
 如需 Visual Studio 的 UML 類別圖的詳細資訊，請參閱下列主題：  
  
-   [UML 類別圖表：參考](../modeling/uml-class-diagrams-reference.md)  
  
-   [UML 類別圖表：方針](../modeling/uml-class-diagrams-guidelines.md)  
  
 若要查看哪些版本的 Visual Studio 支援 UML 類別圖，請參閱[architecture and modeling tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="using-the-generate-code-command"></a>使用產生程式碼命令  
 下列程序描述的預設行為**產生的程式碼**命令：  
  
#### <a name="to-generate-a-separate-file-for-each-element"></a>若要針對每一個項目產生個別的檔案  
  
1.  建立包含類別的 UML 模型。 您可能會想要將造型套用至模型項目。  
  
     如需詳細資訊，請參閱 <<c0> [ 預設程式碼產生轉換](#default)。  
  
2.  在類別圖表或在**UML 模型總管**，選取您要產生程式碼項目。 您可以選取下列其中一項：  
  
    -   一組特定的項目。  
  
    -   封裝或模型，可從其內容中產生程式碼。  
  
    -   圖表，可選取圖表上的所有項目。  
  
3.  開啟選取的項目捷徑功能表，然後選擇**產生的程式碼**。  
  
     您使用第一次**產生的程式碼**在特定模型中，對話方塊隨即出現。 此對話方塊可讓您編輯此模型的程式碼產生參數。  
  
     選擇**確定**除非您知道您想要變更這些參數。  
  
     若要稍後再返回此對話方塊中，開啟**UML 模型總管**。 開啟模型專案的捷徑功能表，然後選擇 **設定的程式碼產生**。 如需詳細資訊，請參閱 <<c0> [ 自訂產生程式碼命令](#custom)。  
  
 隨即產生包含 C# 程式碼的檔案。 在預設案例中，將會針對每一個類型產生檔案，而且會在 C# 類別庫專案中產生檔案。 然而，您可以自訂此行為。 如需詳細資訊，請參閱 <<c0> [ 自訂產生程式碼命令](#custom)。  
  
 某些驗證測試會套用到模型中，以確保它可以轉譯為 C#。 如果這些測試失敗，便會顯示錯誤訊息，而且不會執行程式碼產生作業。 如果您已經建立驗證功能表命令，則不會針對驗證命令失敗的任何項目產生程式碼。 如需詳細資訊，請參閱 <<c0> [ 定義 UML 模型的驗證條件約束](../modeling/define-validation-constraints-for-uml-models.md)。  
  
##  <a name="default"></a> 預設程式碼產生轉換  
 本節摘要說明所產生的結果**產生的程式碼**命令時，除非您自訂的命令。 如需詳細資訊，請參閱 <<c0> [ 自訂產生程式碼命令](#custom)。  
  
-   將會針對您在 UML 模型中選取的每一個類型各產生一個 C# 類型。 每個型別放在不同的程式碼檔底下**GeneratedCode**資料夾。  
  
-   如果 UML 類型包含在封裝內，則產生的 C# 類型會置於命名空間內，而且會在與此命名空間同名的資料夾中產生檔案。  
  
-   針對 UML 類別的每一個 `Attribute` 產生 C# 屬性。  
  
-   針對 UML 類型的每一個 `Operation` 產生 C# 方法。  
  
-   針對此類別參與的每一個可巡覽的關聯產生 C# 欄位。  
  
 您可以藉由將造型加入至每一個 UML 類型來控制產生之 C# 類型的更多屬性。  
  
|**若要建立這個 C# 類型**|**繪製這個 UML 類型**|**套用這個造型**|  
|---------------------------------|----------------------------|-------------------------------|  
|類別|類別|\<沒有任何 > 或<br /><br /> C# 類別|  
|介面|介面|\<沒有任何 > 或<br /><br /> C# 介面|  
|列舉|列舉|\<沒有任何 > 或<br /><br /> C# 列舉|  
|委派|類別|C# 委派|  
|結構|類別|C# 結構|  
  
#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>若要在類型或其他項目上設定造型  
  
1.  開啟快顯功能表項目在圖表或在**UML 模型總管**，然後選擇**屬性**。  
  
2.  在 [**屬性**] 視窗中，選擇的下拉式箭號**造型**屬性，，然後選取您想要套用的造型核取方塊。  
  
    > [!TIP]
    >  如果 C# 造型並未出現，請針對此模型或是包含您有興趣之模型項目的封裝來啟用 C# 設定檔。 選取封裝或模型中的根**UML 模型總管**。 然後在**屬性**] 視窗中，選擇**設定檔**，然後啟用 [C# 設定檔。  
  
3.  依序展開**造型**屬性，以查看您可以設定的其他屬性。  
  
 **描述**的型別、 屬性、 作業和關聯的屬性都會寫入`<summary>`中產生的程式碼的註解。 連結至類型的註解項目會寫入 `<remarks>` 註解。  
  
## <a name="varying-the-generated-code"></a>各種產生的程式碼  
 產生的程式碼會因為每一個類型、屬性或作業的屬性而異。 例如，如果您設定**Is Abstract**屬性的類別設為 true，則`abstract`關鍵字會出現在產生的類別。 如果您設定**多重性**要屬性**0.\***，則產生的屬性會有`IEnumerable<>`型別。  
  
 此外，每個造型都會提供您可以設定的幾個額外屬性。 這些值會解譯成 C# 程式碼中適當的關鍵字。 例如，如果您在類別上設定 `Is Static` 屬性，則 C# 類別將會是 `static`。  
  
 若要設定這些額外的屬性，請選取此類別或圖表中的其他項目。 在 屬性 視窗中，依序展開**造型**，然後展開 C# 造型，例如**C# 類別**。  對於類別而言，這些額外的屬性包括：  
  
-   CLR 屬性  
  
-   Is Partial  
  
-   Is Static  
  
-   Is Unsafe  
  
-   封裝可視性  
  
 每一個屬性 (Attribute) 和作業也會擁有您可以設定的造型屬性 (Property)。 如果您看不見屬性在新的屬性上，執行**產生的程式碼**。  
  
##  <a name="custom"></a> 自訂產生程式碼命令  
 **產生的程式碼**轉換您的模型項目，使用文字範本的一組命令運作。 如需文字範本的詳細資訊，請參閱[程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)。  
  
 中的一組指定的範本*文字範本繫結*。 文字範本繫結指定的範本應該套用，產生的輸出應放置的位置，和其他參數**產生的程式碼**命令。  
  
 當您第一次執行**產生的程式碼**命令特定的模型中，它會將一組預設的範本繫結附加至模型的根目錄。 這些繫結會套用至模型內的所有項目。  
  
 但是，您可以覆寫及加入至這些預設繫結，方法是將您自己的繫結附加至封裝、類別或其他項目。 繫結會套用至附加它的項目內所包含的所有項目。 例如，如果您希望特定封裝內的所有類型都由一組不同的範本來轉換或者輸出到不同的資料夾，您可以將範本繫結附加至此封裝。  
  
 若要檢查附加至模型項目範本繫結，選擇省略符號 **[...]** 中**文字範本繫結**屬性 視窗中的屬性。  
  
 **產生的程式碼**命令適用於您已選取每個模型項目範本。 對於每一個項目而言，套用的範本集合為附加至其容器的合併範本集合，一直到模型的根 (包含在內)。  
  
 如果此集合中的兩個範本繫結有相同的名稱，則較小容器內的繫結會覆寫較大容器內的繫結。 例如，模型根擁有名稱繫結**類別樣板**。 若要讓您自己的範本套用至特定封裝的內容，定義自己的範本繫結具有名稱**類別樣板**。  
  
 可以將一個以上的範本套用至模型項目。 您可以從每一個模型項目產生一個以上的檔案。  
  
> [!NOTE]
>  附加至模型根的繫結會當做模型內所有項目的預設值。 若要查看這些預設繫結，請開啟**UML 模型總管**。 開啟模型專案的捷徑功能表，然後選擇**設定的程式碼產生**。 或者，在 [UML 模型總管] 中選取模型的根。 在 [屬性] 視窗中，選擇 **[...]** 中**文字範本繫結**屬性。 直到您已使用的繫結不會出現**產生的程式碼**至少一次命令。 範本繫結無法附加至圖表。  
  
#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>若要將文字範本繫結附加至封裝或其他模型項目  
  
1.  在  **UML 模型總管**，開啟模型項目的捷徑功能表，然後選擇**屬性**。 一般來說，您會將文字範本繫結附加至封裝或模型的根。  
  
2.  在 [**屬性**] 視窗中，選擇省略符號按鈕 (**[...]**) 中**文字範本繫結**屬性。  
  
     **文字範本繫結** 對話方塊隨即出現。  
  
3.  選擇**新增**來建立新的文字範本繫結。  
  
     \-或-  
  
     選取現有的繫結加以編輯。  
  
     每一個範本繫結都會定義應該如何將指定的範本套用到您所選取的模型項目，以及它所包含的其他模型項目。  
  
4.  在此對話方塊中，設定文字範本繫結的屬性。  
  
    |**Property**|**描述**|  
    |------------------|---------------------|  
    |名稱|這個繫結的名稱。 若要覆寫從包含的封裝或模型繼承的繫結，請使用與您想要覆寫的繫結相同的名稱。|  
    |覆寫|若為 true，則會覆寫任何現有的程式碼。|  
    |目標名稱|產生的檔案名稱。<br /><br /> 您可以將運算式插入這個字串這類`{Name}`或`{Owner.Name}`。 例如，您可以撰寫： `{Owner.Name}_{Name}`。 在模型項目上評估此運算式。 它可以使用項目的屬性，但不能使用方法。 若要尋找可以使用哪些屬性，看看中的型別屬性**Microsoft.VisualStudio.Uml。\***. **重要事項︰** `{Name}`或是`{Owner.Name}`只在**目標名稱**屬性。   若要變更產生之類別的名稱，您必須修改此範本。 如需詳細資訊，請參閱 <<c0> [ 撰寫文字範本](#writing)。|  
    |專案路徑|指定將包含轉換輸出檔案的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案路徑。 使用具類型的值來建立新的專案。 選擇省略符號按鈕 (**[...]**) 來選取現有的專案。<br /><br /> 將會建立新的專案 (如果不存在)。 這會是 C# 類別庫專案。<br /><br /> 若要這麼做，您必須直接輸入專案。 您可以包含環境變數巨集，例如 %ProgramFiles% or %LocalAppData%。|  
    |目標目錄|產生目標檔案的資料夾。 此路徑相對於專案資料夾。<br /><br /> 您可以使用 `{PackageStructure}` 運算式插入路徑，此路徑會對應到包含的封裝名稱。 預設值是 `\GeneratedCode\{PackageStructure}`。 您也可以包含環境變數，例如 %TEMP% 或 %HomePath%。 **重要事項︰** `{PackageStructure}`只在**目標目錄**屬性。  |  
    |範本檔路徑。|將要執行轉換的範本。<br /><br /> 您可以使用提供的範本，或建立自己的範本。 您可以在下列位置找到提供的範本：<br /><br /> …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\|  
  
5.  您可以將不限數目的繫結附加至項目中。  
  
##  <a name="writing"></a> 撰寫文字範本  
 您可以撰寫自己的文字範本。 文字範本可以產生程式碼或任何其他種類的文字檔。  
  
 我們建議您一開始先修改標準範本的複本。 您可以從下列位置複製範本：  
  
 …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\  
  
 若要了解文字範本，請參考下列主題。  
  
-   文字範本是結果檔案的原型，而且包含了結果文字以及讀取模型的程式碼。 如需詳細資訊，請參閱 <<c0> [ 程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)。  
  
-   若要巡覽程式碼中的 UML 模型，您必須使用 UML API。 如需詳細資訊，請參閱 <<c0> [ 巡覽 UML 模型](../modeling/navigate-the-uml-model.md)並[UML 模型擴充性的 API 參考](../modeling/api-reference-for-uml-modeling-extensibility.md)。  
  
 若要使用的範本**產生的程式碼**命令時，您必須包含 Modeling 指示詞。 例如:   
  
 `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`  
  
 `ElementType` 屬性會定義套用這個範本之 UML 項目的類型。  
  
 在此範本中，`this` 屬於具有下列屬性的暫時類別：  
  
-   `Element` = 套用此範本的 UML <xref:Microsoft.VisualStudio.Uml.Classes.IElement>。  
  
-   `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>  
  
-   `Host`: <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
-   `ModelBus`: <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>. 如需詳細資訊，請參閱 <<c0> [ 整合 UML 模型與其他模型及工具](../modeling/integrate-uml-models-with-other-models-and-tools.md)。  
  
-   `ProfileName` = "C#Profile"。  
  
-   `ServiceProvider`: <xref:System.IServiceProvider>  
  
-   `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>.  
  
-   `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>. 這是 UML ModelStore 實作所在的 Visualization and Modeling SDK 存放區。 若要取得 UML <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore>，請使用 `this.Element.GetModelStore()`。  
  
 當您撰寫文字範本時，可能會發現以下要點非常實用。 這項資訊會詳述[程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)。  
  
-   您可以在 `Output` 指示詞中設定結果的副檔名。 每一個文字範本中都需要一個 `Output` 指示詞。  
  
-   此範本會自動參考某些組件。 例如，這些組件包括 System.dll 和 Microsoft.VisualStudio.Uml.Interfaces.dll。  
  
     若要在您產生的程式碼中使用其他組件，您必須使用 `Assembly` 指示詞。 例如：  
  
     `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`  
  
-   某些命名空間 (例如 `System`) 會自動匯入您的程式碼內。 對於其他命名空間，您可以依照使用 `Import` 陳述式的相同方式來使用 `using` 指示詞。 例如：  
  
     `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`  
  
     `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`  
  
-   使用 `Include` 指示詞可參考另一個檔案的文字。  
  
-   以括弧括住的範本部分`<# ... #>`由執行**產生的程式碼**命令。 這些括號外面的範本部分會複製到結果檔案。 請務必區分產生程式碼與產生的文字。 產生的文字可以使用任何語言。  
  
-   `<#= Expressions #>` 會評估及轉換為字串。  
  
## <a name="see-also"></a>另請參閱  
 [UML 類別圖： 參考](../modeling/uml-class-diagrams-reference.md)   
 [UML 類別圖： 方針](../modeling/uml-class-diagrams-guidelines.md)   
 [透過 UML 模型產生檔案](../modeling/generate-files-from-a-uml-model.md)



