---
title: 視覺化程式碼
description: 瞭解如何使用 Visual Studio 中的視覺效果和模型工具來瞭解現有的程式碼，並描述您的應用程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a261589af027c76708a70631426d8033eb2ada63
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924234"
---
# <a name="visualize-code"></a>視覺化程式碼

您可以使用 Visual Studio 的視覺化和模型工具，以利了解現有的程式碼，並描述您的應用程式。 這可讓您以視覺化方式了解變更會如何影響程式碼，並幫助您評估因這些變更所導致的工作和風險。 例如：

- 若要了解程式碼中的關聯性，請以視覺化方式對應這些關聯性。

- 若要描述系統的架構，並讓程式碼與設計保持一致，請建立相依性圖表，並針對這些圖表驗證程式代碼。

- 若要描述類別結構，建立類別圖。

這些工具也可協助您更輕鬆地與專案相關人員通訊。

若要查看 Visual Studio 支援每項功能的版本，請參閱 [架構和模型工具的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

|狀況|文章|
|-|-|
|**了解程式碼及其關聯性：**<br /><br /> 對應特定程式碼片段之間的關聯性。<br /><br /> 查看整個方案的程式碼中的關聯性概觀。|- [將相依性對應到您的解決方案](../modeling/map-dependencies-across-your-solutions.md)<br />- [使用 code map 來對應用程式進行偵錯工具](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [使用 code map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [在調試時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**了解類別結構：**<br /><br /> 從程式碼建立類別圖，將專案中的類別結構視覺化。|[如何：將類別圖表新增至專案 (類別設計工具)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**描述高階系統設計和針對這項設計驗證程式碼：**<br /><br /> 藉由建立相依性圖表來描述高階系統設計及其預定的相依性。 針對此設計驗證程式碼，以確定程式碼中的相依性與設計保持一致。|- [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)<br />- [相依性圖表：參考](../modeling/layer-diagrams-reference.md)<br />- [相依性圖表：指導方針](../modeling/layer-diagrams-guidelines.md)<br />- [使用相依性圖表驗證程式代碼](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>另請參閱

- [情節：使用視覺化和模型功能變更設計](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [分析和模型架構](../modeling/analyze-and-model-your-architecture.md)
- [建立應用程式架構的模型](../modeling/model-your-app-s-architecture.md)
- [在開發程序中使用模型](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
