---
title: Messaging 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 250b213fc3bc54d67f55d41c5eb3aba7e3488cd4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62420182"
---
# <a name="messaging-activity-designers"></a>Messaging 活動設計工具
傳訊活動設計工具會用來建立及設定從 [!INCLUDE[indigo1](../includes/indigo1-md.md)] 應用程式內部傳送與接收 [!INCLUDE[wf](../includes/wf-md.md)] 訊息的傳訊活動。 [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] 導入五個傳訊活動，而且 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 提供兩個新的範本設計工具，可用來管理工作流程內的傳訊。 本節包含的主題以及下表所列的主題會提供如何使用 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 活動與範本設計工具的指引。  
  
## <a name="in-this-section"></a>本節內容  
  
|訊息活動|描述|  
|----------------------|-----------------|  
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|建立及設定 <xref:System.ServiceModel.Activities.CorrelationScope> 活動，該活動會使用 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件提供子系傳訊活動的隱含管理。|  
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|建立及設定 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活動，該活動會用來初始化相互關聯而不傳送或接收訊息。|  
|[Receive](../workflow-designer/receive-activity-designer.md)|建立及設定 <xref:System.ServiceModel.Activities.Receive> 活動，該活動會接收來自服務的訊息。|  
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|在 <xref:System.ServiceModel.Activities.Send> 活動內建立一對預先設定的 <xref:System.ServiceModel.Activities.ReceiveReply> 與 <xref:System.Activities.Statements.Sequence> 活動。|  
|[Send](../workflow-designer/send-activity-designer.md)|建立及設定 <xref:System.ServiceModel.Activities.Send> 活動，該活動會將訊息傳送至服務。|  
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|在 <xref:System.ServiceModel.Activities.Receive> 活動內建立一對預先設定的 <xref:System.ServiceModel.Activities.SendReply> 與 <xref:System.Activities.Statements.Sequence> 活動。|  
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|建立及設定 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動，該活動可讓異動流動至工作流程中。|  
  
## <a name="reference"></a>參考資料  
 <xref:System.Activities.Activity>  
  
 <xref:System.ServiceModel.Activities.CorrelationScope>  
  
 <xref:System.ServiceModel.Activities.Receive>  
  
 <xref:System.ServiceModel.Activities.Send>  
  
 <xref:System.ServiceModel.Activities.ReceiveReply>  
  
 <xref:System.ServiceModel.Activities.SendReply>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>  
  
## <a name="related-sections"></a>相關章節  
 如需其他活動設計工具類型的資訊，請參閱下列主題。  
  
 [控制流程](../workflow-designer/control-flow-activity-designers.md)  
  
 [使用活動設計工具](../workflow-designer/using-the-activity-designers.md)  
  
 [流程圖](../workflow-designer/flowchart-activity-designers.md)  
  
 [執行階段](../workflow-designer/runtime-activity-designers.md)  
  
 [Primitives](../workflow-designer/primitives-activity-designers.md)  
  
 [異動](../workflow-designer/transaction-activity-designers.md)  
  
 [集合](../workflow-designer/collection-activity-designers.md)  
  
 [錯誤處理](../workflow-designer/error-handling-activity-designers.md)  
  
## <a name="external-resources"></a>外部資源  
 [使用活動設計工具](../workflow-designer/using-the-activity-designers.md)