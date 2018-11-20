---
title: 視覺化程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 071048fba8d3663639747ea35dbae4375d101c26
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738923"
---
# <a name="visualize-code"></a>視覺化程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 Visual Studio 的視覺化和模型工具，以利了解現有的程式碼，並描述您的應用程式。 這可讓您以視覺化方式了解變更會如何影響程式碼，並幫助您評估因這些變更所導致的工作和風險。 例如：  
  
- 若要了解程式碼中的關聯性，請以視覺化方式對應這些關聯性。  
  
- 若要描述系統架構，並讓程式碼保持與設計一致，請針對這些圖表建立分層圖並驗證程式碼。  
  
- 若要描述類別結構，建立類別圖。  
  
- 若要建立系統各個層面的模型及溝通渠道，請繪製整合模組化語言 (UML) 圖表。 例如，您可以建立系統元件、類型、互動及處理程序的模型。  
  
  這些工具也可協助您更輕鬆地與專案相關人員通訊。 例如，您可以使用 UML 類別圖建立常用詞彙，與專案的專案關係人、使用者和小組成員討論系統。  
  
  若要查看支援各項功能的 Visual Studio 版本有哪些，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
|||  
|-|-|  
|**了解程式碼和其關聯性：**<br /><br /> 對應特定程式碼片段之間的關聯性。<br /><br /> 查看整個方案的程式碼中的關聯性概觀。<br /><br /> **注意**：在本版 Visual Studio 中，會以 *Code Map* 一詞取代 *「相依性圖形」*(Dependency Graph)。|-   [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)<br />-   [使用 code map 偵錯應用程式](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [使用 code map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [偵錯時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|  
|**了解類別結構：**<br /><br /> 從程式碼建立類別圖，將專案中的類別結構視覺化。|[如何：將類別圖表新增至專案 (類別設計工具)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|  
|**描述高階系統設計，並針對這項設計驗證程式碼：**<br /><br /> 藉由建立分層圖，描述高階系統設計及其預計相依性。 針對此設計驗證程式碼，以確定程式碼中的相依性與設計保持一致。|-   [從您的程式碼建立分層圖](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [分層圖： 參考](../modeling/layer-diagrams-reference.md)<br />-   [分層圖： 方針](../modeling/layer-diagrams-guidelines.md)<br />-   [使用分層圖驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)|  
|**溝通使用者需求和架構：**<br /><br /> 藉由繪製下列 UML 圖表：活動、元件、類別、順序和使用案例，建立使用者需求和軟體系統架構的模型。|-   [建立應用程式模型](../modeling/create-models-for-your-app.md)<br />-   [模型使用者需求](../modeling/model-user-requirements.md)<br />-   [您的應用程式架構模型](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="external-resources"></a>外部資源  
  
|**分類**|**Links**|  
|------------------|---------------|  
|**論壇**|-   [Visual Studio Visualization & Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL 工具)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**部落格**|[Visual Studio ALM + Team Foundation Server 部落格](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**技術文件和日誌**|[MSDN 架構論壇](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>另請參閱  
 [情節： 變更您的設計使用視覺化和模型](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)   
 [分析並製作架構模型](../modeling/analyze-and-model-your-architecture.md)   
 [建立應用程式模型](../modeling/create-models-for-your-app.md)   
 [模型使用者需求](../modeling/model-user-requirements.md)   
 [您的應用程式架構模型](../modeling/model-your-app-s-architecture.md)   
 [在開發程序中使用模型](../modeling/use-models-in-your-development-process.md)



