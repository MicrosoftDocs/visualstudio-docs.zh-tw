---
title: 使用視覺化和模型製作工具變更設計
description: 瞭解 Visual Studio 中的視覺效果和模型工具，以及如何使用這些工具來變更您的設計。
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
author: JoshuaPartlow
ms.author: joshuapa
ms.custom: SEO-VS-2020
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91b62716c87fafd965652452b6494fe255530e7b
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363857"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>情節：使用視覺化和模型功能變更設計

請使用 Visual Studio 中的視覺化與模型工具，確定您的軟體系統符合使用者的需求。
使用程式碼對應、相依性圖表及類別圖表等工具來：

若要查看支援各項工具的 Visual Studio 版本有哪些，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

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

## <a name="scenario-overview"></a>案例概觀

本情節描述兩間虛構公司 Dinner Now 與 Lucerne Publishing 在軟體開發週期所發生的事件。 Dinner Now 在西雅圖提供網站架構的餐點外送服務。 客戶可以訂購餐費，並在 [立即晚餐] 網站上支付費用。 然後訂單便會傳送到合適的當地餐廳以準備外送。 Lucerne Publishing 是一家位在紐約的公司，營業項目涵蓋幾項網路與非網路服務。 例如，他們會執行一個網站，讓客戶可以張貼餐廳評論。

Lucerne 最近併購 Dinner Now，並想要進行下列變更：

- 立即將餐廳審核功能新增至晚餐，以整合其網站。

- 將 Dinner Now 付款系統更換成 Lucerne 系統。

- 將 Dinner Now 服務範圍擴展到全地區。

Dinner Now 使用的是 SCRUM 與 eXtreme 程式設計。 其測試涵蓋範圍非常大，不受支援的程式碼非常少。 會先建立小型但可運作的系統版本，然後以累加的方式加入功能，藉此將風險降到最低。 他們採取短暫且頻繁的反覆項目來開發程式碼。 這讓他們對所做的變更很有信心，也能經常重構程式碼，同時避免「預先大量設計」(Big Design Up Front)。

Lucerne 則維持一個相當大型且複雜的系統集合，其中有些系統已超過 40 年。 有鑑於舊版程式碼的複雜度及範圍，他們對變更相當地謹慎。 他們遵循更嚴格的開發程序，要求設計詳細的解決方案，並將開發期間所做的設計與變更記錄下來。

雙方小組都使用 Visual Studio 的模型圖表，協助他們開發符合使用者需求的系統。 他們使用 Team Foundation Server 搭配其他工具，協助其規劃、組織及管理工作。

如需 Team Foundation Server 的詳細資訊，請參閱：

