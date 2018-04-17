---
title: 逐步解說： 建立自訂站台工作流程活動 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 14eaa5f23af978ae603c4f8b94d3c3d18953943f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>逐步解說：建立自訂站台工作流程活動
  本逐步解說示範如何建立網站層級的工作流程使用的自訂活動[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 （網站層級的工作流程套用至整個網站，而不只是站台上的清單）。自訂活動會建立備份公告清單，然後公告清單的內容複製到其中。  
  
 本逐步解說將示範下列工作：  
  
-   建立站台層級工作流程。  
  
-   建立自訂工作流程活動。  
  
-   建立和刪除 SharePoint 清單。  
  
-   一個清單項目複製到另一個。  
  
-   在 快速啟動列上顯示清單。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的版本[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]和 SharePoint。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## <a name="creating-a-site-workflow-custom-activity-project"></a>建立站台工作流程自訂活動專案  
 首先，建立專案來保存及測試的自訂工作流程活動。  
  
#### <a name="to-create-a-site-workflow-custom-activity-project"></a>若要建立站台工作流程自訂活動專案  
  
1.  在功能表列上選擇 [**檔案**，**新增**，**專案**顯示**新專案**] 對話方塊。  
  
2.  展開**SharePoint**節點之下**Visual C#**或**Visual Basic**，然後選擇  **2010年**節點。  
  
3.  在**範本** 窗格中，選擇**SharePoint 2010 專案**範本。  
  
4.  在**名稱**方塊中，輸入**AnnouncementBackup**，然後選擇 [**確定**] 按鈕。  
  
     **SharePoint 自訂精靈**隨即出現。  
  
5.  上**指定偵錯的網站和安全性層級**頁面上，選擇**部署為伺服陣列方案**選項按鈕，然後再選擇**完成**接受按鈕信任層級和預設站台。  
  
     此步驟會設定為伺服器陣列方案，唯一可用的選項的工作流程專案方案的信任層級。  
  
6.  在**方案總管] 中**，選擇專案節點，然後在功能表列上選擇 [**專案**，**加入新項目**。  
  
7.  之下**Visual C#**或**Visual Basic**，依序展開**SharePoint** ] 節點，然後選擇 [ **2010年**節點。  
  
8.  在**範本** 窗格中，選擇**循序工作流程 （僅限陣列方案）**範本，然後選擇 **新增** 按鈕。  
  
     **SharePoint 自訂精靈**隨即出現。  
  
9. 在**指定偵錯的工作流程名稱**頁面上，接受預設名稱 (AnnouncementBackup-Workflow1)。 將工作流程範本類型變更為**站台工作流程**，然後選擇 [**下一步**] 按鈕。  
  
10. 選擇**完成** 按鈕，接受其餘的預設設定。  
  
## <a name="adding-a-custom-workflow-activity-class"></a>加入自訂工作流程活動類別  
 接下來，將類別加入專案，以包含自訂工作流程活動的程式碼。  
  
#### <a name="to-add-a-custom-workflow-activity-class"></a>若要加入自訂工作流程活動類別  
  
1.  在功能表列上選擇 [**專案**，**加入新項目**顯示**加入新項目**] 對話方塊。  
  
2.  在**已安裝的範本**樹狀檢視中，選擇**程式碼**] 節點，然後選擇 [**類別**專案項目範本清單中的範本。 使用預設名稱 Class1。 選擇 [ **加入** ] 按鈕。  
  
3.  以下列內容取代所有 Class1 的程式碼：  
  
     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]  
  
4.  儲存專案，然後在功能表列上選擇 **建置**，**建置方案**。  
  
     Class1 會顯示為中的自訂動作**工具箱**上**AnnouncementBackup 元件** 索引標籤。  
  
## <a name="adding-the-custom-activity-to-the-site-workflow"></a>將自訂活動新增至站台工作流程  
 接下來，將活動加入至工作流程，以包含自訂程式碼。  
  
#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>將自訂活動新增至站台工作流程  
  
1.  在 [設計] 檢視中的工作流程設計工具中開啟 Workflow1。  
  
2.  拖曳從 Class1**工具箱**使其出現在`onWorkflowActivated1`活動或開啟捷徑功能表的 Class1 選擇**複製**，開啟下的那一行的捷徑功能表`onWorkflowActivated1`活動，然後選擇 **貼上**。  
  
3.  儲存專案。  
  
## <a name="testing-the-site-workflow-custom-activity"></a>測試站台工作流程自訂活動  
 接下來，請執行專案，並啟動網站工作流程。 自訂活動建立備份的公告清單，並將內容從目前的公告清單複製到其中。 程式碼也會檢查備份的清單是否已存在於之前建立一個。 如果備份清單已經存在，會將它刪除。 程式碼也會加入新的清單，在 SharePoint 網站的快速啟動列上的連結。  
  
#### <a name="to-test-the-site-workflow-custom-activity"></a>若要測試的站台工作流程自訂活動  
  
1.  選擇 F5 鍵以執行專案，並將它部署至 SharePoint。  
  
2.  在 快速啟動 列上選擇 **列出**連結可以顯示所有 SharePoint 網站中可用的清單。 請注意會宣告名為只能有一個清單**公告**。  
  
3.  在 SharePoint 網頁的頂端，選擇 **網站工作流程**連結。  
  
4.  在 開始新的工作流程區段中，選擇**AnnouncementBackup-Workflow1**連結。 這樣會啟動網站工作流程，並執行自訂動作的程式碼。  
  
5.  在 快速啟動 列上選擇 **公告備份**連結。 請注意，所有的宣告中所包含的**公告**清單已複製到這個新的清單。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  