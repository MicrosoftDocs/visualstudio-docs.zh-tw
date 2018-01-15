---
title: "將程式碼視覺化 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d3272195d1099ea851cbabf32c845ce2d46a697c
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="visualize-code"></a>視覺化程式碼
您可以使用 Visual Studio 的視覺化和模型工具，以利了解現有的程式碼，並描述您的應用程式。 這可讓您以視覺化方式了解變更會如何影響程式碼，並幫助您評估因這些變更所導致的工作和風險。 例如：  
  
-   若要了解程式碼中的關聯性，請以視覺化方式對應這些關聯性。  
  
-   若要描述您的系統架構，並讓程式碼與設計一致，建立相依性圖表，並針對這些圖表驗證程式碼。  
  
-   若要描述類別結構，建立類別圖。  
  
 這些工具也可協助您更輕鬆地與專案相關人員通訊。 
  
 若要查看支援各項功能的 Visual Studio 版本有哪些，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
|||  
|-|-|  
|**了解程式碼以及其關聯性：**<br /><br /> 對應特定程式碼片段之間的關聯性。<br /><br /> 查看整個方案的程式碼中的關聯性概觀。<br /><br /> **注意**：在本版 Visual Studio 中，會以 *Code Map* 一詞取代 *「相依性圖形」*(Dependency Graph)。|-   [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)<br />-   [使用 code map 偵錯應用程式](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [使用 code map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [偵錯時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|  
|**了解類別結構：**<br /><br /> 從程式碼建立類別圖，將專案中的類別結構視覺化。|[如何：將類別圖表新增至專案 (類別設計工具)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|  
|**會描述高層級的系統設計和驗證此設計的程式碼：**<br /><br /> 藉由建立相依性圖表中說明的高層級的系統設計和預期的相依性。 針對此設計驗證程式碼，以確定程式碼中的相依性與設計保持一致。|-   [從程式碼中建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [相依性圖表： 參考](../modeling/layer-diagrams-reference.md)<br />-   [相依性圖表： 指導方針](../modeling/layer-diagrams-guidelines.md)<br />-   [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>外部資源  
  
|**分類**|**Links**|  
|------------------|---------------|  
|**論壇**|-   [Visual Studio Visualization & Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL 工具)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**部落格**|[Visual Studio ALM + Team Foundation Server 部落格 (英文)](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**技術文件和日誌**|[MSDN 架構論壇](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>請參閱  
 [案例： 變更您的設計使用視覺化和模型](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)   
 [分析和模型架構](../modeling/analyze-and-model-your-architecture.md)   
 [您的應用程式架構模型](../modeling/model-your-app-s-architecture.md)   
 [在開發程序中使用模型](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
