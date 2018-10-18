---
title: CorrelationScope 活動設計工具 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 4a46c50a888808932d071622d83b871761977259
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173195"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope 活動設計工具
**CorrelationScope**活動設計工具會用來建立及設定<xref:System.ServiceModel.Activities.CorrelationScope>活動，以提供使用的子系傳訊活動的隱含管理<xref:System.ServiceModel.Activities.CorrelationHandle>物件。  
  
## <a name="the-correlationscope-activity"></a>CorrelationScope 活動  
 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 屬性會指定用來管理子系傳訊活動的 <xref:System.ServiceModel.Activities.CorrelationHandle>。 包含在 <xref:System.ServiceModel.Activities.Send> 中的 <xref:System.ServiceModel.Activities.Receive> 與 <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> 活動，會設定為使用包含之 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 活動的 <xref:System.ServiceModel.Activities.CorrelationScope> 屬性來執行相互關聯。  
  
### <a name="using-the-correlationscope-activity-designer"></a>使用 CorrelationScope 活動設計工具  
 **CorrelationScope**活動設計工具可在**Messaging**分類**工具箱**，即可存取的哪一個**工具箱**  索引標籤上的左側[!INCLUDE[wfd2](../includes/wfd2-md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **CorrelationScope**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面。 這會建立<xref:System.ServiceModel.Activities.CorrelationScope>活動，具有預設值**DisplayName** CorrelationScope。 <xref:System.Activities.Activity.DisplayName%2A>可以的標頭中編輯**CorrelationScope**活動設計工具或**DisplayName**方塊**屬性**視窗。  
  
 若要指定<xref:System.ServiceModel.Activities.CorrelationHandle>由子系傳訊活動，按一下旁邊的省略符號按鈕**CorrelatesWith**欄位中**屬性**視窗，以顯示**運算式編輯器**  對話方塊。 這個屬性也可以在活動設計工具介面上設定。  
  
 範圍內的相互關聯的活動由卸除其設計工具內**主體**方塊內**CorrelationScope**設計工具。  
  
### <a name="the-correlationscope-properties"></a>CorrelationScope 屬性  
 下表顯示 <xref:System.ServiceModel.Activities.CorrelationScope> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在編輯**屬性**視窗或在[!INCLUDE[wfd2](../includes/wfd2-md.md)]設計工具介面上，且經常在。  
  
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