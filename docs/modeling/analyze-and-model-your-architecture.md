---
title: 架構分析 & 模型工具
description: 設計應用程式並為其建立模型，以確定您的應用程式符合架構需求。
ms.custom: SEO-VS-2020
ms.date: 06/04/2021
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 542b74e7d3bb73847303fa4215651eea7e110e91
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384872"
---
# <a name="analyze-and-model-your-architecture"></a>分析架構並製作架構模型

使用 Visual Studio 架構和模型工具來設計和模型化應用程式，以確定您的應用程式符合架構需求。

1. 使用 code map 和相依性圖表來 [視覺化](visualize-code.md) 程式碼結構、行為和關聯性，以更妥善瞭解現有的程式碼。
    - 藉由建立 **code map**，查看程式碼的組織和關聯性。 
    - 將組件、命名空間、類別、方法等之間的相依性視覺化。
    - 藉由建立相依性 **圖表** 來驗證程式代碼，找出程式碼與其設計之間的衝突。
    - [從程式碼建立類別圖表](../ide/class-designer/designing-and-viewing-classes-and-types.md)，以查看特定專案的類別結構和成員。
    - [使用 T4 範本產生](../modeling/code-generation-and-t4-text-templates.md) 文字，在範本內使用文字區塊和控制邏輯來產生以文字為基礎的檔案。 
    
1. 為您的團隊教育架構相依性的需求。

1. 請在開發過程中，於整個應用程式生命週期的不同詳細資料層級建立模型。

請參閱 [案例：使用視覺化和模型化來變更您的設計](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)。

## <a name="code-maps"></a>Code Map

Code map 是一種模型類型，可協助您查看程式碼中的組織和關聯性。

使用對應來檢查程式碼，讓您更瞭解其結構和其相依性、如何進行更新，以及預估建議的變更成本。

深入了解：
- [安裝架構程式碼工具](install-architecture-tools.md)
- [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)
- [使用 Code Map 偵錯您的應用程式](../modeling/use-code-maps-to-debug-your-applications.md)
- [使用 Code Map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="dependency-diagrams"></a>相依性圖表

相依性圖表可讓您將應用程式的結構定義為一組具有明確相依性的圖層或區塊。 即時驗證會顯示程式碼中的相依性與相依性圖表上所述相依性之間的衝突。

使用相依性圖表來： 
- 在應用程式存留期間，透過多次變更來穩固其結構。
- 在簽入變更到程式碼之前，探索意外的相依性衝突。

深入了解：
- [安裝架構程式碼工具](install-architecture-tools.md)
- [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)
- [相依性圖表︰參考](../modeling/layer-diagrams-reference.md)
- [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)

## <a name="domain-specific-language-dsl-models"></a>特定領域語言 (DSL) 模型

DSL 是您為特定目的所設計的標記法。 在 Visual Studio 中，它通常是圖形化的。

使用特定領域語言來： 
- 產生或設定應用程式的組件。 開發標記法和工具必須進行一些工作。 此結果會比自訂 UML 更適用您的定義域。
- 用於大型專案或產品線，其中在開發 DSL 及其工具方面的投資，可因這個模型用於多個專案而回收。

深入了解：
- [Modeling SDK for Visual Studio - 特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)


## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />架構和模型工具的版本支援

Visual Studio 可以在數個版本中使用。 並非所有這些都提供架構和模型工具的支援。 下表顯示每個工具的可用性。

|**功能**|**Enterprise edition**|**Professional edition**|**社區版**|
|-|-|-|-|
|**Code Map**|是|只支援讀取 code map、篩選 code map、加入新的泛型節點，以及從選取專案建立新的有向圖形。|-|
|**相依性圖表**|是|只支援讀取相依性圖表。|只支援讀取相依性圖表。|
| (DGML 圖表的 **導向圖形**) |是|是|是|
|**程式碼複製**|是|-|-|
