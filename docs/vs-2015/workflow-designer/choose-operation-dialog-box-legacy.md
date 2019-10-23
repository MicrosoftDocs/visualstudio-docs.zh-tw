---
title: 選擇作業對話方塊（舊版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f2736db7e18733a9477238cafad21088eb135e89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659167"
---
# <a name="choose-operation-dialog-box-legacy"></a>選擇作業對話方塊 (舊版)
本主題描述如何使用舊版 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 中的 [**選擇**作業] 對話方塊。 當您需要以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]。

 [**選擇**作業] 對話方塊是用來選取要與 <xref:System.Workflow.Activities.ReceiveActivity> 活動或 <xref:System.Workflow.Activities.SendActivity> 活動產生關聯的作業。 如需搭配使用此對話方塊與這些活動的詳細資訊，請參閱 [How to：執行 WCF 合約作業（舊版） ](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) 並 [How 至：叫用 WCF 合約作業（舊版） ](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)。

 下表描述 [**選擇**作業] 對話方塊的使用者介面（UI）元素。

|UI 項目|描述|
|----------------|-----------------|
|**新增合約**|為您建立新合約。 您可以在這個合約上定義新作業。 (這個介面僅能與 <xref:System.Workflow.Activities.ReceiveActivity> 搭配使用)|
|**新增作業**|將新作業加入至您在 [**選擇操作**] 對話方塊中建立的新合約。 **注意：** 您只能透過 [**選擇**作業] 對話方塊，將新作業新增至您所建立的合約。 <br /><br /> (這個介面僅能與 <xref:System.Workflow.Activities.ReceiveActivity> 搭配使用)|
|**匯入 .。。**|匯入先前定義的合約，並允許您從該合約選取作業。|
|**作業名稱**|目前選取之作業的名稱。 只有當您已透過 [**選擇**作業] 對話方塊建立作業時，這個文字方塊才可供編輯。|
|**參數**|索引標籤，包含目前所選取作業的參數定義。 **注意：** 只有當您已透過 [**選擇**作業] 對話方塊建立作業時，才可以變更參數定義。|
|**屬性**|索引標籤，包含用於用戶端和服務之間所傳送之訊息的 <xref:System.Net.Security.ProtectionLevel> 設定。 **注意：** 只有當您已透過 [**選擇**作業] 對話方塊建立作業時，才會啟用此索引標籤。|
|**權限**|索引標籤，包含允許呼叫該作業之使用者的 <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> 和 <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> 屬性。 例如，如果只有 Administrators 群組的使用者可以呼叫該作業，則您會在 [**角色**] 文字方塊中寫入「系統管理員」。<br /><br /> 這兩個透過 [ **ChooseOperation** ] 對話方塊建立的作業，以及透過 [匯**入**] 按鈕匯入的作業，都會啟用此索引標籤。|

> [!NOTE]
> [**選擇**作業] 對話方塊只會顯示工作流程中其他 <xref:System.Workflow.Activities.SendActivity> 活動所使用的合約或作業。 同樣地，<xref:System.Workflow.Activities.ReceiveActivity> 活動的 [**選擇**作業] 對話方塊只會顯示工作流程中的其他**ReceiveActivity**活動所使用的合約或作業。

## <a name="see-also"></a>另請參閱
 [如何：執行 WCF 合約作業（舊版） ](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [How：叫用 WCF 合約作業（舊版） ](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)[舊版設計工具以取得 WINDOWS WORKFLOW FOUNDATION UI](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)說明