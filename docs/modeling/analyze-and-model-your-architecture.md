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
ms.openlocfilehash: be58a86ec6c3b87954ff5b5be012ce636ad52204
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106956"
---
# <a name="analyze-and-model-your-architecture"></a>分析架構並製作架構模型
請確定您的應用程式可以使用 Visual Studio architecture and modeling 工具來設計和模型化應用程式符合架構需求。

* 您可以使用 Visual Studio 視覺化程式碼的架構、行為和關聯性，更輕鬆地了解現有的程式碼。

* 教育尊重架構的相依性的需求中小組。

* 請在開發過程中，於整個應用程式生命週期的不同詳細資料層級建立模型。

請參閱[案例： 使用視覺化和模型變更設計](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)。

## <a name="to"></a>以

|||
|-|-|
|**視覺化程式碼**：<br /><br /> -藉由建立 code map，請參閱程式碼的組織和關聯性。 將組件、命名空間、類別、方法等之間的相依性視覺化。<br />-藉由從程式碼建立類別圖，了解的類別結構和特定專案的成員。<br />-藉由建立相依性圖表驗證程式碼，找出您的程式碼和其設計之間的衝突。|-   [視覺化程式碼](../modeling/visualize-code.md)<br />-   [使用類別和其他類型 （類別設計工具）](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [影片： 了解的程式碼與 Visual Studio 2015 程式碼對應的設計](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [影片： 驗證您的架構相依性，即時](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**定義架構**：<br /><br /> 定義和強制執行您的程式碼，藉由建立相依性圖表的元件之間的相依性條件約束。|-   [影片： 驗證架構相依性，使用 Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**根據需求和預定設計驗證您的系統**<br /><br /> 驗證程式碼相依性與使用描述預定的架構的相依性圖表，並防止可能會與設計衝突的變更。|-   [影片： 驗證架構相依性，使用 Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**自訂模型和圖表**：<br /><br /> -建立您自己的特定領域語言。|-   [Modeling SDK for Visual Studio-特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**使用 T4 範本產生文字**：<br /><br /> -使用文字區塊和控制邏輯內部範本產生文字為基礎的檔案。<br /> -使用 Visual Studio 中包含的 MSBuild T4 範本建置|-   [程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)|
|**使用 Team Foundation 版本控制，共用模型、圖表和 Code Map**：<br /><br /> -將 code map、 專案和 Team Foundation 版本控制下的相依性圖表，您就可以共用它們。| |

若要查看支援各項功能的 Visual Studio 版本有哪些，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

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
相依性圖表，可讓您為圖層或明確的相依性的文字區塊的一組定義的應用程式的結構。 您可以執行驗證，以探索程式碼中的相依性和相依性圖上描述的相依性之間的衝突。

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

- [最新消息](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps 與應用程式生命週期管理](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
