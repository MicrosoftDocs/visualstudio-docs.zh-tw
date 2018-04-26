---
title: 工作流程設計工具-選擇作業對話方塊 （舊版）
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fed4353771edc5f9cc1bb239424b0e7015acd84a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="choose-operation-dialog-box-legacy"></a>選擇作業對話方塊 (舊版)

本主題描述如何使用**選擇作業**在舊版的 Windows 工作流程設計工具 對話方塊。 當您需要以.NET Framework 3.5 版或 WinFX 為目標時，請使用舊版工作流程設計工具。

 **選擇作業**對話方塊用於選取要與建立關聯的作業<xref:System.Workflow.Activities.ReceiveActivity>活動或<xref:System.Workflow.Activities.SendActivity>活動。 如需有關此對話方塊中使用這些活動的詳細資訊，請參閱[How to： 實作 WCF 合約作業 （舊版）](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)和[How to： 叫用 WCF 合約作業 （舊版）](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)。

 下表描述的使用者介面 (UI) 項目**選擇作業** 對話方塊。

|UI 項目|描述|
|----------------|-----------------|
|**新增合約**|為您建立新合約。 您可以在這個合約上定義新作業。 (這個介面僅能與 <xref:System.Workflow.Activities.ReceiveActivity> 搭配使用)|
|**加入作業**|將新作業加入至您在中建立的新合約**選擇作業** 對話方塊。 **注意：**您可以加入新的作業只透過建立的合約**選擇作業** 對話方塊。 <br /><br /> (這個介面僅能與 <xref:System.Workflow.Activities.ReceiveActivity> 搭配使用)|
|**匯入...**|匯入先前定義的合約，並允許您從該合約選取作業。|
|**作業名稱**|目前選取之作業的名稱。 這個文字方塊是可供編輯您已建立作業時，才**選擇作業** 對話方塊。|
|**參數**|索引標籤，包含目前所選取作業的參數定義。 **注意：**您已建立作業時，才可以變更參數定義**選擇作業** 對話方塊。|
|**屬性**|索引標籤，包含用於用戶端和服務之間所傳送之訊息的 <xref:System.Net.Security.ProtectionLevel> 設定。 **注意：**此索引標籤在您已建立作業時，才會啟用**選擇作業** 對話方塊。|
|**權限**|索引標籤，包含允許呼叫該作業之使用者的 <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> 和 <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> 屬性。 例如，如果只允許從 Administrators 群組的使用者所呼叫該作業，然後您會 「 系統管理員 」 中撰寫**角色**文字方塊。<br /><br /> 此索引標籤已啟用這兩項作業是透過建立**ChooseOperation**對話方塊，並透過匯入作業**匯入** 按鈕。|

> [!NOTE]
> **選擇作業**對話方塊會顯示唯一的合約或作業所使用的其他<xref:System.Workflow.Activities.SendActivity>工作流程中的活動。 同樣地，**選擇作業**對話方塊的 <xref:System.Workflow.Activities.ReceiveActivity>活動顯示唯一的合約或作業所使用的其他**ReceiveActivity**工作流程中的活動。

## <a name="see-also"></a>另請參閱

- [如何： 實作 WCF 合約作業 （舊版）](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)
- [如何： 叫用 WCF 合約作業 （舊版）](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)
- [舊版 Windows Workflow Foundation UI 設計工具的說明](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)