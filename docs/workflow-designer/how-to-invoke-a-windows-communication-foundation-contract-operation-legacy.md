---
title: 工作流程設計工具-How to： 叫用 Windows Communication Foundation 合約作業 （舊版）
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b39d2132b29ec1f8fbfd8339bdb8f81e6f752a0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>HOW TO：叫用 Windows Communication Foundation 合約作業 (舊版)

本主題描述如何叫用使用舊版的 Windows 工作流程設計工具的 Windows Communication Foundation (WCF) 合約作業目標的.NET Framework 3.5 版或 WinFX。

拖曳後**SendActivity**活動從工具箱拖曳至工作流程設計介面中，匯入現有的合約。 判斷哪一項作業會叫用與**SendActivity**活動。 選取的合約和其作業透過[選擇作業對話方塊 （舊版）](../workflow-designer/choose-operation-dialog-box-legacy.md)。

此外，如果您正在使用您的服務組態檔，您需要指定<xref:System.Workflow.Activities.ChannelToken>。 <xref:System.Workflow.Activities.ChannelToken> 會識別您的傳送活動將用於連線至工作流程服務的端點組態。

## <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>若要從 SendActivity 活動叫用 WCF 合約作業

1.  按兩下**SendActivity**活動設計工具中的，或按一下省略符號旁**ServiceOperationInfo**屬性**屬性**窗格。

2.  當**選擇作業**對話方塊隨即開啟，請按一下**匯入**對話方塊右上角。

     [瀏覽並選取.NET 類型對話方塊 （舊版）](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)隨即開啟。

3.  搜尋含有您所要之合約的組件或專案。

4.  選取合約，然後按一下 **確定**。

5.  在下**可用的作業**，選取您想要叫用，然後按一下的操作**確定**。

## <a name="to-specify-a-channel-token"></a>若要指定通道權杖

1.  選取設計工具中的 <xref:System.Workflow.Activities.SendActivity> 活動。

2.  在**屬性** 窗格中，指定的名稱<xref:System.Workflow.Activities.ChannelToken>。 這個名稱會唯一識別通道權杖。

3.  展開通道權杖節點，然後為將在 <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> 欄位使用的用戶端端點指定名稱。 在組態檔中相同名稱的端點組態用來設定通道。

4.  如果端點組態已不存在，請在組態檔中建立端點組態。 如需有關如何設定您的用戶端的詳細資訊，請參閱[WCF 用戶端概觀](/dotnet/framework/wcf/wcf-client-overview)。

## <a name="see-also"></a>另請參閱

- [選擇作業對話方塊 (舊版)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [如何： 實作 WCF 合約作業 （舊版）](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)
- [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)