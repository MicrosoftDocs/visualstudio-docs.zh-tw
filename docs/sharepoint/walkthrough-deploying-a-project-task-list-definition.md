---
title: 逐步解說：部署專案工作清單定義 |Microsoft Docs
description: 在這個逐步解說中，使用 Visual Studio 建立、自訂、偵測和部署 SharePoint 清單來追蹤專案工作。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0be8eed2dc41ad433c0e0514dfd34e3c6e3d7193
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970426"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>逐步解說：部署專案工作清單定義

本逐步解說將示範如何使用 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] 建立、自訂、偵錯和部署 SharePoint 清單以追蹤專案工作。

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites

- 支援的 Microsoft Windows 和 SharePoint 版本。

- Visual Studio 2017 或 Azure DevOps Services。

## <a name="create-a-sharepoint-list"></a>建立 SharePoint 清單

建立 SharePoint 清單專案，並將清單定義與工作產生關聯。

1. 開啟 [ **新增專案** ] 對話方塊，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

2. 在 [ **範本** ] 窗格中，選擇 [ **SharePoint 2010 專案** ] 範本、將專案命名為 **ProjectTaskList**，然後選擇 [ **確定]** 按鈕。

     [ **SharePoint 自訂] Wizard** 隨即出現。

3. 指定您用於偵錯工具的本機 SharePoint 網站，選擇 [ **部署為伺服器陣列方案** ] 選項按鈕，然後選擇 [ **完成]** 按鈕。

4. 開啟專案的快捷方式功能表，然後選擇 [**加入**  >  **新專案**]。

5. 在 [ **範本** ] 窗格中，選擇 [ **清單** ] 範本，然後選擇 [ **加入** ] 按鈕。

     [ **SharePoint 自訂] Wizard** 隨即出現。

6. 在 [ **您要為清單顯示什麼名稱？** ] 方塊中，輸入 **Project 工作清單**。

7. 選擇 [ **依據現有的清單類型建立不可自訂的清單** ] 按鈕，然後在其清單 **中選擇 [** 工作]，然後選擇 [ **完成]** 按鈕。

     清單、功能和套件會出現在 **方案總管** 中。

## <a name="add-an-event-receiver"></a>新增事件接收器

在工作清單中，您可以加入事件接收器，以便自動設定工作的到期日和描述。 下列程式會將簡單的事件處理常式加入至清單實例，做為事件接收器。

1. 開啟專案節點的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

2. 在 SharePoint 範本清單中，選擇 [ **事件接收器** ] 範本，然後將它命名為 **ProjectTaskListEventReceiver**。

     [ **SharePoint 自訂] Wizard** 隨即出現。

3. 在 [ **選擇事件接收器設定** ] 頁面上，選擇 [ **清單專案事件** ] 作為 [ **您需要哪種類型的事件接收器** ] 清單中的 [事件接收器] 類型。

4. 在 [ **哪個專案應該是事件來源** ] 清單中， **選擇 [** 工作]。

5. 在要處理的事件清單中，選取 **已加入專案** 旁的核取方塊，然後選擇 [ **完成]** 按鈕。

     新的事件接收器節點會加入至專案，其中包含名為 **ProjectTaskListEventReceiver** 的程式碼檔案。

6. 將程式碼加入至 `ItemAdded` **ProjectTaskListEventReceiver** 程式碼檔中的方法。 每次新增工作時，就會在工作中加入預設的到期日和描述。 預設的到期日為2009年7月1日。

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>自訂專案工作清單功能

當您建立 SharePoint 方案時，Visual Studio 會自動建立預設專案專案的功能。 您可以使用 [功能設計工具] 來自訂 SharePoint 網站的專案工作清單設定。

1. 在 **方案總管** 中，展開 [ **功能**]。

2. 開啟 **Feature1** 的快捷方式功能表，然後選擇 [ **View Designer**]。

3. 在 [ **標題** ] 方塊中，輸入 **Project 工作清單功能**。

4. 在 [ **範圍** ] 清單中，選擇 [ **Web**]。

5. 在 [ **屬性** ] 視窗中，輸入 **1.0.0.0** 作為 [ **版本** ] 屬性的值。

## <a name="customize-the-project-task-list-package"></a>自訂專案工作清單套件

