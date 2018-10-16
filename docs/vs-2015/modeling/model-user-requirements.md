---
title: 模型使用者需求 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- requirements
- stories
- UML, modeling requirements
ms.assetid: 359900f8-6d69-493d-bfdf-2c9069c74a26
caps.latest.revision: 30
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7ac55e2ec1d07c32c154b69cd467dfc534da6ae3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215822"
---
# <a name="model-user-requirements"></a>模型使用者需求
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 透過繪製使用者活動的圖表，以及系統協助他們達到其目標所扮演的角色，幫助您了解、討論和溝通使用者需求。 需求模型是這些圖表的其中一組，各著重於使用者需求的不同層面。 如需視訊示範，請參閱︰ [Modeling the Business Domain](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/)(模型化商務網域)。  
  
 若要查看支援各類型之模型的 Visual Studio 版本，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
 需求模型可協助您：  
  
-   著重於系統的外部行為，與其內部設計分開。  
  
-   使用自然語言，更明確地描述使用者和利害關係人的需求。  
  
-   定義使用者、開發人員和測試人員可使用的一致詞彙表。  
  
-   減少需求的缺口和不一致。  
  
-   減少回應需求變更所需的工作。  
  
-   規劃功能的開發順序。  
  
-   使用模型作為進行系統測試的基礎，以設定測試與需求之間的清楚關聯性。 需求變更時，此關聯性可協助您正確地更新測試。 這可確保系統符合新的需求。  
  
 如果您使用需求模型來聚焦與使用者或其業務人員的討論，並在每次重複的開頭重新瀏覽該討論，則需求模型提供最大的好處。 撰寫程式碼之前，您不需要詳細地完成它。 局部運作的應用程式 (即使極為簡化) 通常會構成使用者需求討論的最生動基礎。 模型是彙總這些討論結果的有效方法。 如需詳細資訊，請參閱 <<c0> [ 在開發程序中使用模型](../modeling/use-models-in-your-development-process.md)。  
  
> [!NOTE]
>  在這些主題中，「系統」表示您正在開發的系統或應用程式。 它可能是許多軟體和硬體元件的大型集合、單一應用程式或較大系統內的軟體元件。 在每種情況下，需求模型都會描述可在系統外部看到的行為 (不論是透過使用者介面或 API)。  
  
## <a name="common-tasks"></a>一般工作  
 您可以建立數個不同的使用者需求檢視。  每個檢視都提供特定類型的資訊。  建立這些檢視時，最好經常切換使用不同的檢視。 您可以從任何檢視開始。  
  
