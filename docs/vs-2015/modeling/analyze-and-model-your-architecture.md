---
title: 分析架構並為其建立模型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 129
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 38a65a98c1dca5542d3e0e667cb623283bb164c7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602428"
---
# <a name="analyze-and-model-your-architecture"></a>分析架構並製作架構模型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 Visual Studio Architecture and Modeling Tools 設計應用程式並建立應用程式模型，確保您的應用程式符合使用者需求。 您可以使用 Visual Studio 視覺化程式碼的架構、行為和關聯性，更輕鬆地了解現有的程式碼。

 請在開發過程中，於整個應用程式生命週期的不同詳細資料層級建立模型。 您可以將模型項目連結至 Team Foundation Server 工作項目和開發計劃，來追蹤需求、工作、測試案例、Bug 和其他與模型相關聯的工作。 請參閱[案例：使用視覺化和模型化來變更您的設計](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)。

 若要查看支援各項功能的 Visual Studio 版本有哪些，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="to"></a>若要

|||
|-|-|
|**視覺化程式碼**：<br /><br /> -藉由建立 code map，查看程式碼的組織和關聯性。 將組件、命名空間、類別、方法等之間的相依性視覺化。<br />-從程式碼建立類別圖表，以查看特定專案的類別結構和成員。<br />-藉由建立分層圖來驗證程式代碼，尋找您的程式碼與設計之間的衝突。<br /><br /> **注意**：在本版 Visual Studio 中，會以 *Code Map* 一詞取代 *「相依性圖形」* (Dependency Graph)。 *「圖形」* (Graph) 一詞單獨使用時，通常是指有向圖形或 DGML 圖表 (或文件)。 Code Map 是特殊類型的 DGML 圖表。|-   [視覺化程式碼](../modeling/visualize-code.md)<br />-   [使用類別和其他類型（類別設計工具）](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [影片：透過視覺化瞭解程式碼相依性（Channel 9）](http://go.microsoft.com/fwlink/?LinkID=252065)<br />-   [影片：視覺化變更的影響（Channel 9）](http://go.microsoft.com/fwlink/?LinkID=252068)|
|**描述以及溝通使用者需求**：<br /><br /> -藉由繪製 UML 圖表，例如使用案例、活動和類別圖，來澄清使用者故事、商務規則和其他需求，並協助確保其一致性。|-   [為您的應用程式建立模型](../modeling/create-models-for-your-app.md)<br />-   [模型使用者需求](../modeling/model-user-requirements.md)<br />-   [影片：透過模型改進架構（Channel 9）](http://go.microsoft.com/fwlink/?LinkID=252078)|
|**定義架構**：<br /><br /> -藉由繪製 UML 元件、類別和順序圖表，建立軟體系統的大規模結構和設計模式的模型。<br />-藉由建立分層圖，定義和強制執行程式碼元件之間相依性的條件約束。|-   [為您的應用程式建立模型](../modeling/create-models-for-your-app.md)<br />-    為[您的應用程式架構建立模型](../modeling/model-your-app-s-architecture.md)<br />-   [影片：透過模型改進架構（Channel 9）](http://go.microsoft.com/fwlink/?LinkID=252078)<br />-   [影片：使用分層圖設計和驗證架構（Channel 9）](http://go.microsoft.com/fwlink/?LinkID=252073)|
|**根據需求和預定設計驗證您的系統**<br /><br /> -根據需求模型定義接受度測試或系統測試。 這樣可在測試與使用者需求之間建立強式關聯性，並且協助您在需求變更時更輕鬆地更新系統。<br />-使用描述所需架構的分層圖來驗證程式代碼相依性，並防止可能與設計衝突的變更。|-   [在開發期間驗證您的系統](../modeling/validate-your-system-during-development.md)<br />-   [影片：使用分層圖設計和驗證架構（Channel 9）](http://go.microsoft.com/fwlink/?LinkID=252073)|
|**使用 Team Foundation 版本控制，共用模型、圖表和 Code Map**：<br /><br /> -將 code map、模型專案、UML 圖表和分層圖放在 Team Foundation 版本控制之下，讓您可以共用它們。|當多位使用者在 Team Foundation 版本控制使用這些項目時，請使用下列方針協助您避免版本控制問題：<br /><br /> -   [在版本控制下管理模型和圖表](../modeling/manage-models-and-diagrams-under-version-control.md)|
|**產生或設定從 UML 或特定領域語言撰寫成應用程式的組件**：<br /><br /> -讓您的設計能夠更快回應需求變更，並在產品線上輕鬆變數。|-   [從模型產生和設定您的應用程式](../modeling/generate-and-configure-your-app-from-models.md)|
|**自訂模型和圖表**：<br /><br /> -藉由定義 UML 專案的其他屬性、驗證條件約束以確保模型符合您的商務規則，以及其他功能表命令和工具箱專案，將模型調整為您的專案使用它們的方式。<br />-建立您自己的特定領域語言。|-   [擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)<br />[適用于 Visual Studio 網域特定語言的 -    模型 SDK](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**使用 T4 範本產生文字**：<br /><br /> -使用文字區塊並控制範本內部的邏輯，以產生以文字為基礎的檔案。|-    程式[代碼產生和 T4 文字模板](../modeling/code-generation-and-t4-text-templates.md)|

## <a name="types-of-models-and-their-uses"></a>模型的類型及其用法

|**模型類型和一般用法**|
|-------------------------------------|
|**Code Map**<br /><br /> Code Map 可協助您查看程式碼中的組織和關聯性。<br /><br /> 一般用法：<br /><br /> -檢查程式碼，以便進一步瞭解其結構和其相依性、如何更新，以及估計提議變更的成本。<br /><br /> 請參閱：<br /><br /> -   [對應方案之間的](../modeling/map-dependencies-across-your-solutions.md)相依性<br />-   [使用 code map 來對應用程式進行 debug](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [使用 Code Map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**分層圖**<br /><br /> 分層圖可讓您將應用程式的結構定義成一組圖層或區塊，其中含有明確相依性。 您可以執行驗證，藉此探索程式碼中相依性之間的衝突，以及探索分層圖上描述的相依性之衝突。<br /><br /> 一般用法：<br /><br /> -在應用程式的生命週期內，透過許多變更來穩定其結構。<br />-在將變更簽入程式碼之前，探索意外的相依性衝突。<br /><br /> 請參閱：<br /><br /> -   [從您的程式碼建立分層圖](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [分層圖：參考](../modeling/layer-diagrams-reference.md)<br />-   [使用圖層圖表驗證程式代碼](../modeling/validate-code-with-layer-diagrams.md)|
|**UML 模型**<br /><br /> UML 模型具有幾種檢視，包含類別、元件、使用案例、活動和循序圖表。 您可以自訂 UML 以符合您的應用程式定義域。 例如，您可以將標記、其他資訊和條件約束附加到模型項目。 您也可以定義會在模型上作業的工具。 請參閱[為您的應用程式建立模型](../modeling/create-models-for-your-app.md)。<br /><br /> 一般用法：<br /><br /> -描述需求和設計。 您可以快速地將 UML 應用在任何應用程式的開發作業。 請參閱[在開發過程中使用模型](../modeling/use-models-in-your-development-process.md)。<br />-產生或設定應用程式的測試或部分。 您必須完成某些工作，才能自訂標記法和開發產生範本或可設定的應用程式。 請參閱[從模型產生和設定您的應用程式](../modeling/generate-and-configure-your-app-from-models.md)。<br />-適用于較小專案中的一般描述和程式碼產生或設定。|
|**特定領域語言 (DSL)**<br /><br /> DSL 是您為特定目的所設計的標記法。 在 Visual Studio 中，通常會以圖形表示。<br /><br /> 一般用法：<br /><br /> -產生或設定應用程式的元件。 開發標記法和工具必須進行一些工作。 此結果會比自訂 UML 更適用您的定義域。<br />-適用于大型專案或產品線，其中開發 DSL 和其工具的投資會由其在多個專案中使用而傳回。<br /><br /> 請參閱：<br /><br /> [適用于 Visual Studio 網域特定語言的 -    模型 SDK](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>哪裡可以取得詳細資訊？

|||
|-|-|
|**論壇**|-   [Visual Studio Visualization & Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL 工具)](http://go.microsoft.com/fwlink/?LinkId=184721)|

## <a name="see-also"></a>請參閱

- [Visual Studio 2015 中的模型新功能](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps 與應用程式生命週期管理](https://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
