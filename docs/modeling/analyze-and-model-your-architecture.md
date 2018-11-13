---
title: 分析架構並製作架構模型
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4b32f5585c71f5767a907d9f3eb9c2dc8329ab97
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348874"
---
# <a name="analyze-and-model-your-architecture"></a>分析架構並製作架構模型

請確定您的應用程式符合藉由使用 Visual Studio 架構與模型化工具來設計和模型化應用程式的架構需求。

* 您可以使用 Visual Studio 視覺化程式碼的架構、行為和關聯性，更輕鬆地了解現有的程式碼。

* 教育您的小組需要遵守架構相依性。

* 請在開發過程中，於整個應用程式生命週期的不同詳細資料層級建立模型。

請參閱[案例： 使用視覺化和模型變更設計](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)。

## <a name="to"></a>以

|||
|-|-|
|**視覺化程式碼**：<br /><br /> -藉由建立 code map，請參閱程式碼的組織和關聯性。 將組件、命名空間、類別、方法等之間的相依性視覺化。<br />-藉由從程式碼建立類別圖，請參閱類別結構與特定專案的成員。<br />-藉由建立相依性圖表驗證程式碼中尋找您的程式碼和它的設計之間的衝突。|-   [視覺化程式碼](../modeling/visualize-code.md)<br />-   [使用類別和其他類型 （類別設計工具）](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [影片： 了解使用 Visual Studio 2015 code map 的程式碼的設計](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [影片： 驗證即時架構相依性](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**定義架構**：<br /><br /> -定義和強制執行您的程式碼，藉由建立相依性圖表的元件之間的相依性條件約束。|-   [影片： 驗證架構相依性，使用 Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**根據需求和預定設計驗證您的系統**<br /><br /> 驗證使用描述預定的架構的相依性圖表的程式碼相依性，並防止可能會與設計衝突的變更。|-   [影片： 驗證架構相依性，使用 Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**自訂模型和圖表**：<br /><br /> -建立您自己的定義域專屬語言。|-   [Modeling SDK for Visual Studio-特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**使用 T4 範本產生文字**：<br /><br /> -使用文字區塊和範本中的控制邏輯來產生文字檔案。<br /> -使用 Visual Studio 中包含的 MSBuild T4 範本建置|-   [程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)|
|**使用 Team Foundation 版本控制，共用模型、圖表和 Code Map**：<br /><br /> -將 code map、 專案和 Team Foundation 版本控制下的相依性圖表讓您可以共用它們。| |

若要查看哪些版本的 Visual Studio 支援每項功能，請參閱[architecture and modeling tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="types-of-models-and-typical-uses"></a>類型的模型和一般用法

### <a name="code-maps"></a>Code Map
Code Map 可協助您查看程式碼中的組織和關聯性。

**一般用法：**

-   檢查程式碼，以便進一步了解其結構和其相依性，了解如何更新，並評估提議的變更之成本。

**請參閱：**

-   [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)
-   [使用 Code Map 偵錯您的應用程式](../modeling/use-code-maps-to-debug-your-applications.md)
-   [使用 Code Map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagram"></a>相依性圖表
相依性圖表可讓您定義為一組圖層或區塊有明確的相依性的應用程式的結構。 您可以執行驗證，以探索程式碼中的相依性和相依性圖表上所述的相依性之間的衝突。

**一般用法：**

-   在應用程式存留期間，透過多次變更來穩固其結構。
-   在簽入變更到程式碼之前，探索意外的相依性衝突。

**請參閱：**

-   [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)
-   [相依性圖表︰參考](../modeling/layer-diagrams-reference.md)
-   [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>特定領域語言 (DSL)
DSL 是您為特定目的所設計的標記法。 在 Visual Studio 中，通常會以圖形表示。

**一般用法：**

-   產生或設定應用程式的組件。 開發標記法和工具必須進行一些工作。 此結果會比自訂 UML 更適用您的定義域。
-   用於大型專案或產品線，其中在開發 DSL 及其工具方面的投資，可因這個模型用於多個專案而回收。

**請參閱：**

-   [Modeling SDK for Visual Studio - 特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="where-can-i-get-more-information"></a>哪裡可以取得詳細資訊？

[Visual Studio Visualization & Modeling 工具論壇](http://go.microsoft.com/fwlink/?LinkId=184720)

## <a name="see-also"></a>另請參閱

- [新增功能](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps 與應用程式生命週期管理](/azure/devops/user-guide/devops-alm-overview)