|圖表或文件|需求模型中的描述|區段|  
|-------------------------|-----------------------------------------------|-------------|  
|使用案例圖|系統使用者和其對系統的處理方式。|[描述如何使用您的系統](#UseCases)|  
|概念性類別圖|用來描述需求的類型字彙；系統介面上可見的類型。|[定義用來描述需求的詞彙](#RequirementsClasses)|  
|活動圖表|使用者和系統或其組件所執行活動之間的工作和資訊流程。|[顯示使用者與系統之間的工作流程](#Workflow)|  
|順序圖表|使用者和系統或其組件之間的互動順序。 活動圖表的替代檢視。|[顯示使用者與系統之間的互動](#Sequences)|  
|其他文件或工作項目|效能、安全性、可用性和可靠性準則。|[描述服務需求品質](#QoSRequirements)|  
|其他文件或工作項目|非特定使用案例的特定條件約束和規則|[示範商務規則](#BusinessRules)|  
  
 請注意，大部分的圖表類型都可以用於其他用途。 如需圖表類型的概觀，請參閱 <<c0> [ 建立應用程式模型](../modeling/create-models-for-your-app.md)。 如需繪製圖表的基本資訊，請參閱[編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)。  
  
##  <a name="UseCases"></a> 描述如何使用您的系統  
 建立使用案例圖，以描述系統使用者和其系統用途。 使用案例代表系統使用者的目標，以及他們執行以達到目標的程序。  
  
 例如，線上餐點銷售系統必須允許客人從菜單選擇品項，而且必須允許供應餐廳更新菜單。 您可以在使用案例圖中彙整這項資訊：  
  
 ![客戶和餐廳的使用案例](../modeling/media/uml-reqmuc1.png "UML_ReqmUC1")  
  
 您也可以示範較小的案例如何組成使用案例。 例如，訂餐屬於購買餐點，其中也包括付款和送餐：  
  
 ![系統參與付款而非外送。](../modeling/media/uml-reqmuc2.png "UML_ReqmUC2")  
  
 您也可以示範所開發系統範圍中包含的使用案例。 例如，圖例中的系統不會參與「送餐」(Deliver Meal) 使用案例。 這有助於設定開發工作的內容 (在使用案例圖中，子系統容器可以用來代表系統或其元件)。  
  
 它也協助小組討論要在後續版本中包括的內容。 例如，您可以討論在系統的初始版本中，是否直接在餐廳與客人之間安排「餐點付款」(Pay for Meal)，而不是透過系統。 在該情況下，於初版中，您可以將「餐點付款」(Pay for Meal) 移到「立即用餐系統」(Dinner Now System) 矩形外部。  
  
 使用案例圖僅提供使用案例摘要。 若要提供更詳細的描述，您可以連結圖表上的使用案例來區隔文件，以及將它們連結至其他圖表。 若要了解如何執行這項操作，請參閱[將使用案例連結到文件與圖表](../modeling/link-a-use-case-to-documents-and-diagrams.md)。  
  
 繪製使用案例圖可協助您的小組：  
  
-   聚焦於使用者預期如何處理系統，而不會因實作詳細資料而分心。  
  
-   討論系統的範圍或系統的特定版本。  
  
 下列主題提供詳細資訊：  
  
|深入了解|讀取|  
|--------------------|----------|  
|如何建立使用案例的更多詳細資訊|[UML 使用案例圖：方針](../modeling/uml-use-case-diagrams-guidelines.md)|  
|使用案例圖上的項目|[UML 使用案例圖：參考](../modeling/uml-use-case-diagrams-reference.md)|  
|如何透過使用案例開發程式碼|[建立應用程式架構的模型](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="RequirementsClasses"></a> 定義用來描述需求的詞彙  
 您可以使用 UML 類別圖，協助您開發用於下列用途之商務概念的一致詞彙：  
  
-   由使用者自行討論系統運作的商務。  
  
-   描述使用者需求，例如，在使用案例、商務規則和使用者劇本的描述中。  
  
-   在系統的 API 或透過使用者介面交換的資訊類型。  
  
-   系統或接受度測試的描述。  
  
 用於此用途時，UML 類別圖的內容稱為概念性類別圖 (也稱為 *「網域模型」* (domain model) 或 *「分析類別模型」*(analysis class model))。  
  
 在概念性類別圖中，只會顯示需求描述中所需的類別，而不會顯示系統內部設計的任何詳細資料。 此圖表不會顯示系統內部設計的任何詳細資料。 通常不會顯示概念性類別的作業或介面。  
  
 例如，您可以繪製「立即用餐系統」(Dinner Now System) 的這些概念性類別：  
  
 ![類別菜單、 訂單，功能表項目，訂單項目。](../modeling/media/uml-reqmcd1.png "UML_ReqMCD1")  
  
 概念性類別圖提供您在需求模型中使用的詞彙。 例如，在「點餐」(Order a Meal) 使用案例的詳細描述中，您可能會撰寫：  
  
 客人選擇從中建構 *「訂單」* (Order) 的 *「菜單」*(Menu)，然後從 *「菜單」* (Menu) 中選取 *「菜單項目」* (Menu Items)，以在 *「訂單」* (Order) 中建立 *「訂單項目」*(Order Items)。  
  
 請注意，該描述中所用的詞彙是模型中的類別名稱。 此圖表會移除這些類別間之關聯性的模稜兩可。 例如，它會清楚顯示每筆「訂單」(Order) 只會與一個「菜單」(Menu) 相關聯。  
  
 使用者需求的誤解經常可以追溯自單字詳細意義的誤解。 例如，大部分餐廳都了解「菜單」(Menu) 和「訂單」(Order) 這兩個詞彙，但「訂單」(Order) 上的項目與「菜單」(Menu) 上的項目的差異較不明顯。 與商務利害關係人討論需求時，一定要公開這些差異。 類別圖是協助您釐清詞彙和其關聯性的有用工具。  
  
 概念性類別模型可以形成用來描述系統商務邏輯的基本詞彙。 但是，軟體中的類別通常會比概念性模型更為複雜，因為您的實作必須考量效能、分佈、彈性和其他因素的問題。 您經常可以在某個系統中看到概念性類別的數個不同實作。  
  
 例如，在系統的不同組件以及組件之間的不同介面上，Order 可能會以 XML、SQL、HTML 和 C# 呈現。 「訂單」(Order) 與「菜單」(Menu) 之間的關聯可以使用多種不同的方式呈現，例如 C# 程式碼內的參考、資料庫中的關係，或 XML 中的交互參考識別碼。 但是，儘管有這些變化，概念性模型還是提供適用於軟體每個組件的重要資訊。 從範例中的類別圖得知，在每個實作中，一個「菜單」(Menu) 只會與一個「訂單」(Order) 相關聯。  
  
 繪製需求類別圖可協助您的小組：  
  
-   定義並標準化使用者需求討論中所使用的基本詞彙。  
  
-   釐清這些詞彙之間的關聯性。  
  
 下列主題提供詳細資訊：  
  
|深入了解|讀取|  
|--------------------|----------|  
|尋找需求類別的更多詳細資訊|[UML 類別圖表：方針](../modeling/uml-class-diagrams-guidelines.md)|  
|概念性類別圖上的項目|[UML 類別圖表：參考](../modeling/uml-class-diagrams-reference.md)|  
|如何透過概念性類別開發程式碼|[建立應用程式架構的模型](../modeling/model-your-app-s-architecture.md)|  
  
 在概念性類別圖中，通常不適合將箭號放在關聯上來代表巡覽性。 原因是圖表不代表實作。 關聯代表真實世界物件之間的關聯性。 下列 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 擴充功能會將非方向性箭號設為預設值： [Sample: UML Domain Modeling features](http://go.microsoft.com/fwlink/?LinkId=213849)(範例：UML 網域模型功能)。  
  
##  <a name="BusinessRules"></a> Showing Business Rules  
 商務規則是未與特定使用案例相關聯的需求，而且應該會在系統中觀察到。  
  
 許多商務規則是概念性類別間之關聯性的條件約束。 您可以撰寫這些*靜態 * * 商務規則*做為概念性類別圖上的相關類別相關聯的註解。 例如:   
  
 ![附加至 Order 類別的註解的規則。](../modeling/media/uml-reqmcd2.png "UML_ReqmCD2")  
  
 *「動態商務規則」* (dynamic business rules) 限制允許的事件序列。 例如，您可以使用序列或活動圖來示範使用者必須先登入，才能對系統執行其他作業。  
  
 不過，許多動態規則在取代為靜態規則之後會較為有效。 例如，您可以將布林值屬性 'Logged In' 加入概念性類別模型中的類別。 您將 Logged In 加入為登入使用案例中的後置條件，並將它加入為其他大部分使用案例的前置條件。 這種方法可讓您避免定義所有可能的事件序列組合。 需要將新的使用案例加入模型時，它也更有彈性。  
  
 請注意，這裡的選擇是有關如何定義需求，而且這與如何在程式碼中實作需求無關。  
  
 下列主題提供詳細資訊：  
  
|深入了解|讀取|  
|--------------------|----------|  
|尋找和記錄靜態商務規則的更多詳細資訊|[UML 類別圖表：方針](../modeling/uml-class-diagrams-guidelines.md)|  
|概念性類別圖上的項目|[UML 類別圖表：參考](../modeling/uml-class-diagrams-reference.md)|  
|如何開發遵守商務規則的程式碼|[建立應用程式架構的模型](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="QoSRequirements"></a> Describing Quality of Service Requirements  
 有數種類別的服務需求品質。 包括下列各項：  
  
-   效能  
  
-   安全性  
  
-   可用性  
  
-   可靠性  
  
-   加強性  
  
 您可以在特定使用案例描述中包含其中一些需求。 其他需求非使用案例所特定，而且最有效地撰寫於不同的文件中。 如果可以，最好遵守需求模型所定義的詞彙。 在下列範例中，請注意，要求中所使用的主要單字是先前圖例中的行動標題、使用案例和類別：  
  
 如果餐廳刪除「菜單項目」(Menu Item) 時，客人正在點餐，則會以紅色顯示參照該「菜單項目」(Menu Item) 的任何「訂單項目」(Order Item)。  
  
 下列主題提供詳細資訊：  
  
|深入了解|讀取|  
|--------------------|----------|  
|記錄服務品質需求的更多詳細資訊|[定義服務需求品質的方針](http://msdn.microsoft.com/en-us/9677a437-c2cb-4ac4-8c2d-4e3350005f06)|  
|將其他文件附加至使用案例|[將使用案例連結到文件與圖表](../modeling/link-a-use-case-to-documents-and-diagrams.md)|  
|如何開發遵守服務需求品質的程式碼|[建立應用程式架構的模型](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="Workflow"></a> 顯示使用者與系統之間的工作流程  
 您可以使用活動圖示範不同使用案例之間的工作流程。 繪製示範使用者在系統內外部所執行之主要工作的活動圖，這十分適用於開始需求模型。  
  
 例如:   
  
 ![三個動作和一個迴圈的活動。](../modeling/media/uc-reqmwfact.png "UC_ReqmWFAct")  
  
 您可以繪製使用案例圖和活動圖來顯示相同資訊的不同檢視。  使用案例圖可以更有效地顯示較大活動中較小動作的巢狀結構，但不會顯示工作流程。 例如:   
  
 ![前述動作的使用案例](../modeling/media/uml-reqmwfuc.png "UML_ReqmWFUC")  
  
 請注意，您也可以使用活動圖描述軟體內的演算法，但是，使用商務程序的圖表時，聚焦於系統外部可見的動作。  
  
 下列主題提供詳細資訊：  
  
|深入了解|讀取|  
|--------------------|----------|  
|如何定義商務工作流程的詳細資訊|[UML 活動圖表：方針](../modeling/uml-activity-diagrams-guidelines.md)|  
|活動圖上的項目|[UML 活動圖表：參考](../modeling/uml-activity-diagrams-reference.md)|  
|如何透過活動圖開發程式碼|[建立應用程式架構的模型](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="Sequences"></a> 顯示使用者與系統之間的互動  
 您可以使用循序圖來示範系統與外部行動之間或系統不同組件之間的訊息交換。 這提供極清楚顯示互動序列的使用案例中步驟的檢視。 在使用案例中有數個互動方以及系統具有 API 的情況下，循序圖特別有用。  
  
 例如:   
  
 ![包含系統和行動的順序圖表。](../modeling/media/uml-reqmseq.png "UML_ReqmSeq")  
  
 循序圖的其中一個優點在於很容易就可以看到進入您正在建構之系統的訊息為何。 若要設計系統，您可以將單一系統生命線取代為其每個元件的個別生命線，然後顯示它們之間回應每個內送訊息的互動。  
  
 下列主題提供詳細資訊：  
  
|深入了解|讀取|  
|--------------------|----------|  
|如何定義互動的詳細資訊|[UML 順序圖表：方針](../modeling/uml-sequence-diagrams-guidelines.md)|  
|循序圖上的項目|[UML 順序圖表：參考](../modeling/uml-sequence-diagrams-reference.md)|  
|如何透過循序圖開發程式碼|[建立應用程式架構的模型](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="using-a-model-to-reduce-inconsistencies"></a>使用模型來減少不一致  
 建立模型通常會導致大幅降低使用者需求中的不一致和語意模糊。 不同的利害關係人通常會對系統運作的商務世界有不同的了解。 因此，您的第一項工作是解決用戶端之間的這些差異。  
  
 您將發現在建立模型時會自然發生許多商務網域問題。 將這些問題加諸您的使用者，可減少專案中後續階段的變更需求。 以下是一些您可以先問您自己的特定問題，接著詢問商務利害關係人答案是否不清楚：  
  
-   對於需求模型中的每個類別，詢問「什麼使用案例建立這個類別的執行個體？」 例如，在線上點餐服務中，您可能會問「什麼使用案例建立「餐廳菜單」 類別的執行個體？」 這會導致如何將新餐廳註冊到服務以及提供其菜單的討論。 您可以詢問有關什麼建立或變更屬性和關聯的類似問題。  
  
-   對於需求模型中的每個使用案例，嘗試描述類別圖所提供單字中每個使用案例的結果或後置條件。 透過在發生使用案例之前和之後草擬類別執行個體來顯示使用案例的效果，這通常十分有用。 例如，如果使用案例後置條件指出「將菜單項目加入客人訂單」，請草擬「訂單」和「菜單項目」類別的執行個體。 以不同的色彩或新的繪圖，顯示使用案例的效果 (例如新連結或新物件)。 這經常會造成模型中所需資訊的討論。 雖然需求類別未直接與實作相關，但是它們確實會描述您系統儲存和傳輸所需的資訊。  
  
-   詢問屬性和關聯的條件約束，特別是包含多個屬性或關聯的條件約束。  
  
-   詢問有效和無效的使用案例序列，方法是繪製循序圖或活動圖來說明它們。  
  
 檢查不同圖表所提供之檢視間的關聯性，即可快速了解使用者工作的主要概念，並幫助他們了解系統中他們所需的項目。 您也會深入了解利害關係人最不關心的需求。 您可以規劃在專案的早期階段開發這些功能 (至少為簡化形式)，讓使用者實驗它們。  
  
## <a name="see-also"></a>另請參閱  
 [編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)   
 [透過模型開發測試](../modeling/develop-tests-from-a-model.md)   
 [在您的開發程序中使用模型](../modeling/use-models-in-your-development-process.md)   
 [您的應用程式架構模型](../modeling/model-your-app-s-architecture.md)   
 [範例 VS 擴充功能︰ UML 網域模型功能](http://go.microsoft.com/fwlink/?LinkId=213849)   
 [範例 VS 擴充功能： 依據造型色彩 UML 項目](http://go.microsoft.com/fwlink/?LinkID=213841)   
 [範例 VS 擴充功能︰ UML 項目連結至圖表、 檔案和其他項目](http://go.microsoft.com/fwlink/?LinkID=213813)   
 [範例 VS 擴充功能： 對齊 UML 圖表上的圖形](http://go.microsoft.com/fwlink/?LinkID=213809)   
 [視訊︰ 模型化商務網域](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/)



