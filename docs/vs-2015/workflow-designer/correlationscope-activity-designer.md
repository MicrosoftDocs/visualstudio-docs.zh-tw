---
title: CorrelationScope 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6ffcfd63d60ab6f085b5cb2a793e8bf17a50d8e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656917"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope 活動設計工具
**CorrelationScope**活動設計工具是用來建立及設定 <xref:System.ServiceModel.Activities.CorrelationScope> 活動，此活動會使用物件來提供子訊息活動的隱含管理 <xref:System.ServiceModel.Activities.CorrelationHandle> 。

## <a name="the-correlationscope-activity"></a>CorrelationScope 活動
 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 屬性會指定用來管理子系傳訊活動的 <xref:System.ServiceModel.Activities.CorrelationHandle>。 包含在 <xref:System.ServiceModel.Activities.Send> 中的 <xref:System.ServiceModel.Activities.Receive> 與 <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> 活動，會設定為使用包含之 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 活動的 <xref:System.ServiceModel.Activities.CorrelationScope> 屬性來執行相互關聯。

### <a name="using-the-correlationscope-activity-designer"></a>使用 CorrelationScope 活動設計工具
 [ **CorrelationScope** ] 活動設計工具位於 [**工具箱**] 的 [**訊息**] 類別中，若要存取，請按一下 (左側的 [**工具箱**] 索引標籤， [!INCLUDE[wfd2](../includes/wfd2-md.md)] 也可以從 [ **VIEW** ] 功能表選取 [**工具列**]，或按 CTRL + ALT + X。 ) 

 [ **CorrelationScope** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上。 這會建立一個 <xref:System.ServiceModel.Activities.CorrelationScope> 活動，具有 CorrelationScope 的預設 **DisplayName** 。 <xref:System.Activities.Activity.DisplayName%2A>可以在 [ **CorrelationScope** ] 活動設計工具的標頭中編輯，或是在 [**屬性**] 視窗的 [ **DisplayName** ] 方塊中編輯。

 若要指定 <xref:System.ServiceModel.Activities.CorrelationHandle> 子訊息活動所使用的，請在 [**屬性**] 視窗中，按一下 [ **CorrelatesWith** ] 欄位旁邊的省略號按鈕，以顯示 [**運算式編輯器**] 對話方塊。 這個屬性也可以在活動設計工具介面上設定。

 在相互關聯範圍內的活動，是藉由在**CorrelationScope**設計工具內**的 [內**文] 方塊中放置其設計工具來指定。

### <a name="the-correlationscope-properties"></a>CorrelationScope 屬性
 下表顯示 <xref:System.ServiceModel.Activities.CorrelationScope> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在 [ **屬性** ] 視窗中或在設計工具介面上編輯，也可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 這兩種情況中進行編輯。

|屬性名稱|必要|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.ServiceModel.Activities.InitializeCorrelation> 活動可選用的易記名稱。|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|否|指定用來管理子系傳訊活動的 <xref:System.ServiceModel.Activities.CorrelationHandle>。 如果沒有設定這個屬性，<xref:System.ServiceModel.Activities.CorrelationScope> 會自動建立隱含 <xref:System.ServiceModel.Activities.CorrelationHandle>。|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|否|指定相互關聯範圍內的活動。|

## <a name="see-also"></a>另請參閱
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [接收](../workflow-designer/receive-activity-designer.md) [receiveandsendreply]](../workflow-designer/receiveandsendreply-template-designer.md) [傳送](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)