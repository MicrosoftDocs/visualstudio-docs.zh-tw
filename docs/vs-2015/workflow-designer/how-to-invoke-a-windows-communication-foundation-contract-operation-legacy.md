---
title: HOW TO：叫用 Windows Communication Foundation 合約作業 （舊版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d42c9698c6d3a247601909909c49fa92d2d29978
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855979"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>HOW TO：叫用 Windows Communication Foundation 合約作業 (舊版)
本主題描述當使用以 [!INCLUDE[indigo1](../includes/indigo1-md.md)] 或 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 為目標的舊版 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 時，如何叫用 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 合約作業。  
  
 拖曳之後**SendActivity**活動從工具箱拖曳至工作流程設計介面，您必須匯入現有的合約，並判斷哪一項作業將會叫用該**SendActivity**活動。 您選取您的合約和其作業，透過[選擇作業對話方塊 （舊版）](../workflow-designer/choose-operation-dialog-box-legacy.md)。  
  
 此外，如果您正在使用組態檔搭配您的服務，則必須指定 <xref:System.Workflow.Activities.ChannelToken>。 <xref:System.Workflow.Activities.ChannelToken> 會識別您的傳送活動將用於連線至工作流程服務的端點組態。  
  
### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>若要從 SendActivity 活動叫用 WCF 合約作業  
  
1. 按兩下**SendActivity**設計工具中的活動或旁按一下省略符號**ServiceOperationInfo**中的屬性**屬性**窗格。  
  
2. 當**選擇作業** 對話方塊隨即開啟，請按一下**匯入**對話方塊右上角。  
  
     [瀏覽並選取.NET 類型對話方塊 （舊版）](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)隨即開啟。  
  
3. 搜尋含有您所要之合約的組件或專案。  
  
4. 選取合約，然後按一下**確定**。  
  
5. 底下**可用的作業**，選取您想要叫用，並按一下 的作業**確定**。  
  
### <a name="to-specify-a-channel-token"></a>若要指定通道權杖  
  
1. 選取設計工具中的 <xref:System.Workflow.Activities.SendActivity> 活動。  
  
2. 在 **屬性**窗格中，指定的名稱<xref:System.Workflow.Activities.ChannelToken>。 這個名稱會唯一識別通道權杖。  
  
3. 展開通道權杖節點，然後為將在 <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> 欄位使用的用戶端端點指定名稱。 組態檔中相同名稱的端點組態將用於設定通道。  
  
4. 如果端點組態已不存在，請在組態檔中建立端點組態。 如需有關如何設定您的用戶端的詳細資訊，請參閱 < [WCF Client Overview](http://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d)。  
  
## <a name="see-also"></a>另請參閱  
 [選擇作業對話方塊 （舊版）](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [如何：實作 WCF 合約作業 （舊版）](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)