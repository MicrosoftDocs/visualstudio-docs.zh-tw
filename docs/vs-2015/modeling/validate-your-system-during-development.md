---
title: 在開發期間驗證您的系統 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4fec3595ba7886f5ba979c35e9441ab108174726
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301347"
---
# <a name="validate-your-system-during-development"></a>在開發期間驗證您的系統
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 可協助您保持軟體與使用者需求和系統架構的一致性。

 若要查看哪些版本的 Visual Studio 支援這些功能之每一項，請參閱[架構和模型工具的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="key-tasks"></a>主要工作
 使用下列工作來驗證您的軟體。

|**工作**|**相關主題**|
|---------------|---------------------------|
|**請確定您的模型一致：**<br /><br /> 根據您專案使用及解譯模型的方式，不允許某些項目組合可能有所幫助。 例如，您可以限制 UML 類別，使其一律具有 [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]相容名稱。 您可以在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 擴充功能中定義類似此處所列的條件約束。|-   [驗證您的 UML 模型](../modeling/validate-your-uml-model.md)<br />-   [定義 UML 模型的驗證條件約束](../modeling/define-validation-constraints-for-uml-models.md)|
|**請確定您的軟體符合使用者的需求**：<br /><br /> 您可以使用需求和架構模型來協助您組織整理系統及其元件的測試。 這種做法可協助您確保測試對於使用者和其他專案關係人來說非常重要的需求，並可協助您在需求變更時快速地更新測試。|-   [從模型開發測試](../modeling/develop-tests-from-a-model.md)|
|**請確定您的軟體維持與系統的預定設計一致：**<br /><br /> 分層圖會描述應用程式元件之間的預定相依性。 在開發期間，您可以確認程式碼的實際相依性是否符合預定設計。|-   [從您的程式碼建立分層圖](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [使用圖層圖表驗證程式代碼](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>外部資源

|**分類**|**Links**|
|------------------|---------------|
|**影片**|![連結至影片](../data-tools/media/playvideo.gif "連結 playvideo") [Channel 9： Doug 七：程式碼瞭解和使用 Visual Studio 2010 的系統設計](https://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![連結至影片](../data-tools/media/playvideo.gif "PlayVideo")[頻道9：使用分層圖架構應用程式](https://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![連結至影片](../data-tools/media/playvideo.gif "PlayVideo") [MSDN 如何系列：如何使用分層圖驗證程式代碼](https://go.microsoft.com/fwlink/?LinkID=214405)|
|**論壇**|-   [Visual Studio Visualization & Modeling Tools](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL 工具)](https://go.microsoft.com/fwlink/?LinkId=184721)|
|**部落格**|-   [Visual Studio ALM + Team Foundation Server 部落格](https://go.microsoft.com/fwlink/?LinkID=201340)|
|**技術文件和日誌**|[MSDN 架構中心](https://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>另請參閱
 [測試應用程式](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)[擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)[模型使用者需求](../modeling/model-user-requirements.md)[分析和模型化架構](../modeling/analyze-and-model-your-architecture.md)
