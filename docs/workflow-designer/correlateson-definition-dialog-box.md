---
title: "CorrelatesOn 定義對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 07e028a3ac5018c8a9866a6aee061d679cff74a9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn 定義對話方塊
**CorrelatesOn**對話方塊用於[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]編輯<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>屬性<xref:System.ServiceModel.Activities.Receive>活動。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][接收](../workflow-designer/receive-activity-designer.md)主題。  
  
 <xref:System.ServiceModel.Activities.Receive> 活動之間的相互關聯，會指定某個工作流程中不同服務作業彼此之間的關係。  
  
 下表描述的使用者介面 (UI) 項目**CorrelatesOn**  對話方塊。  
  
|UI 項目|描述|  
|----------------|-----------------|  
|**CorrelatesWith**|用來路由訊息到適當工作流程執行個體的 <xref:System.ServiceModel.Activities.CorrelationHandle>。|  
|**XPath 查詢**|配對的索引鍵/值，其中包含用來從傳入訊息擷取相互關聯資料的查詢。 這會對應至 <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> 屬性。 XPath 查詢會包含在 <xref:System.ServiceModel.MessageQuerySet> 物件中。|  
  
## <a name="to-launch-the-correlateson-dialog-box"></a>若要啟動 CorrelatesOn 對話方塊  
 **接收**活動設計工具可以從拖曳**工具箱**，置放到上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面任一處活動通常放置。 這會建立一個 <xref:System.ServiceModel.Activities.Receive> 活動，具有 Receive 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 選取**接收**活動設計工具，然後按一下省略符號按鈕 （集合） 文字旁邊**CorrelatesOn**屬性方格中的**CorrelatesOn 定義**對話方塊出現。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ServiceModel.Activities.Receive>   
 [加入 CorrelationInitializers 對話方塊](../workflow-designer/add-correlationinitializers-dialog-box.md)   
 [加入相互關聯對話方塊](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [初始化相互關聯對話方塊](../workflow-designer/initialize-correlation-dialog-box.md)