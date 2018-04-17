---
title: 初始化相互關聯對話方塊 |Microsoft 文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aac62d4439c2280e977ef929c79bb103348c170a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="initialize-correlation-dialog-box"></a>初始化相互關聯對話方塊

**初始化相互關聯**對話方塊用於在 Windows 工作流程設計工具編輯<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>屬性<xref:System.ServiceModel.Activities.InitializeCorrelation>活動。 如需詳細資訊，請參閱[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)主題。

 下表描述的使用者介面 (UI) 項目**初始化相互關聯** 對話方塊。

|UI 項目|描述|
|----------------|-----------------|
|**相互關聯**|要初始化之相互關聯的 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件。|
|**在初始化**|索引鍵/值組，其包含要初始化的資料。 這會對應至 <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> 屬性。 有效的索引鍵/值組的範例就是名為"OrderID"與名為 OrderID 的變數配對的金鑰。|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>若要啟動初始化相互關聯對話方塊

-   按一下**檢視**上**InitializeCorrelation**活動設計工具或選取<xref:System.ServiceModel.Activities.InitializeCorrelation>中的活動[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]然後按一下省略符號按鈕旁的 <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>中的屬性屬性方格中。

## <a name="see-also"></a>另請參閱

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)