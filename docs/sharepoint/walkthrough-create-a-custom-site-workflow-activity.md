---
title: 逐步解說：建立自訂網站工作流程活動 |Microsoft Docs
description: 在這個逐步解說中，請參閱如何使用 Visual Studio 建立網站層級 SharePoint 工作流程的自訂活動。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29a3cd6fe37ec824a3db3a2c83aad7434d0018cb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218044"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>逐步解說：建立自訂網站工作流程活動
  本逐步解說示範如何使用建立網站層級工作流程的自訂活動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。  (網站層級的工作流程會套用到整個網站，而不只是網站上的清單。 ) 自訂活動會建立備份公告清單，然後將公告清單的內容複寫到其中。

 本逐步解說將示範下列工作：

- 建立網站層級工作流程。

- 建立自訂工作流程活動。

- 建立和刪除 SharePoint 清單。

- 將專案從一個清單複製到另一個清單。

- 在快速啟動列上顯示清單。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- 支援的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。

- Visual Studio。

## <a name="create-a-site-workflow-custom-activity-project"></a>建立網站工作流程自訂活動專案
 首先，建立專案來保存及測試自訂工作流程活動。

#### <a name="to-create-a-site-workflow-custom-activity-project"></a>若要建立網站工作流程自訂活動專案

1. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]，以顯示 [**新增專案**] 對話方塊。

2. 展開 [ **Visual c #** ] 或 [ **Visual Basic**] 底下的 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 在 [ **範本** ] 窗格中，選擇 [ **SharePoint 2010] 專案** 範本。

4. 在 [ **名稱** ] 方塊中，輸入 **AnnouncementBackup**，然後選擇 [ **確定]** 按鈕。

     [ **SharePoint 自訂] Wizard** 隨即出現。

5. 在 [ **指定偵錯工具的網站和安全性層級** ] 頁面上，選擇 [ **部署為伺服器陣列方案** ] 選項按鈕，然後選擇 [ **完成]** 按鈕以接受信任層級和預設網站。

     此步驟會將解決方案的信任層級設定為伺服器陣列方案，這是工作流程專案的唯一可用選項。

6. 在 **方案總管** 中，選擇專案節點，然後在功能表列上選擇 [**專案**  >  **加入新專案**]。

7. 在 [ **Visual c #** ] 或 [ **Visual Basic**] 下，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

8. 在 [ **範本** ] 窗格中，選擇 [ **僅限順序的工作流程 (伺服器陣列方案])** 範本，然後選擇 [ **加入** ] 按鈕。

     [ **SharePoint 自訂] Wizard** 隨即出現。

9. 在 [ **指定用於偵錯工具的工作流程名稱** ] 頁面上，接受預設名稱 (AnnouncementBackup-workflow1.xaml) 。 將 [工作流程範本類型] 變更為 [ **網站工作流程**]，然後選擇 [ **下一步]** 按鈕。

10. 選擇 [ **完成]** 按鈕以接受其餘的預設設定。

## <a name="add-a-custom-workflow-activity-class"></a>新增自訂工作流程活動類別
 接下來，將類別加入至專案，以包含自訂工作流程活動的程式碼。

#### <a name="to-add-a-custom-workflow-activity-class"></a>若要加入自訂工作流程活動類別

1. 在功能表列上 **，選擇 [**  >  **加入新** 專案]，以顯示 [**加入新專案**] 對話方塊。

2. 在 [ **已安裝的範本** ] 樹狀檢視中，選擇 [程式 **代碼** ] 節點，然後選擇專案專案範本清單中的 [ **類別** ] 範本。 使用預設名稱 Class1。 選擇 [新增] 按鈕。

3. 以下列程式碼取代 Class1 中的所有程式碼：

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb" id="Snippet1":::

4. 儲存專案，然後在功能表列上選擇 [**組建**  >  **組建方案**]。

     Class1 會在 [ **AnnouncementBackup 元件**] 索引標籤上的 [**工具箱**] 中顯示為自訂動作。

## <a name="add-the-custom-activity-to-the-site-workflow"></a>將自訂活動新增至網站工作流程
 接下來，將活動新增至工作流程，以包含自訂程式碼。

#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>將自訂活動新增至網站工作流程

1. 在設計檢視的工作流程設計工具中開啟 Workflow1.xaml。

2. 從 [ **工具箱** ] 拖曳 [Class1]，使其出現在活動底下， `onWorkflowActivated1` 或是開啟 [class1] 的快捷方式功能表，選擇 [ **複製**]，開啟活動下的行的快捷方式功能表， `onWorkflowActivated1` 然後選擇 [ **貼** 上]。

3. 儲存專案。

## <a name="test-the-site-workflow-custom-activity"></a>測試網站工作流程自訂活動
 接下來，執行專案並啟動網站工作流程。 自訂活動會建立備份公告清單，並將目前公告清單中的內容複寫到其中。 程式碼也會檢查備份清單是否已存在，然後再建立一個。 如果備份清單已經存在，則會刪除它。 程式碼也會在 SharePoint 網站的快速啟動列上新增新清單的連結。

#### <a name="to-test-the-site-workflow-custom-activity"></a>測試網站工作流程自訂活動

1. 選擇 **F5** 鍵以執行專案，並將其部署到 SharePoint。

2. 在 [快速啟動] 列上，選擇 [ **清單** ] 連結，以顯示可在 SharePoint 網站中使用的所有清單。 請注意，有一個名為「 **宣告**」的公告清單。

3. 在 SharePoint 網頁頂端，選擇 [ **網站工作流程** ] 連結。

4. 在 [開始新的工作流程] 區段下，選擇 [ **AnnouncementBackup-workflow1.xaml** ] 連結。 這會啟動網站工作流程，並在自訂動作中執行程式碼。

5. 在 [快速啟動] 列上，選擇 [ **公告備份** ] 連結。 請注意， **公告** 清單中包含的所有公告都已複製到此新清單。

## <a name="see-also"></a>另請參閱
- [如何：建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
