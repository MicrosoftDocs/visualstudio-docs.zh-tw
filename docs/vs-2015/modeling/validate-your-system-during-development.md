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
ms.openlocfilehash: a1beeef572282a642e4a989086ac0fd228409fec
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586277"
---
# <a name="validate-your-system-during-development"></a>在開發期間驗證您的系統
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 可協助您保持軟體與使用者需求和系統架構的一致性。

 若要查看支援每項功能的 Visual Studio 版本有哪些，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="key-tasks"></a>主要工作
 使用下列工作來驗證您的軟體。

|**工作**|**相關主題**|
|---------------|---------------------------|
|**請確定您的模型一致：**<br /><br /> 根據您專案使用及解譯模型的方式，不允許某些項目組合可能有所幫助。 例如，您可以限制 UML 類別，使其一律具有 [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]相容名稱。 您可以在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 擴充功能中定義類似此處所列的條件約束。|-   [驗證您的 UML 模型](../modeling/validate-your-uml-model.md)<br />-   [定義 UML 模型的驗證條件約束](../modeling/define-validation-constraints-for-uml-models.md)|
|**請確定您的軟體符合使用者的需求**：<br /><br /> 您可以使用需求和架構模型來協助您組織整理系統及其元件的測試。 這種做法可協助您確保測試對於使用者和其他專案關係人來說非常重要的需求，並可協助您在需求變更時快速地更新測試。|-   [從模型開發測試](../modeling/develop-tests-from-a-model.md)|
|**請確定您的軟體維持與系統的預定設計一致：**<br /><br /> 分層圖會描述應用程式元件之間的預定相依性。 在開發期間，您可以確認程式碼的實際相依性是否符合預定設計。|-   [從您的程式碼建立分層圖](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [使用圖層圖表驗證程式代碼](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>外部資源

|**類別**|**連結**|
|------------------|---------------|
|**影片**|![連結至影片](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9： Doug 七：程式碼瞭解和使用 Visual Studio 2010 的系統設計](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![連結至影片](../data-tools/media/playvideo.gif "PlayVideo")[頻道9：使用分層圖架構應用程式](https://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-5-Architecting-an-Application)<br /><br /> ![連結至影片](../data-tools/media/playvideo.gif "PlayVideo") [MSDN 如何系列：如何使用分層圖驗證程式代碼](https://msdn.microsoft.com/vstudio/gg501755)|
|**論壇**|-   [Visual Studio Visualization & Modeling Tools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Visualization & Modeling SDK (DSL 工具)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**網路**|-   [Visual Studio ALM + Team Foundation Server 部落格](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)|
|**技術文件和日誌**|[MSDN 架構中心](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>另請參閱
 [測試應用程式](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)[擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)[模型使用者需求](../modeling/model-user-requirements.md)[分析和模型化架構](../modeling/analyze-and-model-your-architecture.md)
