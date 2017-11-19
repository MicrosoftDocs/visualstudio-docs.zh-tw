---
title: "CorrelationScope 活動設計工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3e6e745e470c5e5b5a279f460198729bd9429ccc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope 活動設計工具
**CorrelationScope**活動設計工具用來建立及設定<xref:System.ServiceModel.Activities.CorrelationScope>活動所提供的子系傳訊活動使用隱含管理<xref:System.ServiceModel.Activities.CorrelationHandle>物件。  
  
## <a name="the-correlationscope-activity"></a>CorrelationScope 活動  
 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 屬性會指定用來管理子系傳訊活動的 <xref:System.ServiceModel.Activities.CorrelationHandle>。 包含在 <xref:System.ServiceModel.Activities.Send> 中的 <xref:System.ServiceModel.Activities.Receive> 與 <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> 活動，會設定為使用包含之 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 活動的 <xref:System.ServiceModel.Activities.CorrelationScope> 屬性來執行相互關聯。  
  
### <a name="using-the-correlationscope-activity-designer"></a>使用 CorrelationScope 活動設計工具  
 **CorrelationScope**活動設計工具位於**傳訊**分類**工具箱**，即可存取的哪一個**工具箱**  索引標籤上的左半部[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **CorrelationScope**活動設計工具可以從拖曳**工具箱**，置放到上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面。 這會建立<xref:System.ServiceModel.Activities.CorrelationScope>預設值的活動**DisplayName** CorrelationScope。 <xref:System.Activities.Activity.DisplayName%2A>可編輯的標頭中**CorrelationScope**活動設計工具或在**DisplayName**方塊**屬性**視窗。  
  
 若要指定<xref:System.ServiceModel.Activities.CorrelationHandle>子傳訊活動使用，請按一下旁邊的橢圓形按鈕**CorrelatesWith**欄位**屬性**視窗，以顯示**運算式編輯器**  對話方塊。 這個屬性也可以在活動設計工具介面上設定。  
  
 指定範圍內的相互關聯的活動，放進其設計工具內**主體**方塊內**CorrelationScope**設計工具。  
  
### <a name="the-correlationscope-properties"></a>CorrelationScope 屬性  
 下表顯示 <xref:System.ServiceModel.Activities.CorrelationScope> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以編輯在**屬性**視窗或在[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]設計工具介面上，且通常兩者中。  
  
|屬性名稱|必要項|使用方式|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> 活動可選用的易記名稱。|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|指定用來管理子系傳訊活動的 <xref:System.ServiceModel.Activities.CorrelationHandle>。 如果沒有設定這個屬性，<xref:System.ServiceModel.Activities.CorrelationScope> 會自動建立隱含 <xref:System.ServiceModel.Activities.CorrelationHandle>。|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|指定相互關聯範圍內的活動。|  
  
## <a name="see-also"></a>另請參閱  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [接收](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [傳送](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)