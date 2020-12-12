---
title: 分析架構並製作架構模型
description: 瞭解如何使用 Visual Studio 架構和模型工具來設計和建立應用程式模型，以確定您的應用程式符合架構需求。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- diagrams - modeling
- architecture
- code visualization
- application design
- code exploration
- modeling
- application architecture
- architecture [Visual Studio ALM], modeling
- application modeling
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71296b9ccb2e442d1bd9bc13865e0086821bf030
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361153"
---
# <a name="analyze-and-model-your-architecture"></a>分析架構並製作架構模型

使用 Visual Studio 架構和模型工具來設計和模型化應用程式，以確定您的應用程式符合架構需求。

* 您可以使用 Visual Studio 視覺化程式碼的架構、行為和關聯性，更輕鬆地了解現有的程式碼。

* 為您的團隊教育架構相依性的需求。

* 請在開發過程中，於整個應用程式生命週期的不同詳細資料層級建立模型。

請參閱 [案例：使用視覺化和模型化來變更您的設計](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)。

## <a name="article-reference"></a>文章參考

|案例|文章|
|-|-|
|**視覺化程式碼**：<br /><br />-藉由建立 code map 來查看程式碼的組織和關聯性。 將組件、命名空間、類別、方法等之間的相依性視覺化。<br />-從程式碼建立類別圖表，以查看特定專案的類別結構和成員。<br />-藉由建立相依性圖表來驗證程式代碼，尋找您的程式碼與其設計之間的衝突。|- [視覺化程式碼](../modeling/visualize-code.md)<br />- [使用類別和其他類型 (類別設計工具) ](../ide/class-designer/designing-and-viewing-classes-and-types.md)<br />- [影片：利用 Visual Studio 2015 code map 瞭解程式碼的設計](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />- [影片：即時驗證您的架構相依性](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**定義架構**：<br /><br />-藉由建立相依性圖表來定義和強制執行程式碼元件之間的相依性條件約束。|- [影片：使用 Visual Studio (Channel 9 驗證架構相依性) ](https://channel9.msdn.com/Events/Connect/2016/170)|
|**根據需求和預定設計驗證您的系統**<br /><br />-使用描述預期架構的相依性圖表驗證程式代碼相依性，並防止可能與設計發生衝突的變更。|- [影片：使用 Visual Studio (Channel 9 驗證架構相依性) ](https://channel9.msdn.com/Events/Connect/2016/170)|
|**自訂模型和圖表**：<br /><br />-建立您自己的特定領域語言。|- [Visual Studio Domain-Specific 語言的模型 SDK](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**使用 T4 範本產生文字**：<br /><br />-在範本內使用文字區塊和控制邏輯來產生以文字為基礎的檔案。<br /> -Visual Studio 中包含 MSBuild 的 T4 範本組建|- [程式碼產生和 T4 文字模板](../modeling/code-generation-and-t4-text-templates.md)|
|**使用 Team Foundation 版本控制，共用模型、圖表和 Code Map**：<br /><br />-在 Team Foundation 版本控制下放置 code map、專案和相依性圖表，讓您可以共用這些專案。| |

若要查看 Visual Studio 支援每項功能的版本，請參閱 [架構和模型工具的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="types-of-models-and-typical-uses"></a>模型類型和一般用法

### <a name="code-maps"></a>Code Map

Code Map 可協助您查看程式碼中的組織和關聯性。

**一般用途：**

- 檢查程式碼，以便進一步了解其結構和其相依性，了解如何更新，並評估提議的變更之成本。

**看到：**

- [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)
- [使用 Code Map 偵錯您的應用程式](../modeling/use-code-maps-to-debug-your-applications.md)
- [使用 Code Map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagrams"></a>相依性圖表

相依性圖表可讓您將應用程式的結構定義為一組具有明確相依性的圖層或區塊。 即時驗證會顯示程式碼中的相依性與相依性圖表上所述相依性之間的衝突。

**一般用途：**

- 在應用程式存留期間，透過多次變更來穩固其結構。
- 在簽入變更到程式碼之前，探索意外的相依性衝突。

**看到：**

- [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)
- [相依性圖表︰參考](../modeling/layer-diagrams-reference.md)
- [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>特定領域語言 (DSL)

DSL 是您為特定目的所設計的標記法。 在 Visual Studio 中，它通常是圖形化的。

**一般用途：**

- 產生或設定應用程式的組件。 開發標記法和工具必須進行一些工作。 此結果會比自訂 UML 更適用您的定義域。
- 用於大型專案或產品線，其中在開發 DSL 及其工具方面的投資，可因這個模型用於多個專案而回收。

**看到：**

- [Modeling SDK for Visual Studio - 特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="see-also"></a>請參閱

- [Visual Studio 2017 中模型化的新功能](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps 與應用程式生命週期管理](/azure/devops/user-guide/devops-alm-overview)
