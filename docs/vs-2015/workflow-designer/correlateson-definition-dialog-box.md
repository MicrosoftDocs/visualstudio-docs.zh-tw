---
title: CorrelatesOn 定義對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 01af296f4cb7dcaa7785438c54527337c110f609
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487187"
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn 定義對話方塊
**CorrelatesOn**  對話方塊會在[!INCLUDE[wfd1](../includes/wfd1-md.md)]編輯<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>屬性<xref:System.ServiceModel.Activities.Receive>活動。 [!INCLUDE[crdefault](../includes/crdefault-md.md)] [接收](../workflow-designer/receive-activity-designer.md)主題。  
  
 <xref:System.ServiceModel.Activities.Receive> 活動之間的相互關聯，會指定某個工作流程中不同服務作業彼此之間的關係。  
  
 下表描述的使用者介面 (UI) 項目**CorrelatesOn**  對話方塊。  
  
|UI 項目|描述|  
|----------------|-----------------|  
|**CorrelatesWith**|用來路由訊息到適當工作流程執行個體的 <xref:System.ServiceModel.Activities.CorrelationHandle>。|  
|**XPath 查詢**|配對的索引鍵/值，其中包含用來從傳入訊息擷取相互關聯資料的查詢。 這會對應至 <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> 屬性。 XPath 查詢會包含在 <xref:System.ServiceModel.MessageQuerySet> 物件中。|  
  
## <a name="to-launch-the-correlateson-dialog-box"></a>若要啟動 CorrelatesOn 對話方塊  
 **接收**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面任一處通常用來放置活動。 這會建立一個 <xref:System.ServiceModel.Activities.Receive> 活動，具有 Receive 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 選取 **接收**活動設計工具 和 （集合） 文字旁邊的省略符號按鈕的 click **CorrelatesOn**屬性的屬性方格中**CorrelatesOn 定義**出現的對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Activities.Receive>   
 [[新增 CorrelationInitializers] 對話方塊](../workflow-designer/add-correlationinitializers-dialog-box.md)   
 [加入相互關聯對話方塊](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [初始化相互關聯對話方塊](../workflow-designer/initialize-correlation-dialog-box.md)