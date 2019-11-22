---
title: 案例：使用視覺化和模型化來變更您的設計 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
ms.assetid: ccc80825-a4a0-44fa-a0bb-f95254785a3b
caps.latest.revision: 63
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cafc4e2a87a31603e1f8cef4174d8538be768428
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296027"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>情節：使用視覺化和模型功能變更設計
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

請使用 Visual Studio 中的視覺化與模型工具，確定您的軟體系統符合使用者的需求。 請使用像是整合模組化語言 (UML) 圖表、Code Map、分層圖與類別圖表等工具，以進行下列項目：

 若要查看支援每項工具的 Visual Studio 版本，請參閱 [Architecture and Modeling Tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

- 釐清使用者的需求與商務程序。

- 探索現有程式碼並將其視覺化。

- 描述現有系統的變更。

- 確認系統符合其需求。

- 讓程式碼與設計保持一致。

  本逐步解說：

- 描述這些工具如何替軟體專案帶來益處。

- 不論您的開發方式為何，都能藉由範例情節來示範如何使用這些工具。

  若要深入了解這些工具與其所支援情節的詳細資訊，請參閱：

- [分析架構並製作架構模型](../modeling/analyze-and-model-your-architecture.md)

- [視覺化程式碼](../modeling/visualize-code.md)

- [建立應用程式模型](../modeling/create-models-for-your-app.md)

## <a name="ScenarioOverview"></a> 情節概觀
 本情節描述兩間虛構公司 Dinner Now 與 Lucerne Publishing 在軟體開發週期所發生的事件。 Dinner Now 在西雅圖提供網站架構的餐點外送服務。 客戶可以在 Dinner Now 網站上訂餐並付款。 然後訂單便會傳送到合適的當地餐廳以準備外送。 Lucerne Publishing 是一家位在紐約的公司，營業項目涵蓋幾項網路與非網路服務。 例如，客戶可以在其經營的網站張貼對餐廳的評論。

 Lucerne 最近併購 Dinner Now，並想要進行下列變更：

- 在 Dinner Now 網站中加入餐廳評論功能，藉此整合雙方網站。

- 將 Dinner Now 付款系統更換成 Lucerne 系統。

- 將 Dinner Now 服務範圍擴展到全地區。

  Dinner Now 使用的是 SCRUM 與 eXtreme 程式設計。 其測試涵蓋範圍非常大，不受支援的程式碼非常少。 會先建立小型但可運作的系統版本，然後以累加的方式加入功能，藉此將風險降到最低。 他們採取短暫且頻繁的反覆項目來開發程式碼。 這讓他們對所做的變更很有信心，也能經常重構程式碼，同時避免「預先大量設計」(Big Design Up Front)。

  Lucerne 則維持一個相當大型且複雜的系統集合，其中有些系統已超過 40 年。 有鑑於舊版程式碼的複雜度及範圍，他們對變更相當地謹慎。 他們遵循更嚴格的開發程序，要求設計詳細的解決方案，並將開發期間所做的設計與變更記錄下來。

  雙方小組都使用 Visual Studio 的模型圖表，協助他們開發符合使用者需求的系統。 他們使用 Team Foundation Server 搭配其他工具，協助其規劃、組織及管理工作。

  如需 Team Foundation Server 的詳細資訊，請參閱：

- [計劃與追蹤工作](#PlanningTracking)

- [在經過更新的程式碼中進行測試、驗證及檢查](#TestValidateCheckInCode)

## <a name="ModelingDiagramsTools"></a> 架構與模型圖表在軟體開發的角色
 下表描述在軟體開發週期多個及多種階段中，這些工具可以扮演的角色：

||**使用者需求模型化**|**商務程序模型化**|**系統架構與設計**|**程式碼視覺化與探索**|**驗證**|
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|
|使用案例圖表 (UML)|√|√|||√|
|活動圖表 (UML)|√|√|√||√|
|類別圖表 (UML)|√|√|√||√|
|元件圖表 (UML)|√|√|√||√|
|順序圖表 (UML)|√|√|√||√|
|領域特定語言 (DSL) 圖表|√|√|√|||
|分層圖、圖層驗證|||√|√|√|
|Code Map|||√|√|√|
|類別設計工具 (以程式碼為基礎)||||√||

 若要繪製 UML 圖表與分層圖，您必須建立模型專案，作為現有方案或新方案的一部分。 這些圖表必須在模型專案中建立。 UML 圖表上的項目是一般模型的一部分，而此 UML 圖表是該模型的檢視。 分層圖上的項目位於模型專案中，但不會儲存在一般模型中。 由程式碼建立的 Code Map 與 .NET 類別圖表則位在模型專案之外。

 請參閱：

- [建立 UML 模型專案和圖表](../modeling/create-uml-modeling-projects-and-diagrams.md)

- [從程式碼建立分層圖](../modeling/create-layer-diagrams-from-your-code.md)

- [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)

- [如何：將類別圖表新增至專案 (類別設計工具)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

- [Modeling SDK for Visual Studio - 特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

  若要顯示架構的替代檢視，您可以在多個或不同圖表上重複使用相同模型中的特定項目。 例如，您可將元件拖曳到另一個元件圖表或順序圖表，使得此元件可作為執行者。 請參閱[編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)。

  雙方小組也會使用圖層驗證，以確定開發中的程式碼與設計保持一致。

  請參閱：

- [讓程式碼與設計保持一致](#ValidatingCode)

- [描述邏輯架構：分層圖](#DescribeLayers)

- [使用分層圖驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)

  > [!NOTE]
  > 某些版本的 Visual Studio 支援圖層驗證以及用於視覺化與模型化之 Code Map 及 UML 圖表的唯讀版本。 若要查看哪些版本的 Visual Studio 支援此功能，請參閱 [Architecture and Modeling Tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="UnderstandingCommunicating"></a> 了解並傳達系統的相關資訊
 Visual Studio 模型圖表並沒有規定使用順序，所以您可以依需求或方法來加以使用。 小組在整個專案進行期間，通常會頻繁地反覆重新審視其模型。 每個圖表都具有特定優勢，可協助您了解、描述及溝通開發中系統的不同層面。

 Dinner Now 及 Lucerne 在彼此溝通以及與專案關係人溝通時，會使用圖表作為其共同語言。 例如，Dinner Now 會使用圖表執行這些工作：

- 將現有程式碼視覺化。

- 與 Lucerne 溝通新的或已更新的使用者劇本。

- 識別出支援新的或已更新的使用者劇本所必須進行的變更。

  Lucerne 會使用圖表執行這些工作：

- 了解 Dinner Now 的商務程序。

- 了解系統的設計。

- 與 Dinner Now 溝通有關新的或已更新的使用者需求。

- 記錄對系統所做的更新。

  圖表會與 Team Foundation Server 整合，如此小組就可以更輕鬆地規劃、管理及追蹤其工作。 例如，他們會使用模型來識別測試案例及開發工作，以及評估其工作。 Lucerne 將 Team Foundation Server 工作項目連結到模型項目，以便監控進度並確保系統符合使用者的需求。 例如，他們將使用案例連結到測試案例工作項目，如此在所有測試通過時即可知道使用案例已完成。

  小組在簽入變更之前，會執行包含圖層驗證與自動化測試的組建，藉此根據測試及設計來驗證程式碼。 這樣有助於確定更新的程式碼不會與設計衝突，且不會破壞先前可運作的功能。

  請參閱：

- [瞭解系統在商務程式中的角色](#UnderstandingBPMandSystemDesign)

- [描述新的或更新的使用者需求](#DescribingURM)

- [從模型建立測試](#CreatingTests)

- [識別現有系統的變更](#DeterminingChanges)

- [Keeping code consistent with the design](#ValidatingCode)

- [與建立及使用模型相關的一般提示](#GeneralTips)

- [計劃與追蹤工作](#PlanningTracking)

- [在經過更新的程式碼中進行測試、驗證及檢查](#TestValidateCheckInCode)

### <a name="UnderstandingBPMandSystemDesign"></a>瞭解系統在商務程式中的角色
 Lucerne 想要深入了解 Dinner Now 的商務程序。 他們建立下列圖表，藉此更輕易地釐清其對於 Dinner Now 的了解：

|**圖表**|**描述**|
|-----------------|-------------------|
|*使用案例圖表（UML）*<br /><br /> 請參閱：<br /><br /> -   [UML 使用案例圖：參考](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML 使用案例圖：方針](../modeling/uml-use-case-diagrams-guidelines.md)|-晚餐現在系統支援的活動<br />-執行活動的人員和外部系統<br />-支援每項活動之系統的主要元件<br />-在目前系統範圍外的商務程式部分，例如食物傳遞|
|*活動圖表（UML）*<br /><br /> 請參閱：<br /><br /> -   [UML 活動圖：參考](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML 活動圖：方針](../modeling/uml-activity-diagrams-guidelines.md)|客戶建立訂單時會發生的步驟流程|
|*類別圖表（UML）*<br /><br /> 請參閱：<br /><br /> -   [UML 類別圖：參考](../modeling/uml-class-diagrams-reference.md)<br />-   [UML 類別圖：方針](../modeling/uml-class-diagrams-guidelines.md)|商務實體以及這些實體間的討論及關聯性所用的詞彙。 例如，「訂單」及「菜單項目」屬於本情節所用的詞彙。|

 例如，Lucerne 會建立下列使用案例圖表，以了解 Dinner Now 網站上所執行的工作，以及執行工作的人員：

 ![UML 使用案例圖表](../modeling/media/uml-usecase.png "UML_UseCase")

 **UML 使用案例圖表**

 下列活動圖表描述客戶在 Dinner Now 網站建立訂單時的步驟流程。 在此版本中，註解項目會識別角色，而線條會建立 *「泳道」* (Swimlane)，其會依角色來組織步驟：

 ![UML 活動圖](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")

 **UML 活動圖**

 下列類別圖表描述參與訂單流程的實體：

 ![UML 類別圖表](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")

 **UML 類別圖表**

### <a name="DescribingURM"></a>描述新的或更新的使用者需求
 Lucerne 想要在 Dinner Now 系統中加入功能，讓客戶可以閱讀及張貼對餐廳的評論。 他們會更新下列圖表，以便與 Dinner Now 描述及討論這個新需求。

|**圖表**|**描述**|
|-----------------|-------------------|
|*使用案例圖表（UML）*<br /><br /> 請參閱：<br /><br /> -   [UML 使用案例圖：參考](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML 使用案例圖：方針](../modeling/uml-use-case-diagrams-guidelines.md)|用於「撰寫餐廳評論」的新使用案例|
|*活動圖表（UML）*<br /><br /> 請參閱：<br /><br /> -   [UML 活動圖：參考](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML 活動圖：方針](../modeling/uml-activity-diagrams-guidelines.md)|客戶想要撰寫餐廳評論時會發生的步驟|
|*類別圖表（UML）*<br /><br /> 請參閱：<br /><br /> -   [UML 類別圖：參考](../modeling/uml-class-diagrams-reference.md)<br />-   [UML 類別圖：方針](../modeling/uml-class-diagrams-guidelines.md)|必須要有這些資料才能儲存評論。|

 例如，下列使用案例圖表包含新的「撰寫評論」使用案例，用以代表新的需求。 在圖表上會以橙色醒目提示，藉此便於辨識：

 ![UML 使用案例圖表](../modeling/media/uml-writerev.png "UML_WriteRev")

 **UML 使用案例圖**

 下列活動圖表包含新項目 (以橙色表示) 以描述新使用案例中的步驟流程：

 ![UML 活動圖](../modeling/media/uml-writereview.png "UML_WriteReview")

 **UML 活動圖表**

 下列類別圖表包含新的評論類別，以及其與其他類別的關聯性，如此小組可以討論其詳細內容。 請注意，客戶及餐聽可以有多個評論：

 ![UML 類別圖表](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")

 **UML 類別圖表**

### <a name="CreatingTests"></a>從模型建立測試
 雙方小組同意在進行任何變更前，必需針對系統及其元件執行一組完整的測試。 Lucerne 有專門小組在執行系統及元件層級的測試。 他們重複使用 Dinner Now 所建立的測試，並使用 UML 圖表來組織這些測試：

- 每個使用案例皆由一或多個測試代表。 使用案例圖表上的項目會連結到 Team Foundation Server 中的「測試案例」工作項目。

- 活動圖表或系統層級順序圖表上的每個流程至少皆會連結到一項測試。 測試小組以有系統的方式確定其會測試到整個活動圖表的每個可能路徑。

- 用來描述測試的詞彙是源自使用案例、類別及活動圖表所定義的詞彙。

  當需求變更且圖表經更新以反映這些變更時，測試也會隨之更新。 所有測試皆通過時才會視為滿足需求。 當情況允許時，在實作開始前會根據 UML 圖表定義測試。

  請參閱：

- [透過模型開發測試](../modeling/develop-tests-from-a-model.md)

- [驗證 UML 模型](../modeling/validate-your-uml-model.md)

### <a name="DeterminingChanges"></a> Identifying Changes to the Existing System
 Dinner Now 必須評估符合新需求所需的成本。 這有一部分取決於此變更對系統其他部分會造成多大的影響。 為協助他們了解，Dinner Now 的其中一位開發人員從現有程式碼建立下列地圖和圖表：

|**地圖或圖表**|**顯示**|
|------------------------|---------------|
|*Code Map*<br /><br /> 請參閱：<br /><br /> -   [對應方案之間的](../modeling/map-dependencies-across-your-solutions.md)相依性<br />-   [流覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)<br />-   藉[由編輯 DGML 檔案自訂 code map](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|程式碼中的相依性及其他關聯性<br /><br /> 例如，Dinner Now 可能一開始會檢閱組件 Code Map，以取得組件及其相依性的概觀。 他們可以深入研究此地圖，以探索這些組件中的命名空間及類別。<br /><br /> Dinner Now 也可以建立地圖，以探索程式碼中的特定區域及其他種類的關聯性。 他們可以使用 [方案總管] 來尋找並選取其感興趣的區域及關聯性。|
|*以程式碼為基礎的類別圖表*<br /><br /> 請參閱[如何：將類別圖加入專案 (類別設計工具)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)。|程式碼中的現有類別|

 例如，開發人員建立了 Code Map。 接著調整其範圍以便將焦點放在新情節會影響的區域。 這些區域在地圖上會處於選取及醒目提示的狀態：

 ![命名空間相依性圖形](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")

 **命名空間 Code Map**

 開發人員展開選取的命名空間以查看其類別、方法及關聯性：

 ![展開的命名空間相依性圖形](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")

 **展開的命名空間 Code Map，包含可見的跨群組連結**

 開發人員檢查程式碼以找出受影響的類別及方法。 若要在每次變更時查看所產生的影響，請在每次變更後重新產生 Code Map。 請參閱將程式[代碼視覺化](../modeling/visualize-code.md)。

 若要描述對系統其他部分 (例如元件或互動) 所造成的變更，小組可能會在白板上繪製這些項目。 他們也可能會在 Visual Studio 中繪製下列圖表，如此雙方小組皆可擷取、管理及了解詳細資料。

|**圖表**|**描述**|
|------------------|-------------------|
|*活動圖表（UML）*<br /><br /> 請參閱：<br /><br /> -   [UML 活動圖：參考](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML 活動圖：方針](../modeling/uml-activity-diagrams-guidelines.md)|當系統注意到客戶向某餐廳再次下訂單時所產生的步驟流程，系統會提示客戶撰寫評論。|
|*類別圖表（UML）*<br /><br /> 請參閱：<br /><br /> -   [UML 類別圖：參考](../modeling/uml-class-diagrams-reference.md)<br />-   [UML 類別圖：方針](../modeling/uml-class-diagrams-guidelines.md)|邏輯類別及其關聯性。 例如，系統會加入新類別以便描述 [評論] 以及其與其他實體 (例如 [餐廳]、[菜單] 及 [客戶]) 的關聯性。<br /><br /> 若要將評論與客戶相關聯，系統必須儲存客戶詳細資料。 UML 類別圖表可協助釐清這些詳細資料。|
|*以程式碼為基礎的類別圖表*<br /><br /> 請參閱[如何：將類別圖加入專案 (類別設計工具)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)。|程式碼中的現有類別。|
|*元件圖表（UML）*<br /><br /> 請參閱：<br /><br /> -   [UML 元件圖：參考](../modeling/uml-component-diagrams-reference.md)<br />-   [UML 元件圖：方針](../modeling/uml-component-diagrams-guidelines.md)|系統的高階組成部分，例如 Dinner Now 網站及其介面。 這些介面可定義元件如何透過其所提供及使用的方法或服務，與其他元件互動。|
|*順序圖表（UML）*<br /><br /> 請參閱：<br /><br /> -   [UML 順序圖表：參考](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML 順序圖表：方針](../modeling/uml-sequence-diagrams-guidelines.md)|執行個體間互動的順序。|

 例如，下列元件圖表顯示屬於 Dinner Now 網站元件的新元件。 ReviewProcessing 元件會處理用來建立評論的功能，而此元件以橙色醒目提示。

 ![UML 元件圖表](../modeling/media/uml-internal.png "UML_Internal")

 **UML 元件圖表**

 下列順序圖表顯示當 Dinner Now 網站檢查客戶是否曾向餐廳訂過餐時，會發生的互動順序。 如果曾訂過餐，系統即會要求客戶建立評論，然後將評論傳送到餐廳並在網站上公佈。

 ![UML 順序圖表](../modeling/media/uml-revsystem.png "UML_RevSystem")

 **UML 順序圖表**

### <a name="ValidatingCode"></a> 讓程式碼與設計保持一致
 Dinner Now 必須確定已更新的程式碼與設計保持一致。 他們建立會描述系統功能圖層的分層圖、指定圖層間的允許相依性，以及建立方案成品與這些圖層之間的關聯。

|**圖表**|**描述**|
|-----------------|-------------------|
|*分層圖*<br /><br /> 請參閱：<br /><br /> -   [從您的程式碼建立分層圖](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [分層圖：參考](../modeling/layer-diagrams-reference.md)<br />-   [分層圖：方針](../modeling/layer-diagrams-guidelines.md)<br />-   [使用圖層圖表驗證程式代碼](../modeling/validate-code-with-layer-diagrams.md)|程式碼的邏輯架構。<br /><br /> 分層圖會組織 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 方案中的成品並將其對應到稱為 *「圖層」* (Layer) 的抽象群組。 這些圖層可識別這些成品在系統中執行的角色、工作或功能。<br /><br /> 分層圖有助於說明系統的預定設計，以及根據該設計來驗證不斷演變的程式碼。<br /><br /> 若要建立圖層，請從 [方案總管]、[Code Map]、[類別檢視] 以及 [物件瀏覽器] 拖曳項目。 若要繪製新圖層，請使用工具箱或以滑鼠右鍵按一下圖表介面。<br /><br /> 若要檢視現有相依性，請以滑鼠右鍵按一下分層圖介面，然後按一下 [產生相依性]。 若要指定預定的相依性，請繪製新相依性。|

 例如，下列分層圖會描述圖層間的相依性，以及與每個圖層相關聯的成品數目。

 ![整合式付款系統的分層圖](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **分層圖**

 為了確保在程式碼開發期間不會發生與設計衝突的狀況，小組會針對在 Team Foundation Build 上執行的組建使用圖層驗證。 他們也會建立自訂的 MSBuild 工作，在簽入作業中要求圖層驗證。 他們會使用組建報告來收集驗證錯誤。

 請參閱：

- [定義建置流程](https://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)

- [使用閘道簽入建置流程來驗證變更](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)

- [自訂建置流程範本](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

### <a name="GeneralTips"></a> General Tips for Creating and Using Models

- 大部分的圖表是由以線條連結之節點所組成。 針對每個圖表類型，工具箱會提供不同種類的節點及線條。

   若要開啟工具箱，請在 [檢視] 功能表上按一下 [工具箱]。

- 若要建立節點，請將其從工具箱拖曳到圖表。 特定種類的節點必須拖曳到現有節點上。 例如，在元件圖表上，必須將新連接埠加入現有元件中。

- 若要建立線條或是連接，請在工具箱中依序按一下適當的工具、來源節點以及目標節點。 某些線條只能在特定種類的節點之間建立。 當您將指標移到可能的來源或目標上，指標就會指出您是否可以建立連接。

- 當您在 UML 圖表上建立項目時，同時也會將這些項目加入一般模型中。 模型專案中的 UML 圖表為該模型的檢視。 分層圖上的項目雖然不會儲存在一般模型中，但仍屬於模型專案的一部分。

   若要查看模型，請在 [架構] 功能表中指向 [視窗]，然後按一下 [UML 模型總管]。

- 在某些情況下，您可以從 [UML 模型總管] 將特定項目拖曳到 UML 圖表。 相同模型中的某些項目可以用在多個或不同的圖表，以顯示架構的替代檢視。 例如，您可將元件拖曳到另一個元件圖表或順序圖表中作為執行者。

- Visual Studio 支援 UML 2.1.2。 本概觀僅描述此版本 UML 圖表的主要功能，但有許多書籍會詳細討論 UML 及其用法。

  請參閱[為您的應用程式建立模型](../modeling/create-models-for-your-app.md)。

### <a name="PlanningTracking"></a> Planning and Tracking Work
 Visual Studio 模型圖表已經與 Team Foundation Server 整合，以便您可以更輕鬆地計畫、管理及追蹤工作。 兩個小組都使用模型來識別測試案例及開發工作，以及評估其工作。 Lucerne 建立 Team Foundation Server 工作項目並將其連結到模型項目，例如使用案例或元件。 這樣可協助他們監視進度及針對使用者需求追蹤工作。 也可協助他們確定所做的變更能持續符合這些需求。

 當工作進行時，小組會更新工作項目以反映實際花在工作上的時間。 他們也會使用下列 Team Foundation Server 功能來監視及報告工作狀態：

- 每日 *「待執行工作報表」* (Burndown Report)，此報表會顯示他們是否會在預定時間內完成計劃的工作。 他們會從 Team Foundation Server 產生其他類似的報表來追蹤 Bug 進度。

- *「反覆項目工作表」* (Iteration Worksheet)，此工作表使用 Microsoft Excel 協助小組監視及平衡小組成員間的工作量。 此工作表連結到 Team Foundation Server，並在定期進度會議中提供討論重點。

- *「開發儀表板」* (Development Dashboard)，此儀表板使用 Office Project 讓小組隨時獲知重要的專案資訊。

  請參閱：

- [使用 Visual Studio Team Services 或 Team Foundation Server 來追蹤工作](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)

- [連結模型項目和工作項目](../modeling/link-model-elements-and-work-items.md)

- [Visual Studio ALM 的圖表、儀表板和報表](https://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)

- [使用 Project 建立您的待處理項目和工作](https://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)

### <a name="TestValidateCheckInCode"></a> 在程式碼中進行測試、驗證及檢查
 當小組完成每項工作時，他們會將程式碼簽入至 Team Foundation 版本控制，如果忘了這麼做，則會收到 Team Foundation Server 的提醒。 在 Team Foundation Server 接受簽入之前，小組會執行單元測試及圖層驗證，針對測試案例及設計來驗證程式碼。 他們使用 Team Foundation Server 定期執行組建、自動化單元測試及圖層驗證。 此行為有助於確定程式碼符合下列準則：

- 這麼做確實有成效。

- 不會破壞先前運作的程式碼。

- 不會與設計衝突。

  Dinner Now 擁有大型自動化測試集合，因為這些測試幾乎仍適用，所以 Lucerne 可重複使用。 Lucerne 也可以根據這些測試進行建置，並加入新測試以涵蓋新功能。 同時也會使用 Visual Studio 執行手動測試。

  為確定程式碼符合設計，小組在 Team Foundation Build 中設定其組建以包含圖層驗證。 如果發生任何衝突，則會產生包含詳細資料的報表。

  請參閱：

- [測試應用程式](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)

- [在開發期間驗證您的系統](../modeling/validate-your-system-during-development.md)

- [使用版本控制](https://go.microsoft.com/fwlink/?LinkID=525605)

- [建置應用程式](/azure/devops/pipelines/index)

## <a name="UpdatingSystem"></a> Updating the System Using Visualization and Modeling
 Lucerne 及 Dinner Now 必須整合其付款系統。 下列各節將示範 Visual Studio 中的模型圖表如何協助其執行這項工作：

- [瞭解使用者需求：使用案例圖](#UnderstandUseCases)

- [瞭解商務程式：活動圖](#UnderstandActivities)

- [描述系統結構：元件圖](#DescribeComponents)

- [描述互動：順序圖表](#DescribeSequence)

- [將現有程式碼視覺化：Code Map](#VisualizeCode)

- [定義類型的詞彙：類別圖表](#DefineClasses)

- [描述邏輯架構：分層圖](#DescribeLayers)

  請參閱：

- [建立應用程式模型](../modeling/create-models-for-your-app.md)

- [視覺化程式碼](../modeling/visualize-code.md)

- [在開發程序中使用模型](../modeling/use-models-in-your-development-process.md)

- [模型使用者需求](../modeling/model-user-requirements.md)

- [建立應用程式架構的模型](../modeling/model-your-app-s-architecture.md)

### <a name="UnderstandUseCases"></a>瞭解使用者需求：使用案例圖
 使用案例圖表會摘要說明系統支援的活動，以及執行這些活動的人員。 Lucerne 藉助使用案例圖表來了解 Dinner Now 系統的下列項目：

- 客戶建立訂單。

- 餐廳接收訂單。

- 外部付款處理器閘道 (Dinner Now 付款系統用其來驗證付款) 不在網站範圍內。

  圖表也會顯示某些主要使用案例如何分成較小的使用案例。 Lucerne 想要使用自己的付款系統。 他們以不同顏色將「處理付款」使用案例醒目提示，以表示此使用案例需要變更：

  ![在使用案例圖上反白顯示進程付款](../modeling/media/uml-processpay.png "UML_ProcessPay")

  **在使用案例圖上反白顯示進程付款**

  如果開發時間較短，小組可能會討論是否要讓客戶直接付款給餐廳。 若要顯示此做法，他們會將「處理付款」使用案例更換成在 Dinner Now 系統界限之外的使用案例。 接著會將「客戶」直接連結到「餐廳」，表示 Dinner Now 只會處理訂單：

  ![Rescoping 使用案例圖上的付款餐廳](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")

  **Rescoping 使用案例圖上的付款餐廳**

  請參閱：

- [UML 使用案例圖：參考](../modeling/uml-use-case-diagrams-reference.md)

- [UML 使用案例圖：方針](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="drawing-a-use-case-diagram"></a>繪製使用案例圖表
 使用案例圖表具有下列主要功能：

- *「執行者」* (Actor) 代表人員、組織、機器或軟體系統所扮演的角色。 例如「客戶」、「餐廳」及「Dinner Now 付款系統」為執行者。

- *「使用案例」* (Use Case) 代表執行者與開發中系統之間的互動。  其可代表任何規模的互動，舉凡單一滑鼠點選或訊息，或是延續多天的交易皆可。

- *「關聯」* (Association) 可將執行者連結到使用案例。

- 大型使用案例可以 *「包含」* (Include) 小型使用案例，例如「建立訂單」包含「選取餐廳」。 您可以 *「擴充」* (Extend) 使用案例，將目標及步驟加入擴充的使用案例，以表示使用案例只有在特定條件下才會發生。 使用案例也可以彼此繼承。

- *「子系統」* (Subsystem) 代表開發中的軟體系統或其中的一個元件。 其是包含使用案例的大型方塊。 使用案例圖表會釐清哪些使用案例位在子系統界限之內或之外。 若要表示使用者必須以其他方式完成特定目標，請在子系統界限之外繪製使用案例。

- *「成品」* (Artifact) 可將圖表上的項目連結到其他圖表或文件。

  請參閱：

- [UML 使用案例圖：參考](../modeling/uml-use-case-diagrams-reference.md)

- [UML 使用案例圖：方針](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="summary-strengths-of-use-case-diagrams"></a>摘要：使用案例圖表的優勢
 使用案例圖表可協助您將下列項目視覺化：

- 系統所支援或不支援的活動。

- 執行這些活動的人員與外部系統。

- 支援每項活動之系統的主要元件，您可將其表示為在父系統內部巢狀化的子系統。

- 使用案例如何分成較小的使用案例或變化。

#### <a name="relationship-to-other-diagrams"></a>與其他圖表的關聯性

|**圖表**|**描述**|
|-----------------|-------------------|
|活動圖|使用案例中的步驟流程，以及在該使用案例中執行這些步驟的人員。<br /><br /> 使用案例名稱通常會反映活動圖表中的步驟。 活動圖表支援像是決策、合併、輸入與輸出、並行的流程等項目。<br /><br /> 請參閱：<br /><br /> -   [UML 活動圖：參考](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML 活動圖：方針](../modeling/uml-activity-diagrams-guidelines.md)|
|順序圖表|使用案例參與者之間的互動順序。<br /><br /> 請參閱：<br /><br /> -   [UML 順序圖表：參考](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML 順序圖表：方針](../modeling/uml-sequence-diagrams-guidelines.md)|
|類別圖表 (UML)|參與使用案例的實體或類型。<br /><br /> 請參閱：<br /><br /> -   [UML 類別圖：參考](../modeling/uml-class-diagrams-reference.md)<br />-   [UML 類別圖：方針](../modeling/uml-class-diagrams-guidelines.md)|

### <a name="UnderstandActivities"></a>瞭解商務程式：活動圖
 活動圖表描述商務程序中的步驟流程，並提供簡單的方式來溝通工作流程。 開發專案可以有多個活動圖表。 活動通常包含一個外部動作產生的所有動作，例如訂餐、更新菜單或將新餐廳加入營業。 活動也可能會描述複雜動作的詳細資料。

 Lucerne 更新下列活動圖表以顯示 Lucerne 會處理付款並支付給餐廳。 他們將 Dinner Now 付款系統更換成 Lucerne 付款系統，如下醒目提示：

 ![活動圖表上的 Lucerne 付款系統](../modeling/media/uml-lucerne.png "UML_Lucerne")

 **取代活動圖表上的「立即晚餐」付款系統**

 已更新的圖表可協助 Lucerne 及 Dinner Now 將Lucerne 付款系統於商務程序所在之處視覺化。 在此版本中，註解會用來識別執行步驟的角色。 線條會用來建立 *「泳道」* (Swimlane)，其會依角色來組織步驟。

 小組也可能需要討論替代的劇本，即客戶改為在訂單抵達後付款給餐廳的情況。 這樣會針對軟體系統建立不同的需求。

 Dinner Now 先前是在白板或 PowerPoint 中繪製這些圖表。 現在他們也使用 Visual Studio 繪製這些圖表，如此雙方小組皆可擷取、了解及管理詳細資料。

 請參閱：

- [UML 活動圖：參考](../modeling/uml-activity-diagrams-reference.md)

- [UML 活動圖：方針](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="drawing-an-activity-diagram"></a>繪製活動圖表
 活動圖表具有下列主要功能：

- *「初始節點」* (Initial Node)，表示活動的第一個動作。

   圖表一律要有其中一個這類節點。

- *「動作」* (Action)，描述使用者或軟體會在其中執行工作的步驟。

- *「控制流程」* (Control Flow)，顯示動作之間的流程。

- *「決策節點」* (Decision Node)，代表流程中的條件分支。

- *「分岔節點」* (Fork Node)，將單一流程分成並行的流程。

- *「活動的最後節點」* (Activity Final Node)，顯示活動的終點。

   雖然這些節點為選擇性，但是將其加入圖表會很有用，藉此可顯示活動在何處結束。

  請參閱：

- [UML 活動圖：參考](../modeling/uml-activity-diagrams-reference.md)

- [UML 活動圖：方針](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="summary-strengths-of-activity-diagrams"></a>摘要：活動圖表的優勢
 活動圖表可協助您描述商務、系統或程式之動作間的控制流程及資訊，並將其視覺化。 在與他人溝通描述工作流程時，這方式相當簡單實用。

#### <a name="relationship-to-other-diagrams"></a>與其他圖表的關聯性

|**圖表**|**說明**|
|-----------------|---------------------|
|使用案例圖|摘要說明各個執行者所執行的活動。<br /><br /> 請參閱：<br /><br /> -   [UML 使用案例圖：參考](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML 使用案例圖：方針](../modeling/uml-use-case-diagrams-guidelines.md)|
|元件圖|將系統視覺化為可重覆使用的組件集合，該組件透過一組妥善定義的介面來提供或使用行為。<br /><br /> 請參閱：<br /><br /> -   [UML 元件圖：參考](../modeling/uml-component-diagrams-reference.md)<br />-   [UML 元件圖：方針](../modeling/uml-component-diagrams-guidelines.md)|

### <a name="DescribeComponents"></a>描述系統結構：元件圖
 元件圖表將系統描述為可分隔的組件集合，該組件透過一組妥善定義的介面來提供或使用行為。 這些組件可以是任何規模，且可以採用任何方式進行連接。

 為協助 Lucerne 與 Dinner Now 討論系統的元件及其介面，並將其視覺化，他們建立了下列元件圖表：

 ![付款系統中的外部元件](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")

 **晚餐現已付款系統的元件**

 此圖表顯示不同的元件類型及其 *「相依性」* (Dependency)。 例如，Dinner Now 網站與 Lucerne 付款系統皆需要「外部付款處理器閘道」來驗證付款。 元件之間的箭號代表相依性，表示哪些元件需要其他元件的功能。

 為使用 Lucerne 付款系統，Dinner Now 網站必須更新以使用 Lucerne 付款系統的 PaymentApproval 及 PayableInsertion 介面。

 下列圖表顯示 Dinner Now 網站的特定元件設定。 此設定表示網站的任一執行個體是由四個 *「組件」* (Part) 所組成：

- CustomerProcessing

- OrderProcessing

- ReviewProcessing

- PaymentProcessing

  這些組件是指定之元件類型的執行個體，會以下列方式連接：

  ![晚餐中的元件 Now 網站](../modeling/media/uml-dinnernow.png "UML_DinnerNow")

  **晚餐 Now 網站內的元件**

  Dinner Now 網站將其行為委派給這些組件，而這些組件會處理網站的功能。 父元件及其成員元件間的箭號會顯示 *「委派」* (Delegation)，其表示哪些組件會處理父元件透過其介面接收或傳遞的訊息。

  在此設定中，PaymentProcessing 元件會處理客戶付款作業。 因此必須更新這個元件，藉此與 Lucerne 付款系統整合。 在其他案例中，相同父元件內可能存在同一元件類型的多個執行個體。

  請參閱：

- [UML 元件圖表：參考](../modeling/uml-component-diagrams-reference.md)

- [UML 元件圖：方針](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="drawing-a-component-diagram"></a>繪製元件圖表
 元件圖表具有下列主要功能：

- *「元件」* (Component)，代表系統功能可加以分隔的片段。

- *「提供的介面連接埠」* (Provided Interface Port)，代表由元件實作的訊息或呼叫群組，並由其他元件或外部系統使用。

- *「需要的介面連接埠」* (Required Interface Port)，代表訊息或呼叫群組，元件會將其傳送給其他元件或外部系統。 此類連接埠會描述元件預期其他元件或外部系統至少會使用的作業。

- *「組件」* (Part) 是元件的成員，且通常是其他元件的執行個體。 組件是父元件內部設計的片段。

- *「相依性」* (Dependency)，表示元件需要其他元件的功能。

- *「委派」* (Delegation)，表示元件的組件會處理父元件所傳送或接收的訊息。

  請參閱：

- [UML 元件圖表：參考](../modeling/uml-component-diagrams-reference.md)

- [UML 元件圖：方針](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="summary-strengths-of-component-diagrams"></a>摘要：元件圖表的優勢
 元件圖表可協助您將下列項目視覺化：

- 以一組可分隔組件來表示的系統，不論其實作語言或樣式為何。

- 具有妥善定義之介面的元件，在需求變更時讓設計更易於了解及進行更新。

#### <a name="relationship-to-other-diagrams"></a>與其他圖表的關聯性

|**圖表**|**說明**|
|-----------------|---------------------|
|Code Map|將現有程式碼中的組織與關聯性視覺化。<br /><br /> 若要識別候選元件，請建立 Code Map，並在系統中依功能將項目分組。<br /><br /> 請參閱：<br /><br /> -   [對應方案之間的](../modeling/map-dependencies-across-your-solutions.md)相依性|
|順序圖表|將元件或元件內部組件間的互動順序視覺化。<br /><br /> 若要在順序圖表上從元件建立生命線，請以滑鼠右鍵按一下元件，然後按一下 [建立生命線]。<br /><br /> 請參閱：<br /><br /> -   [UML 順序圖表：參考](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML 順序圖表：方針](../modeling/uml-sequence-diagrams-guidelines.md)|
|類別圖表 (UML)|定義提供的連接埠或必要的連接埠上的介面，以及定義實作元件功能的類別。<br /><br /> 請參閱：<br /><br /> -   [UML 類別圖：參考](../modeling/uml-class-diagrams-reference.md)<br />-   [UML 類別圖：方針](../modeling/uml-class-diagrams-guidelines.md)|
|分層圖|描述與元件相關的系統邏輯架構。 使用圖層驗證以確定程式碼與設計維持一致。<br /><br /> 請參閱：<br /><br /> -   [從您的程式碼建立分層圖](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [分層圖：參考](../modeling/layer-diagrams-reference.md)<br />-   [分層圖：方針](../modeling/layer-diagrams-guidelines.md)<br />-   [使用圖層圖表驗證程式代碼](../modeling/validate-code-with-layer-diagrams.md)|
|活動圖|將元件為回應傳入訊息所執行的內部處理程序視覺化。<br /><br /> 請參閱：<br /><br /> -   [UML 活動圖：參考](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML 活動圖：方針](../modeling/uml-activity-diagrams-guidelines.md)|

### <a name="VisualizeCode"></a> 將現有程式碼視覺化：Code Map
 Code Map 顯示程式碼的目前組織及關聯性。 項目在地圖上是以 *「節點」* (Node) 來代表，關聯性則是以 *「連結」* (Link) 來代表。 Code Map 可協助您執行下列種類的工作：

- 探索不熟悉的程式碼。

- 了解提議的變更可能會影響現有程式碼的哪些部分以及影響的方式。

- 尋找複雜度、自然圖層或模式的區域，或是可能因改善而受惠的其他區域。

  例如，Dinner Now 必須評估更新 PaymentProcessing 元件所需的成本。 這有一部分取決於此變更對系統其他部分會造成多大的影響。 為協助他們了解，Dinner Now 開發人員從程式碼產生 Code Map，並將範圍焦點調整在可能受變更影響的區域：

  下列地圖顯示 PaymentProcessing 類別及 Dinner Now 系統其他部分之間的相依性，其以選取狀態顯示：

  ![晚餐現在付款系統的相依性圖形](../modeling/media/dep-dnpayment.png "Dep_DNPayment")

  **Dinner Now 付款系統的 Code Map**

  開發人員展開 PaymentProcessing 類別並選取其成員以探索地圖，進而查看可能受影響的區域。

  ![PaymentProcessing 和相依性中的方法](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")

  **PaymentProcessing 類別內部方法及其相依性**

  他們針對 Lucerne 付款系統產生下列地圖以查看其類別、方法與相依性。 小組發現 Lucerne 系統可能也需要處理，以與 Dinner Now 系統其他部分互動：

  ![Lucerne 付款系統的相依性圖形](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")

  **Lucerne 付款系統的 Code Map**

  雙方小組一塊合作，判斷整合雙方系統所需進行的變更。 他們決定重構部分程式碼，以方便進行更新。 PaymentApprover 類別將移到 DinnerNow.Business 命名空間，且需要一些新方法。 處理交易的 Dinner Now 類別將擁有自己的命名空間。 小組建立並使用工作項目以規劃、組織及追蹤工作。 他們將工作項目連結到對模型項目有用之處。

  在重新組織程式碼之後，小組產生新的 Code Map 來查看已更新的結構及關聯性：

  ![具有重新組織程式碼的相依性圖形](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")

  **程式碼已重新組織過的 Code Map**

  此地圖顯示 PaymentApprover 類別目前已位於 DinnerNow.Business 命名空間中，且具有一些新方法。 Dinner Now 交易類別現在已擁有自己的 PaymentSystem 命名空間，之後處理該程式碼會變得更容易。

#### <a name="creating-a-code-map"></a>建立 Code Map

- 如需快速取得原始程式碼的概觀，請遵循這些步驟來產生 Code Map：

     在 [架構] 功能表上，按一下 [產生方案的 Code Map]。

     若要快速取得已編譯程式碼的概觀，請建立空白的 Code Map，然後將組件檔或二進位檔拖曳到地圖介面上。

- 若要探索特定程式碼或方案項目，請使用 [方案總管] 來選取想要視覺化的項目及關聯性。 然後您可以產生新地圖，或將所選項目加入現有地圖中。 請參閱[對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)。

- 為了協助您探索地圖，請重新整理配置，以便其符合您要執行的工作種類。

     例如，若要將程式碼的圖層視覺化，請選取樹狀配置。 請參閱[流覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)。

#### <a name="summary-strengths-of-code-maps"></a>摘要：Code Map 的優勢
 Code Map 可協助您：

- 深入了解現有程式碼的組織及關聯性。

- 識別所提議的變更可能影響的區域。

- 尋找複雜度、模式、圖層的區域，或可加以改善而讓程式碼更易於維護、變更及重複使用的其他區域。

#### <a name="relationship-to-other-diagrams"></a>與其他圖表的關聯性

|**圖表**|**描述**|
|-----------------|-------------------|
|分層圖|系統的邏輯架構。 使用圖層驗證以確定程式碼與設計維持一致。<br /><br /> 若要易於識別現有圖層或預定圖層，請建立 Code Map 並將相關項目分組。 若要建立分層圖，請參閱：<br /><br /> -   [從您的程式碼建立分層圖](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [分層圖：方針](../modeling/layer-diagrams-guidelines.md)|
|元件圖|元件、其介面及關聯性。<br /><br /> 為了協助您識別元件，請建立 Code Map，並在系統中依功能將項目分組。<br /><br /> 請參閱：<br /><br /> -   [UML 元件圖：參考](../modeling/uml-component-diagrams-reference.md)<br />-   [UML 元件圖：方針](../modeling/uml-component-diagrams-guidelines.md)|
|類別圖表 (UML)|類別、其屬性與作業及關聯性。<br /><br /> 為了協助您識別這些項目，請建立會顯示這些項目的 UML 類別圖表。<br /><br /> 請參閱：<br /><br /> -   [UML 類別圖：參考](../modeling/uml-class-diagrams-reference.md)<br />-   [UML 類別圖：方針](../modeling/uml-class-diagrams-guidelines.md)|
|類別圖表 (以程式碼為基礎)|特定專案程式碼中的現有類別。<br /><br /> 若要修改程式碼中的現有類別並將其視覺化，請使用 [類別設計工具]。<br /><br /> 請參閱[如何：將類別圖加入專案 (類別設計工具)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)。|

### <a name="DescribeSequence"></a>描述互動：順序圖表
 順序圖表描述系統組成部分之間的一系列互動。 組成部分可以是任何規模。 例如，其範圍可小至程式的個別物件，或大至大型子系統或外部執行者。 互動可以是任何規模及類型。 例如，其範圍可小至個別訊息或大至擴充的異動，而且可做為函式呼叫或 Web 服務訊息。

 為協助 Lucerne 與 Dinner Now 描述及討論「處理付款」使用案例中的步驟，其從元件圖表建立下列順序圖表。 生命線反映 Dinner Now 網站元件及其組件。 出現在生命線之間的訊息會遵循元件圖表上的連接。

 ![進程付款使用案例的順序圖表](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")

 **處理付款使用案例的順序圖表**

 順序圖表顯示在客戶建立訂單時，Dinner Now 網站會在 OrderProcessing 執行個體上呼叫 ProcessOrder。 接著，OrderProcessing 會在 PaymentProcessing 上呼叫 ProcessPayment。 這項作業會一直持續直到「外部付款處理器閘道」驗證付款。 唯有如此，控制權才會回到 Dinner Now 網站。

 Lucerne 必須評估為了與 Dinner Now 系統整合而更新付款系統所需的成本。 為協助他們了解，他們或許可以建立 Code Map，以便將受影響的程式碼視覺化。

 請參閱：

- [UML 循序圖：參考](../modeling/uml-sequence-diagrams-reference.md)

- [UML 循序圖：方針](../modeling/uml-sequence-diagrams-guidelines.md)

- [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)

#### <a name="drawing-a-sequence-diagram"></a>繪製順序圖表
 順序圖表具有下列主要功能：

- 垂直 *「生命線」* (Lifeline) 代表執行者或軟體物件的執行個體。

   若要加入執行者符號 (表示參與者位在開發中系統之外)，請按一下生命線。 在 [屬性] 視窗中，將**執行者**設為 **True**。 如果 [屬性] 視窗未開啟，請按 **F4**。

- 水平 *「訊息」* (Message) 代表方法呼叫、Web 服務訊息或一些其他通訊。 *「執行出現次數」* (Execution Occurrence) 是出現在生命線上帶有垂直陰影的矩形，代表接收物件處理呼叫的期間。

- 在*同步*訊息期間，傳送者物件會等待控制項 <，\<傳回 > >，如同在一般函式呼叫中。 在 *「非同步」* (Asynchronous) 訊息期間，傳送者可立即繼續作業。

- 使用 <\<建立 > > 訊息，以指示其他物件的物件結構。 這應該是第一個傳送到物件的訊息。

  請參閱：

- [UML 循序圖：參考](../modeling/uml-sequence-diagrams-reference.md)

- [UML 循序圖：方針](../modeling/uml-sequence-diagrams-guidelines.md)

#### <a name="summary-strengths-of-sequence-diagrams"></a>摘要：順序圖表的優勢
 順序圖表可協助您將下列項目視覺化：

- 在使用案例執行期間，於執行者或物件間轉移的控制流程。

- 方法呼叫或訊息的實作。

#### <a name="relationship-to-other-diagrams"></a>與其他圖表的關聯性

|**圖表**|**說明**|
|-----------------|---------------------|
|類別圖表 (UML)|定義生命線代表的類別，以及定義參數及傳回值，而此參數及傳回值用於在生命線之間傳送的訊息中。<br /><br /> 若要從生命線建立類別，請以滑鼠右鍵按一下生命線，然後按一下 [建立類別] 或 [建立介面]。 若要在類別圖表上從類型建立生命線，請以滑鼠右鍵按一下類型，然後按一下 [建立生命線]。<br /><br /> 請參閱：<br /><br /> -   [UML 類別圖：參考](../modeling/uml-class-diagrams-reference.md)<br />-   [UML 類別圖：方針](../modeling/uml-class-diagrams-guidelines.md)|
|元件圖|描述生命線代表的元件，以及描述會提供及使用訊息代表之行為的介面。<br /><br /> 若要從元件圖表建立生命線，請以滑鼠右鍵按一下元件，然後按一下 [建立生命線]。<br /><br /> 請參閱：<br /><br /> -   [UML 元件圖：參考](../modeling/uml-component-diagrams-reference.md)<br />-   [UML 元件圖：方針](../modeling/uml-component-diagrams-guidelines.md)|
|使用案例圖|將順序圖表上使用者及元件之間的互動摘要說明為使用案例，其代表使用者的目標。<br /><br /> 請參閱：<br /><br /> -   [UML 使用案例圖：參考](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML 使用案例圖：方針](../modeling/uml-use-case-diagrams-guidelines.md)|

### <a name="DefineClasses"></a> 定義類型的詞彙：類別圖表
 類別圖表定義參與系統的實體、詞彙或概念，以及彼此的關聯性。 例如，您可以在開發期間使用這些圖表來描述每個類別的屬性及作業，不論其實作語言或樣式為何。

 為了協助 Lucerne 描述及討論參與「處理付款」使用案例的實體，他們繪製了下列類別圖表：

 ![類別圖表上的處理付款實體](../modeling/media/uml-payentities.png "UML_PayEntities")

 **類別圖表上的「處理付款」實體**

 此圖表顯示「客戶」可以有多個訂單及不同的付款方式。 BankAccount 與 CreditCard 都繼承自 Payment。

 在開發期間，Lucerne 使用下列類別圖表來描述及討論每個類別的詳細資料：

 ![類別圖表上的處理付款實體詳細資料](../modeling/media/uml-payment.png "UML_Payment")

 **類別圖表上的「處理付款」詳細資料**

 請參閱：

- [UML 類別圖表：參考](../modeling/uml-class-diagrams-reference.md)

- [UML 類別圖：方針](../modeling/uml-class-diagrams-guidelines.md)

#### <a name="drawing-a-class-diagram"></a>繪製類別圖表
 類別圖表具有下列主要功能：

- 類型，例如類別、介面及列舉：

  - *「類別」* (Class) 是物件的定義，而這些物件共用特定的結構或行為特性。

  - *「介面」* (Interface) 會定義物件外部可見行為的一部分。

  - *「列舉」* (Enumeration) 是包含常值清單的分類器。

- *「屬性」* (Attribute) 是特定類型的值，其描述 *「分類器」* (Classifier) 的每個執行個體。 分類器是類型、元件、使用案例的一般名稱，甚至是執行者的一般名稱。

- *「作業」* (Operation) 是分類器執行個體可以執行的方法或函式。

- *「關聯」* (Association) 表示兩個分類器之間的某種關聯性。

  - *「彙總」* (Aggregation) 是一種關聯，表示兩個分類器之間的共用擁有權。

  - *「組合」* (Composition) 是一種關聯，表示兩個分類器之間的整體-部分關聯性。

    若要顯示彙總或組合，請在關聯上設定 **彙總** 屬性。 **共用** 顯示彙總， **組合** 則顯示組合。

- *「相依性」* (Dependency) 表示若變更某個分類器的定義，可能會變更另一個分類器的定義。

- *「一般化」* (Generalization) 表示特定分類器的部分定義繼承自一般分類器。 *「實現」* (Realization) 表示類別實作介面提供的作業及屬性。

   若要建立這些關聯性，請使用 [繼承] 工具。 另外，實現可以用 *「棒棒糖符號」* (Lollipop) 表示。

- *「封裝」* (Package) 是分類器、關聯、生命線、元件及其他封裝的群組。 *「匯入」* (Import) 關聯性表示某個封裝包含另一個封裝的所有定義。

  您可以使用 [類別設計工具] 從程式碼建立類別圖，來開始探索及討論現有類別。

  請參閱：

- [UML 類別圖表：參考](../modeling/uml-class-diagrams-reference.md)

- [UML 類別圖：方針](../modeling/uml-class-diagrams-guidelines.md)

- [如何：將類別圖表新增至專案 (類別設計工具)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

#### <a name="summary-strengths-of-class-diagrams"></a>摘要：類別圖表的優勢
 類別圖表可協助您定義下列項目：

- 討論使用者需求及參與系統的實體時可使用的常用詞彙。 請參閱[模型使用者需求](../modeling/model-user-requirements.md)。

- 系統組成部分 (例如元件) 使用的類型，不論其實作為何。 請參閱[模型應用程式的架構](../modeling/model-your-app-s-architecture.md)。

- 類型之間的關聯性 (例如相依性)。 例如，您可以顯示某個類型可以與另一個類型的多個執行個體相關聯。

#### <a name="relationship-to-other-diagrams"></a>與其他圖表的關聯性

|**圖表**|**說明**|
|-----------------|---------------------|
|使用案例圖|定義用於描述使用案例中目標及步驟的類型。<br /><br /> 請參閱：<br /><br /> -   [UML 使用案例圖：參考](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML 使用案例圖：方針](../modeling/uml-use-case-diagrams-guidelines.md)|
|活動圖|定義會通過物件節點、輸入連接、輸出連接及活動參數節點的資料類型。<br /><br /> 請參閱：<br /><br /> -   [UML 活動圖：參考](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML 活動圖：方針](../modeling/uml-activity-diagrams-guidelines.md)|
|元件圖|描述元件、其介面及關聯性。 類別可能也會描述完整元件。<br /><br /> 請參閱：<br /><br /> -   [UML 元件圖：參考](../modeling/uml-component-diagrams-reference.md)<br />-   [UML 元件圖：方針](../modeling/uml-component-diagrams-guidelines.md)|
|分層圖|定義與類別相關的系統邏輯架構。<br /><br /> 使用圖層驗證以確定程式碼與設計維持一致。<br /><br /> 請參閱：<br /><br /> -   [從您的程式碼建立分層圖](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [分層圖：參考](../modeling/layer-diagrams-reference.md)<br />-   [分層圖：方針](../modeling/layer-diagrams-guidelines.md)<br />-   [使用圖層圖表驗證程式代碼](../modeling/validate-code-with-layer-diagrams.md)|
|順序圖表|定義生命線的類型，以及生命線可以接收之所有訊息的作業、參數及傳回值。<br /><br /> 若要在類別圖表上從類型建立生命線，請以滑鼠右鍵按一下類型，然後按一下 [建立生命線]。<br /><br /> 請參閱：<br /><br /> -   [UML 順序圖表：參考](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML 順序圖表：方針](../modeling/uml-sequence-diagrams-guidelines.md)|
|Code Map|將現有程式碼中的組織與關聯性視覺化。<br /><br /> 若要識別類別、其關聯性及方法，請建立會顯示這些項目的 Code Map。<br /><br /> 請參閱：<br /><br /> -   [對應方案之間的](../modeling/map-dependencies-across-your-solutions.md)相依性|

### <a name="DescribeLayers"></a>描述邏輯架構：分層圖
 分層圖將您方案中的成品組織成抽象群組 (也就是 *「圖層」* (Layer))，來描述系統的邏輯架構。 成品可以是多個項目，例如命名空間、專案、類別、方法等等。 圖層代表及描述成品在系統中執行的角色或工作。 您也可以在組建中加入圖層驗證並簽入作業，以確定程式碼與設計維持一致。

 為了讓程式碼與設計一致，Dinner Now 及 Lucerne 使用下列分層圖來驗證演變的程式碼：

 ![整合式付款系統的分層圖](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **晚餐的圖層圖表現在已與 Lucerne 整合**

 這個圖表上的圖層會連結到對應的 Dinner Now 及 Lucerne 方案成品。 例如，商務圖層會連結到 DinnerNow.Business 命名空間及其成員，其目前已包含 PaymentApprover 類別。 資源存取圖層會連結到 DinnerNow.Data 命名空間。 箭號 (也就是 *「相依性」* (Dependency)) 會指定只有商務圖層可以使用位於資源存取圖層中的功能。 小組在更新程式碼時，圖層驗證會定期執行，以便在發生衝突時加以攔截，並協助小組立即解決衝突。

 小組共同合作，以逐步進行整合並測試這兩個系統。 他們首先確定 PaymentApprover 與 Dinner Now 其餘部分彼此可順利運作，才會處理 PaymentProcessing。

 下列 Code Map 顯示 Dinner Now 及 PaymentApprover 之間的新呼叫：

 ![已更新整合式系統的相依性圖形](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")

 **內含已更新方法呼叫的 Code Map**

 在確定系統如預期運作之後，Dinner Now 會將 PaymentProcessing 程式碼註解化。 圖層驗證報表結果無誤，且產生的 Code Map 顯示沒有任何 PaymentProcessing 相依性存在：

 ![沒有 PaymentProcessing 的相依性圖形](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")

 **未含 PaymentProcessing 的 Code Map**

#### <a name="drawing-a-layer-diagram"></a>繪製分層圖
 分層圖具有下列主要功能：

- *「圖層」* (Layer) 描述成品的邏輯群組。

- *「連結」* (Link) 是圖層與成品之間的關聯。

   若要從成品建立圖層，請從 [方案總管]、[Code Map]、[類別檢視] 或 [物件瀏覽器] 拖曳項目。 若要繪製新圖層再連結到成品，請使用工具箱或以滑鼠右鍵按一下圖表介面以建立圖層，然後將項目拖曳到這些圖層。

   圖層上的數字會顯示圖層連結的成品數目。 這些成品可以是命名空間、專案、類別、方法等等。 當您解譯圖層上的成品數目時，請記住下列事項：

  - 如果圖層連結的成品有包含其他成品，但圖層未直接連結這些其他成品，則數字將只包含連結的成品。 然而，在圖層驗證期間會加入其他成品以進行分析。

     例如，如果圖層連結到單一命名空間，即使命名空間包含類別，連結的成品數目仍為 1。 如果圖層也有命名空間中每個類別的連結，則數字將包含這些已連結的類別。

  - 如果圖層包含已連結到成品的其他圖層，即使此容器圖層上的數字未包含那些成品，容器圖層也會連結到那些成品。

    若要查看連結到圖層的成品，請以滑鼠右鍵按一下圖層，然後按一下 [檢視連結] 來開啟 [圖層總管]。

- *「相依性」* (Dependency) 表示某個圖層可以使用另一個圖層中的功能，但反過來則不行。 *「雙向相依性」* (Bidirectional Dependency) 表示某個圖層可以使用另一個圖層中的功能，反之亦然。

   若要在分層圖上顯示現有相依性，請以滑鼠右鍵按一下圖表介面，然後按一下 [產生相依性]。 若要描述預定的相依性，請繪製新的相依性。

  請參閱：

- [從程式碼建立分層圖](../modeling/create-layer-diagrams-from-your-code.md)

- [分層圖：參考](../modeling/layer-diagrams-reference.md)

- [分層圖：方針](../modeling/layer-diagrams-guidelines.md)

- [使用分層圖驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-layer-diagrams"></a>摘要：分層圖的優勢
 分層圖可以協助您：

- 根據成品功能描述系統的邏輯架構。

- 確保開發中的程式碼符合指定的設計。

#### <a name="relationship-to-other-diagrams"></a>與其他圖表的關聯性

|**圖表**|**說明**|
|-----------------|---------------------|
|Code Map|將現有程式碼中的組織與關聯性視覺化。<br /><br /> 若要建立圖層，請產生 Code Map，然後在地圖上將項目分組為可能的圖層。 將群組從地圖拖曳到分層圖。<br /><br /> 請參閱：<br /><br /> -   [對應方案之間的](../modeling/map-dependencies-across-your-solutions.md)相依性<br />-   [流覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)|
|元件圖|描述元件、其介面及關聯性。<br /><br /> 若要將圖層視覺化，請建立會描述系統中不同元件之功能的元件圖表。<br /><br /> 請參閱：<br /><br /> -   [UML 元件圖：參考](../modeling/uml-component-diagrams-reference.md)<br />-   [UML 元件圖：方針](../modeling/uml-component-diagrams-guidelines.md)|

## <a name="external-resources"></a>外部資源

|**分類**|**Links**|
|------------------|---------------|
|**論壇**|-   [Visual Studio Visualization & Modeling Tools](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL 工具)](https://go.microsoft.com/fwlink/?LinkId=184721)|

## <a name="see-also"></a>另請參閱
 [以視覺化](../modeling/visualize-code.md)方式將[應用程式的程式碼建立模型](../modeling/create-models-for-your-app.md)使用[開發流程](../modeling/use-models-in-your-development-process.md)中的模型[使用 Agile 開發](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)中的模型在[開發期間驗證您的系統](../modeling/validate-your-system-during-development.md)[擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)
