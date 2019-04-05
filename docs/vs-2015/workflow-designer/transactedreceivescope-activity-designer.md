---
title: TransactedReceiveScope 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f4864a19cf48b468abed90e120e4924237653cec
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945494"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope 活動設計工具
**TransactedReceiveScope**設計工具會用來建立及設定<xref:System.ServiceModel.Activities.TransactedReceiveScope>活動。  
  
## <a name="the-transactedreceivescope-activity"></a>TransactedReceiveScope 活動  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動可讓您將交易流動至工作流程或發送器建立的服務端交易。  
  
### <a name="using-the-transactedreceivescope-activity-designer"></a>使用 TransactedReceiveScope 活動設計工具  
 **TransactedReceiveScope**活動設計工具位於**Messaging**類別**工具箱**，即可存取的哪一個**工具箱**索引標籤上[!INCLUDE[wfd2](../includes/wfd2-md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **TransactedReceiveScope**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面任一處通常用來放置活動。 這會建立<xref:System.ServiceModel.Activities.TransactedReceiveScope>活動，具有預設值**DisplayName** TransactedReceiveScope。 <xref:System.Activities.Activity.DisplayName%2A>可以的標頭中編輯**TransactedReceiveScope**活動設計工具或**DisplayName**屬性方格的方塊。  
  
 **TransactedReceiveScope**設計師 」 包含**要求**並**主體**方塊。 這些會用來設定 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> 屬性，而該屬性會指定 <xref:System.ServiceModel.Activities.Receive> 活動與 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 屬性，而此屬性再指定某個其他 <xref:System.Activities.Activity>。 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> 會建立異動。 然後，此異動會變成 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 範圍的環境異動，於是此範圍內的任何活動會在此異動的內部執行。  
  
### <a name="the-transactedreceivescope-properties"></a>TransactedReceiveScope 屬性  
 下表顯示 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 屬性，並且描述屬性在設計工具中的使用方式。 這些 <xref:System.Activities.Activity.DisplayName%2A> 屬性可以在屬性方格中或在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上編輯，但其他屬性必須在設計工具介面上編輯。  
  
|屬性名稱|必要|使用量|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動可選用的易記名稱。 預設為 TransactedReceiveScope。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 名稱並非絕對必要，但建議您盡量使用顯示名稱。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|卸除<xref:System.ServiceModel.Activities.Receive>活動**要求**活動設計工具介面上的區塊。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|卸除<xref:System.Activities.Activity>成**主體**活動設計工具介面上的區塊。|  
  
## <a name="see-also"></a>另請參閱  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [接收](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [傳送](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)