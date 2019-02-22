---
title: 工作流程設計工具-初始化相互關聯對話方塊
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fab86b39cd927d516bc627630a29feee1698daa
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919881"
---
# <a name="initialize-correlation-dialog-box"></a>初始化相互關聯對話方塊

**初始化相互關聯** 對話方塊中編輯時，會在工作流程設計工具<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>屬性<xref:System.ServiceModel.Activities.InitializeCorrelation>活動。 如需詳細資訊，請參閱 < [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)。

下表描述的使用者介面 (UI) 項目**初始化相互關聯** 對話方塊中：

|UI 項目|描述|
|-|-----------------|
|**相互關聯**|要初始化之相互關聯的 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件。|
|**在初始化**|索引鍵/值組，其包含要初始化的資料。 這個值會對應到<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>屬性。 有效的索引鍵/值組的範例是名為"OrderID"與名為 OrderID 的變數配對的索引鍵。|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>若要啟動初始化相互關聯對話方塊

按一下 **檢視**上**InitializeCorrelation**活動設計工具上或選取<xref:System.ServiceModel.Activities.InitializeCorrelation>工作流程設計工具中的活動。 然後，按一下省略符號按鈕旁<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>屬性方格中的屬性。

## <a name="see-also"></a>另請參閱

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)