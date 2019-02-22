---
title: 逐步解說：建立自訂網站工作流程活動 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dfed62c493473c48704061fac00427f40d828520
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615828"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>逐步解說：建立自訂網站工作流程活動
  本逐步解說示範如何建立站台層級工作流程使用自訂活動[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 （網站層級的工作流程套用至整個網站，而不只是在站台上的清單）。自訂活動建立備份的公告清單中，並再將 [公告] 清單的內容複製到其中。

 本逐步解說將示範下列工作：

- 建立站台層級工作流程。

- 建立自訂工作流程活動。

- 建立和刪除 SharePoint 清單。

- 從一份清單的項目複製到另一個。

- 在 [快速啟動] 列上顯示的清單。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

-   支援的版本[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]和 SharePoint。

-   Visual Studio。

## <a name="create-a-site-workflow-custom-activity-project"></a>建立站台工作流程自訂活動專案
 首先，建立專案來保存，並測試自訂工作流程活動。

#### <a name="to-create-a-site-workflow-custom-activity-project"></a>若要建立站台工作流程自訂活動專案

1.  在功能表列上選擇 [**檔案** > **新增** > **專案**顯示**新專案**] 對話方塊。

2.  依序展開**SharePoint**節點之下**Visual C#** 或**Visual Basic**，然後選擇**2010年**節點。

3.  在 **範本**窗格中，選擇**SharePoint 2010 專案**範本。

4.  在 [**名稱**方塊中，輸入**AnnouncementBackup**，然後選擇 **[確定]** ] 按鈕。

     **SharePoint 自訂精靈**隨即出現。

5.  在上**指定偵錯的網站和安全性層級**頁面上，選擇**部署為伺服陣列方案**選項按鈕，然後選擇**完成**按鈕以接受信任層級和預設站台。

     此步驟會設定為陣列方案，唯一可用的選項，工作流程專案方案的信任層級。

6.  在 **方案總管**，選擇專案節點，然後在功能表列上選擇 **專案** > **加入新項目**。

7.  之下**Visual C#** 或**Visual Basic**，展開**SharePoint**  節點，然後選擇**2010年**節點。

8.  在**範本** 窗格中，選擇**循序工作流程 （僅限陣列方案）** 範本，然後選擇**新增** 按鈕。

     **SharePoint 自訂精靈**隨即出現。

9. 在 **指定偵錯的工作流程名稱**頁面上，接受預設名稱 (AnnouncementBackup-Workflow1)。 將工作流程範本類型變更為**站台工作流程**，然後選擇**下一步**  按鈕。

10. 選擇**完成** 按鈕，接受其餘的預設設定。

## <a name="add-a-custom-workflow-activity-class"></a>加入自訂工作流程活動類別
 接下來，將類別加入專案，以包含自訂工作流程活動的程式碼。

#### <a name="to-add-a-custom-workflow-activity-class"></a>若要加入自訂工作流程活動類別

1.  在功能表列上選擇 [**專案** > **加入新項目**以顯示**加入新項目**] 對話方塊。

2.  中**已安裝的範本**樹狀檢視中，選擇**程式碼**節點，然後選擇**類別**專案項目範本清單中的範本。 使用預設名稱 Class1。 選擇 [ **加入** ] 按鈕。

3.  您可以將所有類別 1 中的程式碼取代為下列：

     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]

4.  儲存專案，，然後在功能表列上，選擇**建置** > **建置方案**。

     Class1 會顯示為中的自訂動作**工具箱**上**AnnouncementBackup 元件** 索引標籤。

## <a name="add-the-custom-activity-to-the-site-workflow"></a>將自訂活動新增至網站工作流程
 接下來，將活動新增至工作流程，以包含自訂程式碼。

#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>若要將自訂活動新增至網站工作流程

1.  在 [設計] 檢視中的工作流程設計工具中開啟 Workflow1。

2.  拖曳從 Class1**工具箱**，使其出現在`onWorkflowActivated1`活動或 Class1，開啟捷徑功能表選擇 **複製**，開啟下的那一行的捷徑功能表`onWorkflowActivated1`活動，然後選擇**貼上**。

3.  儲存專案。

## <a name="test-the-site-workflow-custom-activity"></a>測試站台工作流程自訂活動
 接下來，執行專案，並啟動網站工作流程。 自訂活動會建立備份的公告清單，並從目前的公告清單的內容複製到其中。 程式碼也會檢查是否建立之前已存在備份清單。 如果備份清單已經存在，則會將它刪除。 程式碼也會新增至新的清單，在 SharePoint 網站的 [快速啟動] 列上的連結。

#### <a name="to-test-the-site-workflow-custom-activity"></a>若要測試的站台工作流程自訂活動

1.  選擇**F5**執行專案，並將它部署到 SharePoint 的索引鍵。

2.  在 [快速啟動] 列中，選擇**列出**連結可以顯示所有的 SharePoint 網站中可用的清單。 請注意有只有一個名為的公告清單**宣布**。

3.  在 SharePoint 網頁的頂端，選擇**站台工作流程**連結。

4.  在 開始新的工作流程區段中，選擇**AnnouncementBackup-Workflow1**連結。 這會啟動網站工作流程，並執行自訂動作中的程式碼。

5.  在 [快速啟動] 列中，選擇**宣布備份**連結。 請注意，宣告中所包含的所有**宣布**清單已複製到這個新的清單。

## <a name="see-also"></a>另請參閱
- [如何：建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
