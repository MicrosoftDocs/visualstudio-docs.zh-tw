---
title: 視覺化程式碼
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 49f3c0e9cdd1feee0161c95d30bed03244d14e15
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47857623"
---
# <a name="visualize-code"></a>視覺化程式碼

您可以使用 Visual Studio 的視覺化和模型工具，以利了解現有的程式碼，並描述您的應用程式。 這可讓您以視覺化方式了解變更會如何影響程式碼，並幫助您評估因這些變更所導致的工作和風險。 例如：

- 若要了解程式碼中的關聯性，請以視覺化方式對應這些關聯性。

- 若要描述您的系統架構，並讓程式碼與設計一致，建立相依性圖表，並針對這些圖表驗證程式碼。

- 若要描述類別結構，建立類別圖。

這些工具也可協助您更輕鬆地與專案相關人員通訊。

若要查看哪些版本的 Visual Studio 支援每項功能，請參閱[architecture and modeling tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>請您指定選項。

|||
|-|-|
|**了解程式碼和其關聯性：**<br /><br /> 對應特定程式碼片段之間的關聯性。<br /><br /> 查看整個方案的程式碼中的關聯性概觀。|- [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)<br />- [使用 code map 偵錯應用程式](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [使用 code map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [偵錯時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**了解類別結構：**<br /><br /> 從程式碼建立類別圖，將專案中的類別結構視覺化。|[如何：將類別圖表新增至專案 (類別設計工具)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**描述高階系統設計，並針對這項設計驗證程式碼：**<br /><br /> 藉由建立相依性圖表，描述高階系統設計和其預定的相依性。 針對此設計驗證程式碼，以確定程式碼中的相依性與設計保持一致。|- [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)<br />- [相依性圖表： 參考](../modeling/layer-diagrams-reference.md)<br />- [相依性圖表： 指導方針](../modeling/layer-diagrams-guidelines.md)<br />- [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>另請參閱

- [情節：使用視覺化和模型功能變更設計](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [分析與模型結構](../modeling/analyze-and-model-your-architecture.md)
- [建立應用程式架構的模型](../modeling/model-your-app-s-architecture.md)
- [在開發程序中使用模型](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
