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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656917"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope 活動設計工具
[ **CorrelationScope** ] 活動設計工具會用來建立和設定 <xref:System.ServiceModel.Activities.CorrelationScope> 活動，以使用 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件來提供子訊息活動的隱含管理。

## <a name="the-correlationscope-activity"></a>CorrelationScope 活動
 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 屬性會指定用來管理子系傳訊活動的 <xref:System.ServiceModel.Activities.CorrelationHandle>。 包含在 <xref:System.ServiceModel.Activities.Send> 中的 <xref:System.ServiceModel.Activities.Receive> 與 <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> 活動，會設定為使用包含之 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 活動的 <xref:System.ServiceModel.Activities.CorrelationScope> 屬性來執行相互關聯。

### <a name="using-the-correlationscope-activity-designer"></a>使用 CorrelationScope 活動設計工具
 [ **CorrelationScope** ] 活動設計**工具**位於 [工具箱] 的 [**訊息**] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 左側的 [**工具箱**] 索引標籤（也可以選取 [**工具列**]，從[ **View** ] 功能表，或 CTRL + ALT + X）。

 [ **CorrelationScope** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上。 這會建立具有 CorrelationScope 預設**DisplayName**的 <xref:System.ServiceModel.Activities.CorrelationScope> 活動。 @No__t_0 可以在 [ **CorrelationScope** ] 活動設計工具的標頭中編輯，或是在 [**屬性**] 視窗的 [ **DisplayName** ] 方塊中編輯。

 若要指定子訊息活動所使用的 <xref:System.ServiceModel.Activities.CorrelationHandle>，請按一下 [**屬性**] 視窗中 [ **CorrelatesWith** ] 欄位旁邊的省略號按鈕，以顯示 [**運算式編輯器**] 對話方塊。 這個屬性也可以在活動設計工具介面上設定。

 在相互關聯內設定範圍的活動，是藉由在**CorrelationScope**設計工具內**的 [內**文] 方塊中卸載其設計工具來指定。

### <a name="the-correlationscope-properties"></a>CorrelationScope 屬性
 下表顯示 <xref:System.ServiceModel.Activities.CorrelationScope> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在 [**屬性**] 視窗中或在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 設計工具介面上編輯，通常是在這兩者中。

|屬性名稱|必要項|使用量|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> 活動可選用的易記名稱。|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|指定用來管理子系傳訊活動的 <xref:System.ServiceModel.Activities.CorrelationHandle>。 如果沒有設定這個屬性，<xref:System.ServiceModel.Activities.CorrelationScope> 會自動建立隱含 <xref:System.ServiceModel.Activities.CorrelationHandle>。|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|指定相互關聯範圍內的活動。|

## <a name="see-also"></a>請參閱
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [接收](../workflow-designer/receive-activity-designer.md) [receiveandsendreply](../workflow-designer/receiveandsendreply-template-designer.md) [傳送](../workflow-designer/send-activity-designer.md) [sendandreceivereply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)