- [計畫和追蹤工作](#plan-and-track-work)

- [在經過更新的程式碼中進行測試、驗證及檢查](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a> 架構與模型圖表在軟體發展中的角色

下表描述在軟體開發週期多個及多種階段中，這些工具可以扮演的角色：

|工具/角色|使用者需求模型化|商務程序模型化|系統架構和設計|程式碼視覺化與探索|驗證|
|------|-|-|-|-|-|
|領域特定語言 (DSL) 圖表|是|是|是|||
|相依性圖表，圖層驗證|||是|是|是|
|Code Map|||是|是|是|
|類別設計工具 (以程式碼為基礎)||||是||

若要繪製相依性圖表，您必須建立模型專案作為現有方案的一部分，或建立一個新的方案。 這些圖表必須在模型專案中建立。
相依性圖表上的專案位於模型專案中，但不會儲存在一般模型中。 由程式碼建立的 Code Map 與 .NET 類別圖表則位在模型專案之外。

請參閱：

- [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)

- [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)

- [如何：將類別圖表新增至專案 (類別設計工具)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

- [Modeling SDK for Visual Studio - 特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

這兩個小組也會使用相依性驗證，以確保開發中的程式碼與設計保持一致。 請參閱：

- [使程式碼與設計保持一致](#ValidatingCode)

- [描述邏輯架構：相依性圖表](#DescribeLayers)

- [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> 某些版本的 Visual Studio 支援適用于視覺效果和模型化之 code map 的相依性驗證和唯讀版本。 若要查看 Visual Studio 支援這項功能的版本，請參閱 [架構和模型工具的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="understand-and-communicate-information-about-the-system"></a>瞭解並傳達系統的相關資訊

Visual Studio 模型圖表並沒有規定使用順序，所以您可以依需求或方法來加以使用。 小組在整個專案進行期間，通常會頻繁地反覆重新審視其模型。 每個圖表都具有特定優勢，可協助您了解、描述及溝通開發中系統的不同層面。

現在晚餐和 Lucerne 會使用圖表做為其通用語言，彼此通訊，並與專案專案關係人溝通。 例如，Dinner Now 會使用圖表執行這些工作：

- 將現有程式碼視覺化。

- 與 Lucerne 溝通新的或已更新的使用者劇本。

- 識別出支援新的或已更新的使用者劇本所必須進行的變更。

Lucerne 會使用圖表執行這些工作：

- 了解 Dinner Now 的商務程序。

- 了解系統的設計。

- 與 Dinner Now 溝通有關新的或已更新的使用者需求。

- 記錄對系統所做的更新。

圖表會與 Team Foundation Server 整合，如此小組就可以更輕鬆地規劃、管理及追蹤其工作。 例如，他們會使用模型來識別測試案例及開發工作，以及評估其工作。 Lucerne 將 Team Foundation Server 工作項目連結到模型項目，以便監控進度並確保系統符合使用者的需求。 例如，他們將使用案例連結到測試案例工作項目，如此在所有測試通過時即可知道使用案例已完成。

在小組簽入變更之前，他們會執行包含相依性驗證和自動化測試的組建，以針對測試和設計驗證程式代碼。 這樣有助於確定更新的程式碼不會與設計衝突，且不會破壞先前可運作的功能。

### <a name="identify-changes-to-the-existing-system"></a>識別現有系統的變更

Dinner Now 必須評估符合新需求所需的成本。 這有一部分取決於此變更對系統其他部分會造成多大的影響。 為協助他們了解，Dinner Now 的其中一位開發人員從現有程式碼建立下列地圖和圖表：

|**地圖或圖表**|**顯示**|
|-|-|
|*Code Map*<br /><br /> 請參閱：<br /><br /> - [將相依性對應到您的解決方案](../modeling/map-dependencies-across-your-solutions.md)<br />- [流覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)<br />- [藉由編輯 DGML 檔案自訂 code map](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|程式碼中的相依性及其他關聯性<br /><br /> 例如，Dinner Now 可能一開始會檢閱組件 Code Map，以取得組件及其相依性的概觀。 他們可以深入研究此地圖，以探索這些組件中的命名空間及類別。<br /><br /> Dinner Now 也可以建立地圖，以探索程式碼中的特定區域及其他種類的關聯性。 他們可以使用 [方案總管] 來尋找並選取其感興趣的區域及關聯性。|
|*以程式碼為基礎的類別圖表*<br /><br /> 請參閱[如何：將類別圖表新增至專案 (類別設計工具)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)。|程式碼中的現有類別|

 例如，開發人員建立了 Code Map。 接著調整其範圍以便將焦點放在新情節會影響的區域。 這些區域在地圖上會處於選取及醒目提示的狀態：

 ![命名空間相依性圖形](../modeling/media/namespace_reviewsystem.png)

 **命名空間 Code Map**

 開發人員展開選取的命名空間以查看其類別、方法及關聯性：

 ![展開的命名空間相依性圖形](../modeling/media/dep_reviewsystem.png)

 **展開的命名空間 Code Map，包含可見的跨群組連結**

 開發人員檢查程式碼以找出受影響的類別及方法。 若要在每次變更時查看所產生的影響，請在每次變更後重新產生 Code Map。 請參閱 [視覺化程式碼](../modeling/visualize-code.md)。

 若要描述對系統其他部分 (例如元件或互動) 所造成的變更，小組可能會在白板上繪製這些項目。 他們也可能會在 Visual Studio 中繪製下列圖表，如此雙方小組皆可擷取、管理及了解詳細資料。

|**圖表**|**描述**|
|-|-|
|*以程式碼為基礎的類別圖表*<br /><br /> 請參閱[如何：將類別圖表新增至專案 (類別設計工具)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)。|程式碼中的現有類別。|

### <a name="keep-code-consistent-with-the-design"></a><a name="ValidatingCode"></a> 使程式碼與設計保持一致
 Dinner Now 必須確定已更新的程式碼與設計保持一致。 它們會建立描述系統中功能層的相依性圖表、指定兩者之間允許的相依性，以及將方案成品與這些圖層產生關聯。

|**圖表**|**描述**|
|-|-|
|*相依性圖表*<br /><br /> 請參閱：<br /><br /> - [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)<br />- [相依性圖表：參考](../modeling/layer-diagrams-reference.md)<br />- [相依性圖表：指導方針](../modeling/layer-diagrams-guidelines.md)<br />- [使用相依性圖表驗證程式代碼](../modeling/validate-code-with-layer-diagrams.md)|程式碼的邏輯架構。<br /><br /> 相依性圖表會將 Visual Studio 方案中的成品組織和對應至稱為 *圖層* 的抽象群組。 這些圖層可識別這些成品在系統中執行的角色、工作或功能。<br /><br /> 相依性圖表適用于描述系統的預定設計，以及針對該設計驗證不斷演進的程式碼。<br /><br /> 若要建立圖層，請從 [方案總管]、[Code Map]、[類別檢視] 以及 [物件瀏覽器] 拖曳項目。 若要繪製新圖層，請使用工具箱或以滑鼠右鍵按一下圖表介面。<br /><br /> 若要查看現有的相依性，請在相依性圖表介面上按一下滑鼠右鍵，然後按一下 [產生相依性 **]**。 若要指定預定的相依性，請繪製新相依性。|

例如，下列相依性圖表描述各層之間的相依性，以及與每個圖層相關聯的成品數目：

![整合式付款系統的相依性圖表](../modeling/media/layer_integrated_dnlucerne.png)

 **相依性圖表**

為了確保在程式碼開發期間不會發生與設計衝突的情況，小組會在 Azure DevOps 上執行的組建上使用相依性驗證。 它們也會建立自訂 MSBuild 工作，以在其簽入作業中要求相依性驗證。 他們會使用組建報告來收集驗證錯誤。

請參閱：

- [使用視覺化設計工具](/azure/devops/pipelines/get-started-designer)

- [TFVC 閘道簽入](/azure/devops/pipelines/build/triggers)

- [組建和發行工作](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>與建立及使用模型相關的一般提示

- 大部分的圖表是由以線條連結之節點所組成。 針對每個圖表類型，工具箱會提供不同種類的節點及線條。

   若要開啟工具箱，請在 [檢視]  功能表上按一下 [工具箱] 。

- 若要建立節點，請將其從工具箱拖曳到圖表。 特定種類的節點必須拖曳到現有節點上。 例如，在元件圖表上，必須將新連接埠加入現有元件中。

- 若要建立線條或是連接，請在工具箱中依序按一下適當的工具、來源節點以及目標節點。 某些線條只能在特定種類的節點之間建立。 當您將指標移到可能的來源或目標上，指標就會指出您是否可以建立連接。

### <a name="plan-and-track-work"></a>計畫和追蹤工作

Visual Studio 模型圖表已經與 Team Foundation Server 整合，以便您可以更輕鬆地計畫、管理及追蹤工作。 兩個小組都使用模型來識別測試案例及開發工作，以及評估其工作。 Lucerne 建立 Team Foundation Server 工作項目並將其連結到模型項目，例如使用案例或元件。 這樣可協助他們監視進度及針對使用者需求追蹤工作。 也可協助他們確定所做的變更能持續符合這些需求。

當工作進行時，小組會更新工作項目以反映實際花在工作上的時間。 他們也會使用下列 Team Foundation Server 功能來監視及報告工作狀態：

- 每日的每日 *燒錄報表* ，顯示是否會在預期的時間內完成規劃的工作。 他們會從 Team Foundation Server 產生其他類似的報表來追蹤 Bug 進度。

- *「反覆項目工作表」* (Iteration Worksheet)，此工作表使用 Microsoft Excel 協助小組監視及平衡小組成員間的工作量。 此工作表連結到 Team Foundation Server，並在定期進度會議中提供討論重點。

- *「開發儀表板」* (Development Dashboard)，此儀表板使用 Office Project 讓小組隨時獲知重要的專案資訊。

請參閱：

- [關於 Agile 工具和 Agile 專案管理](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true)

- [圖表、儀表板和小工具 (Azure DevOps Services) ](/azure/devops/report/dashboards/overview?view=vsts&preserve-view=true)

- [使用 Project 建立您的待處理項目和工作](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="test-validate-and-check-in-code"></a><a name="TestValidateCheckInCode"></a> 測試、驗證和簽入程式碼

當小組完成每項工作時，他們會將程式碼簽入原始檔控制，並接收 Team Foundation Server 的提醒（如果忘記）。 在 Team Foundation Server 接受簽入之前，小組會執行單元測試和相依性驗證，以根據其測試案例和設計來驗證程式代碼。 它們會使用 Team Foundation Server 來定期執行組建、自動化單元測試和相依性驗證。 此行為有助於確定程式碼符合下列準則：

- 這麼做確實有成效。

- 不會破壞先前運作的程式碼。

- 不會與設計衝突。

Dinner Now 擁有大型自動化測試集合，因為這些測試幾乎仍適用，所以 Lucerne 可重複使用。 Lucerne 也可以根據這些測試進行建置，並加入新測試以涵蓋新功能。 同時也會使用 Visual Studio 執行手動測試。

為了確保程式碼符合設計，小組在 Azure DevOps 中設定其組建以包含相依性驗證。 如果發生任何衝突，則會產生包含詳細資料的報表。

請參閱：

- [測試應用程式](/azure/devops/test/overview?view=vsts&preserve-view=true)

- [在開發期間驗證您的系統](../modeling/validate-your-system-during-development.md)

- [使用版本控制](/azure/devops/repos/tfvc/overview?view=azure-devops&preserve-view=true)

- [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)

## <a name="update-the-system-using-visualization-and-modeling"></a>使用視覺效果和模型化來更新系統

Lucerne 及 Dinner Now 必須整合其付款系統。 下列各節將示範 Visual Studio 中的模型圖表如何協助其執行這項工作：

- [將現有程式碼視覺化：Code Map](#VisualizeCode)

- [定義類型的詞彙：類別圖表](#DefineClasses)

- [描述邏輯架構：相依性圖表](#DescribeLayers)

請參閱：

- [視覺化程式碼](../modeling/visualize-code.md)

- [在開發程序中使用模型](../modeling/use-models-in-your-development-process.md)

- [建立應用程式架構的模型](../modeling/model-your-app-s-architecture.md)

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a> 將現有程式碼視覺化： Code Map

Code Map 顯示程式碼的目前組織及關聯性。 項目在地圖上是以 *「節點」* (Node) 來代表，關聯性則是以 *「連結」*(Link) 來代表。 Code Map 可協助您執行下列種類的工作：

- 探索不熟悉的程式碼。

- 了解提議的變更可能會影響現有程式碼的哪些部分以及影響的方式。

- 尋找複雜性、自然相依性或模式的區域，或其他可能受益于改進的區域。

例如，Dinner Now 必須評估更新 PaymentProcessing 元件所需的成本。 這有一部分取決於此變更對系統其他部分會造成多大的影響。 為協助他們了解，Dinner Now 開發人員從程式碼產生 Code Map，並將範圍焦點調整在可能受變更影響的區域：

下列地圖顯示 PaymentProcessing 類別及 Dinner Now 系統其他部分之間的相依性，其以選取狀態顯示：

![Dinner Now 付款系統相依性圖形](../modeling/media/dep_dnpayment.png)

**Dinner Now 付款系統的 Code Map**

開發人員展開 PaymentProcessing 類別並選取其成員以探索地圖，進而查看可能受影響的區域。

![PaymentProcessing 和相依性內部的方法](../modeling/media/depgraph_expandeddn.png)

**PaymentProcessing 類別內部方法及其相依性**

他們針對 Lucerne 付款系統產生下列地圖以查看其類別、方法與相依性。 小組發現 Lucerne 系統可能也需要處理，以與 Dinner Now 系統其他部分互動：

![Lucerne 付款系統相依性圖形](../modeling/media/depgraph_lucernepay.png)

**Lucerne 付款系統的 Code Map**

雙方小組一塊合作，判斷整合雙方系統所需進行的變更。 他們決定重構部分程式碼，以方便進行更新。 PaymentApprover 類別將移到 DinnerNow.Business 命名空間，且需要一些新方法。 處理交易的 Dinner Now 類別將擁有自己的命名空間。 小組建立並使用工作項目以規劃、組織及追蹤工作。 他們將工作項目連結到對模型項目有用之處。

在重新組織程式碼之後，小組產生新的 Code Map 來查看已更新的結構及關聯性：

![包含重組程式碼的相依性圖形](../modeling/media/depgraph_integrated.png)

**程式碼已重新組織過的 Code Map**

此地圖顯示 PaymentApprover 類別目前已位於 DinnerNow.Business 命名空間中，且具有一些新方法。 Dinner Now 交易類別現在已擁有自己的 PaymentSystem 命名空間，之後處理該程式碼會變得更容易。

#### <a name="creating-a-code-map"></a>建立 Code Map

- 如需快速取得原始程式碼的概觀，請遵循這些步驟來產生 Code Map：

     在 [架構]  功能表上，按一下 [產生方案的 Code Map] 。

     若要快速取得已編譯程式碼的概觀，請建立空白的 Code Map，然後將組件檔或二進位檔拖曳到地圖介面上。

- 若要探索特定程式碼或方案項目，請使用 [方案總管] 來選取想要視覺化的項目及關聯性。 然後您可以產生新地圖，或將所選項目加入現有地圖中。 請參閱 [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md)。

- 為了協助您探索地圖，請重新整理配置，以便其符合您要執行的工作種類。

     例如，若要將程式碼的圖層視覺化，請選取樹狀配置。 請參閱 [流覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)。

#### <a name="summary-strengths-of-code-maps"></a>摘要：Code Map 的優勢
 Code Map 可協助您：

- 深入了解現有程式碼的組織及關聯性。

- 識別所提議的變更可能影響的區域。

- 尋找複雜度、模式、圖層的區域，或可加以改善而讓程式碼更易於維護、變更及重複使用的其他區域。

#### <a name="relationship-to-other-diagrams"></a>與其他圖表的關聯性

|**圖表**|**描述**|
|-|-|
|相依性圖表|系統的邏輯架構。 使用相依性驗證可確保程式碼與設計保持一致。<br /><br /> 若要協助您識別現有的相依性或預定的相依性，請建立 code map 並將相關專案分組。 若要建立相依性圖表，請參閱：<br /><br /> - [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)<br />- [相依性圖表：指導方針](../modeling/layer-diagrams-guidelines.md)|
|類別圖表 (以程式碼為基礎)|特定專案程式碼中的現有類別。<br /><br /> 若要修改程式碼中的現有類別並將其視覺化，請使用 [類別設計工具]。<br /><br /> 請參閱[如何：將類別圖表新增至專案 (類別設計工具)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)。|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a> 定義類型的詞彙：類別圖表
 類別圖表定義參與系統的實體、詞彙或概念，以及彼此的關聯性。 例如，您可以在開發期間使用這些圖表來描述每個類別的屬性及作業，不論其實作語言或樣式為何。

 為了協助 Lucerne 描述及討論參與「處理付款」使用案例的實體，他們繪製了下列類別圖表：

 ![類別圖表上的「處理付款」實體](../modeling/media/uml_payentities.png)

 **類別圖表上的「處理付款」實體**

 此圖表顯示「客戶」可以有多個訂單及不同的付款方式。 BankAccount 與 CreditCard 都繼承自 Payment。

 在開發期間，Lucerne 使用下列類別圖表來描述及討論每個類別的詳細資料：

 ![類別圖表上的「處理付款」實體詳細資料](../modeling/media/uml_payment.png)

 **類別圖表上的「處理付款」詳細資料**

#### <a name="drawing-a-class-diagram"></a>繪製類別圖表

類別圖表具有下列主要功能：

- 類型，例如類別、介面及列舉：

  - *「類別」* (Class) 是物件的定義，而這些物件共用特定的結構或行為特性。

  - *「介面」* (Interface) 會定義物件外部可見行為的一部分。

  - *「列舉」* (Enumeration) 是包含常值清單的分類器。

- *「屬性」* (Attribute) 是特定類型的值，其描述 *「分類器」*(Classifier) 的每個執行個體。 分類器是類型、元件、使用案例的一般名稱，甚至是執行者的一般名稱。

- *「作業」* (Operation) 是分類器執行個體可以執行的方法或函式。

- *「關聯」* (Association) 表示兩個分類器之間的某種關聯性。

  - *「彙總」* (Aggregation) 是一種關聯，表示兩個分類器之間的共用擁有權。

  - *「組合」* (Composition) 是一種關聯，表示兩個分類器之間的整體-部分關聯性。

    若要顯示彙總或組合，請在關聯上設定 **彙總** 屬性。 **共用** 顯示彙總， **組合** 則顯示組合。

- *「相依性」* (Dependency) 表示若變更某個分類器的定義，可能會變更另一個分類器的定義。

- *「一般化」* (Generalization) 表示特定分類器的部分定義繼承自一般分類器。 *「實現」* (Realization) 表示類別實作介面提供的作業及屬性。

     若要建立這些關聯性，請使用 [繼承]  工具。 另外，實現可以用 *「棒棒糖符號」*(Lollipop) 表示。

- *「封裝」* (Package) 是分類器、關聯、生命線、元件及其他封裝的群組。 *「匯入」* (Import) 關聯性表示某個封裝包含另一個封裝的所有定義。

您可以使用 [類別設計工具] 從程式碼建立類別圖，來開始探索及討論現有類別。

- [如何：將類別圖表新增至專案 (類別設計工具)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

#### <a name="summary-strengths-of-class-diagrams"></a>摘要：類別圖表的優勢
 類別圖表可協助您定義下列項目：

- 討論使用者需求及參與系統的實體時可使用的常用詞彙。 請參閱 [模型使用者需求](../modeling/model-user-requirements.md)。

- 系統組成部分 (例如元件) 使用的類型，不論其實作為何。 請參閱 [模型您的應用程式架構](../modeling/model-your-app-s-architecture.md)。

- 類型之間的關聯性 (例如相依性)。 例如，您可以顯示某個類型可以與另一個類型的多個執行個體相關聯。

#### <a name="relationship-to-other-diagrams"></a>與其他圖表的關聯性

|**圖表**|**說明**|
|-|-|
|相依性圖表|定義與類別相關的系統邏輯架構。<br /><br /> 使用相依性驗證可確保程式碼與設計保持一致。<br /><br /> 請參閱：<br /><br /> - [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)<br />- [相依性圖表：參考](../modeling/layer-diagrams-reference.md)<br />- [相依性圖表：指導方針](../modeling/layer-diagrams-guidelines.md)<br />- [使用相依性圖表驗證程式代碼](../modeling/validate-code-with-layer-diagrams.md)|
|Code Map|將現有程式碼中的組織與關聯性視覺化。<br /><br /> 若要識別類別、其關聯性及方法，請建立會顯示這些項目的 Code Map。<br /><br /> 請參閱：<br /><br /> - [將相依性對應到您的解決方案](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="describe-the-logical-architecture-dependency-diagrams"></a><a name="DescribeLayers"></a> 描述邏輯架構：相依性圖表
 相依性圖表會藉由將方案中的成品組織成抽象群組或 *圖層*，來描述系統的邏輯架構。 成品可以是多個項目，例如命名空間、專案、類別、方法等等。 圖層代表及描述成品在系統中執行的角色或工作。 您也可以在組建中加入圖層驗證並簽入作業，以確定程式碼與設計維持一致。

 為了讓程式碼與設計保持一致，現在晚餐和 Lucerne 使用下列相依性圖表來驗證程式代碼的發展：

 ![整合式付款系統的相依性圖表](../modeling/media/layer_integrated_dnlucerne.png)

 **晚餐的相依性圖表現在已與 Lucerne 整合**

 這個圖表上的圖層會連結到對應的 Dinner Now 及 Lucerne 方案成品。 例如，商務圖層會連結到 DinnerNow.Business 命名空間及其成員，其目前已包含 PaymentApprover 類別。 資源存取圖層會連結到 DinnerNow.Data 命名空間。 箭號 (也就是 *「相依性」*(Dependency)) 會指定只有商務圖層可以使用位於資源存取圖層中的功能。 小組在更新程式碼時，圖層驗證會定期執行，以便在發生衝突時加以攔截，並協助小組立即解決衝突。

 小組共同合作，以逐步進行整合並測試這兩個系統。 他們首先確定 PaymentApprover 與 Dinner Now 其餘部分彼此可順利運作，才會處理 PaymentProcessing。

 下列 Code Map 顯示 Dinner Now 及 PaymentApprover 之間的新呼叫：

 ![包含已整合之系統的更新相依性圖形](../modeling/media/depgraph_intsystem.png)

 **內含已更新方法呼叫的 Code Map**

 在確定系統如預期運作之後，Dinner Now 會將 PaymentProcessing 程式碼註解化。 圖層驗證報表結果無誤，且產生的 Code Map 顯示沒有任何 PaymentProcessing 相依性存在：

 ![沒有 PaymentProcessing 的相依性圖形](../modeling/media/depgraph_nomore.png)

 **未含 PaymentProcessing 的 Code Map**

#### <a name="drawing-a-dependency-diagram"></a>繪製相依性圖表

相依性圖表具有下列主要功能：

- *「圖層」* (Layer) 描述成品的邏輯群組。

- *「連結」* (Link) 是圖層與成品之間的關聯。

     若要從成品建立圖層，請從 [方案總管]、[Code Map]、[類別檢視] 或 [物件瀏覽器] 拖曳項目。 若要繪製新圖層再連結到成品，請使用工具箱或以滑鼠右鍵按一下圖表介面以建立圖層，然後將項目拖曳到這些圖層。

     圖層上的數字會顯示圖層連結的成品數目。 這些成品可以是命名空間、專案、類別、方法等等。 當您解譯圖層上的成品數目時，請記住下列事項：

  - 如果圖層連結的成品有包含其他成品，但圖層未直接連結這些其他成品，則數字將只包含連結的成品。 然而，在圖層驗證期間會加入其他成品以進行分析。

       例如，如果圖層連結到單一命名空間，即使命名空間包含類別，連結的成品數目仍為 1。 如果圖層也有命名空間中每個類別的連結，則數字將包含這些已連結的類別。

  - 如果圖層包含已連結到成品的其他圖層，即使此容器圖層上的數字未包含那些成品，容器圖層也會連結到那些成品。

    若要查看連結到圖層的成品，請以滑鼠右鍵按一下相依性，然後按一下 [ **View Links** ] 以開啟 [ **圖層瀏覽器**]。

- *「相依性」* (Dependency) 表示某個圖層可以使用另一個圖層中的功能，但反過來則不行。 *「雙向相依性」* (Bidirectional Dependency) 表示某個圖層可以使用另一個圖層中的功能，反之亦然。

     若要顯示相依性圖表上的現有相依性，請以滑鼠右鍵按一下圖表介面，然後按一下 [產生相依性 **]**。 若要描述預定的相依性，請繪製新的相依性。

請參閱：

- [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)

- [相依性圖表︰參考](../modeling/layer-diagrams-reference.md)

- [相依性圖表︰方針](../modeling/layer-diagrams-guidelines.md)

- [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-dependency-diagrams"></a>摘要：相依性圖表的優勢

相依性圖表可協助您：

- 根據成品功能描述系統的邏輯架構。

- 確保開發中的程式碼符合指定的設計。

#### <a name="relationship-to-other-diagrams"></a>與其他圖表的關聯性

|**圖表**|**說明**|
|-|-|
|Code Map|將現有程式碼中的組織與關聯性視覺化。<br /><br /> 若要建立圖層，請產生 Code Map，然後在地圖上將項目分組為可能的圖層。 將群組從地圖拖曳至相依性圖表。<br /><br /> 請參閱：<br /><br /> - [將相依性對應到您的解決方案](../modeling/map-dependencies-across-your-solutions.md)<br />- [流覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)|

## <a name="external-resources"></a>外部資源

|**類別**|**連結**|
|-|-|
|**論壇**|- [Visual Studio Visualization & Modeling Tools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio Visualization & Modeling SDK (DSL 工具)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>請參閱

- [視覺化程式碼](../modeling/visualize-code.md)
- [在開發程序中使用模型](../modeling/use-models-in-your-development-process.md)
- [在 Agile 開發中使用模型](/previous-versions/ff398061(v=vs.140))
- [在開發期間驗證您的系統](../modeling/validate-your-system-during-development.md)