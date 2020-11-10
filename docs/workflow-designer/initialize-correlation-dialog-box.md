---
title: 工作流程設計工具-初始化相互關聯對話方塊
description: 瞭解如何使用工作流程設計工具中的 [初始化相互關聯] 對話方塊來編輯 InitializeCorrelation 活動的 CorrelationData 屬性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a35911fef39315580f402e174b0f32d443a33cf
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437797"
---
# <a name="initialize-correlation-dialog-box"></a>初始化相互關聯對話方塊

[ **初始化相互關聯** ] 對話方塊會在工作流程設計工具中用來編輯 <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> 活動的屬性 <xref:System.ServiceModel.Activities.InitializeCorrelation> 。 如需詳細資訊，請參閱 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)。

下表說明 [ **初始化相互關聯** ] 對話方塊的使用者介面 (UI) 元素：

|UI 元素|描述|
|-|-----------------|
|**相互關聯**|要初始化之相互關聯的 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件。|
|**開啟初始化**|索引鍵/值組，其包含要初始化的資料。 這個值會對應至 <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> 屬性。 有效的索引鍵/值組範例是名為 "Id" 的索引鍵，與名為 [訂單識別碼] 的變數配對。|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>若要啟動初始化相互關聯對話方塊

按一下 [ **InitializeCorrelation** ] 活動設計工具上的 [ **View** ]，或選取 <xref:System.ServiceModel.Activities.InitializeCorrelation> 工作流程設計工具中的活動。 然後，按一下 <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> 屬性方格中屬性旁的省略號按鈕。

## <a name="see-also"></a>請參閱

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
