---
title: CorrelatesOn 定義對話方塊 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2a9a6f7ec6b8bf246ebfc03c166780b229e1aee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656944"
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn 定義對話方塊
在 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 中使用 [ **CorrelatesOn** ] 對話方塊來編輯 <xref:System.ServiceModel.Activities.Receive> 活動的 <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> 屬性。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][接收](../workflow-designer/receive-activity-designer.md)主題。

 <xref:System.ServiceModel.Activities.Receive> 活動之間的相互關聯，會指定某個工作流程中不同服務作業彼此之間的關係。

 下表描述 [ **CorrelatesOn** ] 對話方塊的使用者介面（UI）元素。

|UI 項目|描述|
|----------------|-----------------|
|**CorrelatesWith**|用來路由訊息到適當工作流程執行個體的 <xref:System.ServiceModel.Activities.CorrelationHandle>。|
|**XPath 查詢**|配對的索引鍵/值，其中包含用來從傳入訊息擷取相互關聯資料的查詢。 這會對應至 <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> 屬性。 XPath 查詢會包含在 <xref:System.ServiceModel.MessageQuerySet> 物件中。|

## <a name="to-launch-the-correlateson-dialog-box"></a>若要啟動 CorrelatesOn 對話方塊
 [ **Receive** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上通常用來放置活動的任一處。 這會建立一個 <xref:System.ServiceModel.Activities.Receive> 活動，具有 Receive 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 選取 [ **Receive** ] 活動設計工具，然後按一下屬性方格中 [ **CorrelatesOn** ] 屬性的（集合）文字旁邊的省略號按鈕，就會出現 [ **CorrelatesOn 定義**] 對話方塊。

## <a name="see-also"></a>請參閱
 <xref:System.ServiceModel.Activities.Receive>[新增 CorrelationInitializers 對話方塊](../workflow-designer/add-correlationinitializers-dialog-box.md)[[初始化相互關聯] 對話方塊](../workflow-designer/initialize-correlation-dialog-box.md)