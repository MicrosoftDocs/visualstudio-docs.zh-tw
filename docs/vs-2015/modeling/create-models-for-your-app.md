---
title: 建立應用程式模型 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.commentlink.properties
- vs.teamarch.UMLModelExplorer.dependency
- vs.teamarch.UMLModelExplorer.commentlink
- vs.teamarch.common.dependency.properties
- Microsoft.VisualStudio.Uml.Diagrams.CommentShape.IsTransparent
- vs.teamarch.common.comment.properties
- vs.teamarch.UMLModelExplorer.comment
helpviewer_keywords:
- diagrams - modeling, sequence
- software design
- diagrams - modeling, use case
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML model
- diagrams - modeling, UML use case
- diagrams - modeling, class
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- software modeling
- diagrams - modeling, UML sequence
- UML
- diagrams - modeling, UML
- diagrams - modeling, layer
- software, designing
- diagrams - modeling, UML class
- software, modeling
- UML diagrams
ms.assetid: b69d9d91-c7e7-4dee-8eb6-706076eecb85
caps.latest.revision: 60
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9e3aa389441914121493148ecb8fa45b9f86beed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745132"
---
# <a name="create-models-for-your-app"></a>建立應用程式模型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

模型圖表可幫助您了解、釐清和溝通程式碼和軟體必須支援之使用者需求的想法。 例如，您可以使用整合模組化語言 (UML) 之使用案例圖、活動圖、類別圖和循序圖描述和溝通使用者需求。 若要描述和溝通系統的功能，您可以使用 UML 元件圖、類別圖、活動圖和循序圖。  
  
 請參閱[Channel 9 影片： 透過模型改善結構](http://go.microsoft.com/fwlink/?LinkID=252078)。  
  
 您可在這個版本中建立下列 UML 圖表：  
  
|**圖表**|**顯示**|  
|-----------------|---------------|  
|[UML 活動圖表：參考](../modeling/uml-activity-diagrams-reference.md)|商務程序中動作與參與者之間的工作流程|  
|[UML 元件圖表：參考](../modeling/uml-component-diagrams-reference.md)|系統、其介面、通訊埠和關聯性的元件|  
|[UML 類別圖表：參考](../modeling/uml-class-diagrams-reference.md)|系統及其關聯性中用來儲存和交換資料的類型|  
|[UML 順序圖表：參考](../modeling/uml-sequence-diagrams-reference.md)|物件、元件、系統或行動之間的互動順序|  
|[UML 使用案例圖：參考](../modeling/uml-use-case-diagrams-reference.md)|系統支援的使用者目標和工作|  
  
 若要查看哪些版本的 Visual Studio 支援每種圖表類型，請參閱[architecture and modeling tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
 若要將系統或現有程式碼的架構視覺化，請建立下列圖表：  
  
|**圖表**|**顯示**|  
|-----------------|---------------|  
|[分層圖：方針](../modeling/layer-diagrams-guidelines.md)<br /><br /> [分層圖：參考](../modeling/layer-diagrams-reference.md)|系統的高階架構|  
|Code Map<br /><br /> [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)<br /><br /> [使用 Code Map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)|現有程式碼中的相依性和其他關聯性|  
|程式碼產生的類別圖<br /><br /> [使用類別圖表 (類別設計工具)](../ide/working-with-class-diagrams-class-designer.md)|.NET 程式碼中的類型及其關聯性|  
  
## <a name="common-tasks"></a>一般工作  
  
|**主題**|**Task**|  
|---------------|--------------|  
|[建立 UML 模型專案和圖表](../modeling/create-uml-modeling-projects-and-diagrams.md)|**建立模型**並加入圖表。|  
|[編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)|**繪製圖表**藉以編輯此模型。|  
|[定義套件和命名空間](../modeling/define-packages-and-namespaces.md)|**建立套件**將模型分成不同的小組成員可以處理的單位。|  
|[從 UML 類別圖表產生程式碼](../modeling/generate-code-from-uml-class-diagrams.md)|**從類別圖產生 C# 程式碼**啟動您的實作。|  
|[使用設定檔和造型自訂您的模型](../modeling/customize-your-model-with-profiles-and-stereotypes.md)|**自訂模型項目**使用造型，來針對特定用途擴充標準 UML 模型項目。|  
|[連結模型項目和工作項目](../modeling/link-model-elements-and-work-items.md)|**建立模型項目和工作項目之間的連結**以協助您追蹤工作、 測試案例、 bug、 需求、 問題或其他類型的工作，會與特定模型部分相關聯。|  
|[將圖表匯出為影像](../modeling/export-diagrams-as-images.md)|**儲存您的模型和圖表**，因此您可以與其他使用者共用，包括那些不會使用[!INCLUDE[vsUltShort](../includes/vsultshort-md.md)]。|  
  
## <a name="related-tasks"></a>相關工作  
  
|**主題**|**Task**|  
|---------------|--------------|  
|[視覺化程式碼](../modeling/visualize-code.md)|建立 Code Map 和分層圖，藉此深入了解不熟悉的程式碼。|  
|[模型使用者需求](../modeling/model-user-requirements.md)|使用模型來釐清和溝通使用者的需求。|  
|[建立應用程式架構的模型](../modeling/model-your-app-s-architecture.md)|使用模型描述系統的整體結構和行為，以及確保其符合使用者的需求。|  
|[在開發期間驗證您的系統](../modeling/validate-your-system-during-development.md)|確認您的軟體符合使用者的需求以及系統的整體架構。|  
|[在開發程序中使用模型](../modeling/use-models-in-your-development-process.md)<br /><br /> [在 Agile 開發中使用模型](http://msdn.microsoft.com/en-us/592ac27c-3d3e-454a-9c38-b76658ed137f)|使用模型可幫助您在開發期間了解和變更系統。|  
|[建構模型方案](../modeling/structure-your-modeling-solution.md)|組織大型或中型專案中的模型。|  
  
## <a name="external-resources"></a>外部資源  
  
|**分類**|**Links**|  
|------------------|---------------|  
|**論壇**|-   [Visual Studio Visualization & Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL 工具)](http://go.microsoft.com/fwlink/?LinkId=184721)|



