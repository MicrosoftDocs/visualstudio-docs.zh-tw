---
title: 分析並製作架構模型 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 59cb744b64137a3ccf34e87d89abcba22e2afc9b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681001"
---
# <a name="analyze-and-model-your-architecture"></a>分析架構並製作架構模型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 Visual Studio Architecture and Modeling Tools 設計應用程式並建立應用程式模型，確保您的應用程式符合使用者需求。 您可以使用 Visual Studio 視覺化程式碼的架構、行為和關聯性，更輕鬆地了解現有的程式碼。  
  
 請在開發過程中，於整個應用程式生命週期的不同詳細資料層級建立模型。 您可以將模型項目連結至 Team Foundation Server 工作項目和開發計劃，來追蹤需求、工作、測試案例、Bug 和其他與模型相關聯的工作。 請參閱[案例：變更您的設計使用視覺化和模型化](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)。  
  
 若要查看支援各項功能的 Visual Studio 版本有哪些，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="to"></a>若要  
  
|||  
|-|-|  
|**視覺化程式碼**：<br /><br /> -藉由建立 code map，請參閱程式碼的組織和關聯性。 將組件、命名空間、類別、方法等之間的相依性視覺化。<br />-藉由從程式碼建立類別圖，請參閱類別結構與特定專案的成員。<br />-藉由建立分層圖驗證程式碼中尋找您的程式碼和它的設計之間的衝突。<br /><br /> **注意**：在這一版的 Visual Studio 中，詞彙*的 code map*用來取代*相依性圖形*。 *「圖形」* (Graph) 一詞單獨使用時，通常是指有向圖形或 DGML 圖表 (或文件)。 Code Map 是特殊類型的 DGML 圖表。|-   [視覺化程式碼](../modeling/visualize-code.md)<br />-   [使用類別和其他類型 （類別設計工具）](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [影片：了解您的程式碼相依性，透過視覺效果 (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252065)<br />-   [影片：以視覺化方式檢視變更 (Channel 9) 的影響](http://go.microsoft.com/fwlink/?LinkID=252068)|  
|**描述以及溝通使用者需求**：<br /><br /> 為釐清使用者劇本、 商務規則和其他需求，並協助確保一致性，藉由繪製 UML 圖表，例如使用案例、 活動和類別圖表。|-   [建立應用程式模型](../modeling/create-models-for-your-app.md)<br />-   [模型使用者需求](../modeling/model-user-requirements.md)<br />-   [影片：改善透過模型 (Channel 9) 的架構](http://go.microsoft.com/fwlink/?LinkID=252078)|  
|**定義架構**：<br /><br /> -模型藉由繪製 UML 元件、 類別和循序圖的大型結構之軟體系統和設計模式。<br />-定義和強制執行您的程式碼，藉由建立分層圖的元件之間的相依性條件約束。|-   [建立應用程式模型](../modeling/create-models-for-your-app.md)<br />-   [您的應用程式架構模型](../modeling/model-your-app-s-architecture.md)<br />-   [影片：改善透過模型 (Channel 9) 的架構](http://go.microsoft.com/fwlink/?LinkID=252078)<br />-   [影片：使用分層圖設計和驗證架構 (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252073)|  
|**根據需求和預定設計驗證您的系統**<br /><br /> -定義接受度測試或以需求模型為基礎的系統測試。 這樣可在測試與使用者需求之間建立強式關聯性，並且協助您在需求變更時更輕鬆地更新系統。<br />驗證使用描述預定的架構的分層圖的程式碼相依性，並防止可能會與設計衝突的變更。|-   [在開發期間驗證您的系統](../modeling/validate-your-system-during-development.md)<br />-   [影片：使用分層圖設計和驗證架構 (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252073)|  
|**使用 Team Foundation 版本控制，共用模型、圖表和 Code Map**：<br /><br /> -將 code map、 模型專案、 UML 圖表和分層圖，在 Team Foundation 版本控制，讓您可以共用它們。|當多位使用者在 Team Foundation 版本控制使用這些項目時，請使用下列方針協助您避免版本控制問題：<br /><br /> -   [管理模型與版本控制下的圖表](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**產生或設定從 UML 或特定領域語言撰寫成應用程式的組件**：<br /><br /> -讓您設計更快速地回應需求變更且輕鬆地變數不同產品線。|-   [產生和設定您的應用程式，從模型](../modeling/generate-and-configure-your-app-from-models.md)|  
|**自訂模型和圖表**：<br /><br /> -調整模型如何您的專案藉由定義 UML 項目，藉此確定您的模型符合您的商務規則和其他功能表命令和工具箱項目驗證條件約束的其他屬性來使用它們。<br />-建立您自己的定義域專屬語言。|-   [擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)<br />-   [Modeling SDK for Visual Studio-特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**使用 T4 範本產生文字**：<br /><br /> -使用文字區塊和範本中的控制邏輯來產生文字檔案。|-   [程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)|  
  
## <a name="types-of-models-and-their-uses"></a>模型的類型及其用法  
  
|**模型類型和一般用法**|  
|-------------------------------------|  
|**Code Map**<br /><br /> Code Map 可協助您查看程式碼中的組織和關聯性。<br /><br /> 一般用法：<br /><br /> -檢查程式碼讓您更可以了解其結構和其相依性，如何更新，以及估計的成本提議的變更。<br /><br /> 請參閱：<br /><br /> -   [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)<br />-   [使用 code map 偵錯應用程式](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [使用 code map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**分層圖**<br /><br /> 分層圖可讓您將應用程式的結構定義成一組圖層或區塊，其中含有明確相依性。 您可以執行驗證，藉此探索程式碼中相依性之間的衝突，以及探索分層圖上描述的相依性之衝突。<br /><br /> 一般用法：<br /><br /> -存留期間來穩固其結構，透過多次變更應用程式。<br />簽入程式碼變更之前探索意外的相依性衝突。<br /><br /> 請參閱：<br /><br /> -   [從您的程式碼建立分層圖](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [分層圖：參考](../modeling/layer-diagrams-reference.md)<br />-   [使用分層圖驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)|  
|**UML 模型**<br /><br /> UML 模型具有幾種檢視，包含類別、元件、使用案例、活動和循序圖表。 您可以自訂 UML 以符合您的應用程式定義域。 例如，您可以將標記、其他資訊和條件約束附加到模型項目。 您也可以定義會在模型上作業的工具。 請參閱[建立應用程式模型](../modeling/create-models-for-your-app.md)。<br /><br /> 一般用法：<br /><br /> -描述需求和設計。 您可以快速地將 UML 應用在任何應用程式的開發作業。 請參閱[在開發程序中使用模型](../modeling/use-models-in-your-development-process.md)。<br />產生或設定測試或應用程式的組件。 您必須完成某些工作，才能自訂標記法和開發產生範本或可設定的應用程式。 請參閱[產生，並設定您的應用程式，從模型](../modeling/generate-and-configure-your-app-from-models.md)。<br />-若為一般的描述，並產生程式碼或在較小的專案中的組態。|  
|**特定領域語言 (DSL)**<br /><br /> DSL 是您為特定目的所設計的標記法。 在 Visual Studio 中，通常會以圖形表示。<br /><br /> 一般用法：<br /><br /> 產生或設定應用程式的組件。 開發標記法和工具必須進行一些工作。 此結果會比自訂 UML 更適用您的定義域。<br />-若為大型專案或產品線，其中投入開發 DSL 及其工具由多個專案中使用。<br /><br /> 請參閱：<br /><br /> -   [Modeling SDK for Visual Studio-特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>哪裡可以取得詳細資訊？  
  
|||  
|-|-|  
|**論壇**|-   [Visual Studio Visualization & Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL 工具)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>另請參閱  

- [Visual Studio 2015 中的模型化的最新消息](../modeling/what-s-new-for-design-in-visual-studio.md)   
- [DevOps 與應用程式生命週期管理](https://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