當您建立 SharePoint 專案時，Visual Studio 會自動將包含預設專案專案的功能加入封裝中。 您可以使用封裝設計工具來自訂 SharePoint 網站的專案工作清單設定。

1. 在 [ **方案總管**] 中，開啟 [ **封裝**] 的快捷方式功能表，然後選擇 [ **View Designer**]。

2. 在 [ **名稱** ] 方塊中，輸入 **ProjectTaskListPackage**。

3. 選取 [ **重設網頁伺服器** ] 核取方塊。

## <a name="build-and-test-the-project-task-list"></a>建立和測試專案工作清單

當您執行專案時，會開啟 SharePoint 網站。 不過，您必須以手動方式流覽至 [工作清單] 的位置。

1. 選擇 **F5** 鍵來建立和部署專案工作清單。

     SharePoint 網站隨即開啟。

2. 選擇 [ **首頁** ] 索引標籤。

3. 在左側提要欄位中，選擇 **專案工作清單** 連結。

     [專案工作清單] 頁面隨即出現。

4. 在 [ **清單工具** ] 索引標籤中，選擇 [ **專案** ] 索引標籤。

5. 在 [ **專案** ] 群組中，選擇 [ **新增專案** ] 按鈕。

6. 在 [ **標題** ] 文字方塊中，輸入 **Task1**。

7. 選擇 [ **儲存** ] 按鈕。

     重新整理網站之後， **Task1** 工作會顯示為到期日7/1/2009。

8. 選擇 [ **Task1**]。

     工作的詳細觀點隨即出現，且描述會顯示「這是重要的工作」。

## <a name="deploy-the-project-task-list"></a>部署專案工作清單

在您建立並測試專案工作清單之後，就可以將它部署到 *本機系統* 或 *遠端系統*。 本機系統是您用來開發解決方案的同一部電腦，而遠端系統則是不同的電腦。

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>將專案工作清單部署至本機系統

在 [Visual Studio] 功能表列上，選擇 [**建立**  >  **部署方案**]。

Visual Studio 回收 IIS 應用程式集區、撤銷任何現有版本的解決方案、將方案套件 (*.wsp*) 檔案複製到 SharePoint，然後啟動其功能。 您現在可以在 SharePoint 中使用方案。 如需部署設定步驟的詳細資訊，請參閱 [如何：編輯 SharePoint 部署](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)設定。

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>將專案工作清單部署至遠端系統

1. 在 [Visual Studio] 功能表列上，選擇 [**組建**  >  **發行**]。

2. 在 [ **發行** ] 對話方塊中，選擇 [ **發行至檔案系統** ] 選項按鈕。

     您可以在 [ **發行** ] 對話方塊中，選擇省略號按鈕 ![省略號圖示](../sharepoint/media/ellipsisicon.gif "省略符號圖示") ，然後流覽至另一個位置，以變更目標位置。

3. 選擇 [**發行**] 按鈕。

     為方案建立 *.wsp* 檔。

4. 將 *.wsp* 檔案複製到遠端 SharePoint 系統。

5. 使用 PowerShell `Add-SPUserSolution` 命令，在遠端 SharePoint 安裝上安裝套件。  (伺服器陣列方案，請使用 `Add-SPSolution` 命令。 ) 

     例如： `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp` 。

6. 使用 PowerShell `Install-SPUserSolution` 命令來部署解決方案。  (伺服器陣列方案，請使用 `Install-SPSolution` 命令。 ) 

     例如： `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName` 。

     如需遠端部署的詳細資訊，請參閱在 SharePoint 2010 中 [使用方案和使用](/previous-versions/office/developer/sharepoint-2010/ee534972(v=office.14)) [PowerShell 新增和部署解決方案](http://www.dotnetmafia.com/blogs/dotnettipoftheday/archive/2009/12/02/adding-and-deploying-solutions-with-powershell-in-sharepoint-2010.aspx)。

## <a name="next-steps"></a>後續步驟

您可以從下列主題深入瞭解如何自訂及部署 SharePoint 方案：

- [逐步解說：建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [如何：建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)

- [適用于 SharePoint Server 2010 的 Windows PowerShell](/powershell/module/sharepoint-server)

## <a name="see-also"></a>另請參閱
[封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
