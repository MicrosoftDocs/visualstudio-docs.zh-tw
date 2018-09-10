---
title: 逐步解說： 部署專案工作清單定義 |Microsoft Docs
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
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0e0a0338f14ecdea36c5a5678a42a76ae234bb6d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280359"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>逐步解說： 部署專案工作清單定義

本逐步解說將示範如何使用 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] 建立、自訂、偵錯和部署 SharePoint 清單以追蹤專案工作。

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件

- 支援的 Microsoft Windows 和 SharePoint 版本。

- Visual Studio 2017 或 Azure 的 DevOps 服務。

## <a name="create-a-sharepoint-list"></a>建立 SharePoint 清單

建立 SharePoint 清單專案，並將清單定義與工作產生關聯。

1. 開啟**新的專案**對話方塊方塊中，展開**SharePoint**節點，然後選擇**2010年**節點。

2. 在 [**範本**] 窗格中，選擇**SharePoint 2010 專案**範本，將專案命名為**ProjectTaskList**，然後選擇 [ **[確定]**] 按鈕。

     **SharePoint 自訂精靈**隨即出現。

3. 指定您用於偵錯的本機 SharePoint 網站選擇**部署為伺服陣列方案**選項按鈕，然後再選擇**完成** 按鈕。

4. 開啟專案的捷徑功能表，然後選擇**新增** > **新項目**。

5. 在**範本** 窗格中，選擇**清單**範本，然後選擇**新增** 按鈕。

     **SharePoint 自訂精靈**隨即出現。

6. 在 **您想要讓清單顯示什麼名稱？** 方塊中，輸入**專案工作清單**。

7. 選擇**建立不可自訂的清單，根據現有清單類型**選項按鈕，，然後在其清單中，選擇**工作**，然後選擇**完成** 按鈕。

     會出現在清單、 功能和封裝**方案總管 中**。

## <a name="add-an-event-receiver"></a>加入事件接收器

在工作清單中，您可以加入事件接收器，以便自動設定工作的到期日和描述。 下列程序會做為事件接收者，將簡單的事件處理常式加入至清單執行個體。

1. 開啟專案節點的捷徑功能表，選擇 **新增**，然後選擇**新項目**。

2. 在 SharePoint 範本清單中，選擇**事件接收器**範本，並將它命名**ProjectTaskListEventReceiver**。

     **SharePoint 自訂精靈**隨即出現。

3. 在上**選擇事件接收器設定**頁面上，選擇**清單項目事件**作為中的事件接收器類型**您要何種類型的事件接收器**清單。

4. 在 **何種項目應該做為事件來源**清單中，選擇**工作**。

5. 在要處理的事件清單中，選取核取方塊旁**項目已加入**，然後選擇**完成** 按鈕。

     新的事件接收器節點，會使用名為的程式碼檔案加入至專案**ProjectTaskListEventReceiver**。

6. 將程式碼加入`ItemAdded`方法中的**ProjectTaskListEventReceiver**程式碼檔案。 每次加入新的工作，就會到期日] 和 [描述預設值新增至工作。 由於預設日期是 2009 年 7 月 1 日。

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>自訂專案工作清單功能

當您建立 SharePoint 方案時，Visual Studio 會自動建立預設的功能的專案項目。 您可以使用功能設計工具中自訂 SharePoint 網站的專案工作清單設定。

1. 在 **方案總管**，展開**功能**。

2. 開啟捷徑功能表**Feature1**，然後選擇**檢視表設計工具**。

3. 在 **標題**方塊中，輸入**專案工作清單功能**。

4. 在 **領域**清單中，選擇**Web**。

5. 在 [**屬性**] 視窗中，輸入**1.0.0.0**做為值**版本**屬性。

## <a name="customize-the-project-task-list-package"></a>自訂專案工作清單中的封裝

當您建立 SharePoint 專案時，Visual Studio 會自動加入包含預設專案項目加入封裝的功能。 您可以使用封裝設計工具自訂 SharePoint 網站的專案工作清單設定。

1. 在  **SolutionExplorer**，開啟捷徑功能表**封裝**，然後選擇 **檢視表設計工具**。

2. 在 **名稱**方塊中，輸入**ProjectTaskListPackage**。

3. 選取 **重設 Web 伺服器**核取方塊。

## <a name="build-and-test-the-project-task-list"></a>建置和測試專案工作清單

當您執行專案時，會開啟 SharePoint 網站。 不過，您必須以手動方式瀏覽至工作清單的位置。

1. 選擇**F5**建置和部署專案工作清單的索引鍵。

     SharePoint 網站隨即開啟。

2. 選擇**首頁** 索引標籤。

3. 在左提要欄位中，選擇**專案工作清單**連結。

     專案工作清單 頁面隨即出現。

4. 在 [**清單工具**索引標籤上，選擇**項目**] 索引標籤。

5. 在 [**項目**群組中，選擇**新項目**] 按鈕。

6. 在 **標題**文字方塊中，輸入**Task1**。

7. 選擇**儲存** 按鈕。

     站台會重新整理之後， **Task1**工作會顯示 2009 年 7 月 1 日到期日。

8. 選擇**Task1**。

     工作的詳細的檢視隨即出現，並描述可讓您顯示 「 這是重要的工作 」。

## <a name="deploy-the-project-task-list"></a>部署專案工作清單

您建置和測試專案工作清單之後，您可以部署它*本機系統*或是*遠端系統*。 在本機系統是您用以開發方案，在同一部電腦，而遠端系統為不同的電腦。

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>若要部署到本機系統的專案工作清單

在 Visual Studio 功能表列上選擇 **建置** > **部署方案**。

Visual Studio 回收 IIS 應用程式集區、 撤銷方案的任何現有版本，將複製的方案套件 (*.wsp*) 到 SharePoint 的檔案，然後再啟動它的功能。 您現在可以在 SharePoint 中使用的解決方案。 如需有關部署組態步驟的詳細資訊，請參閱 <<c0> [ 如何： 編輯 SharePoint 部署組態](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)。

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>若要部署到遠端系統的專案工作清單

1. 在 Visual Studio 功能表列上選擇 **建置** > **發行**。

2. 在 **發佈**對話方塊方塊中，選擇**發行至檔案系統**選項按鈕。

     您可以變更的目標位置**發佈**對話方塊中，選擇省略符號按鈕![省略符號圖示](../sharepoint/media/ellipsisicon.gif "省略符號圖示")，然後巡覽至另一個位置。

3. 選擇**發佈** 按鈕。

     A *.wsp*方案建立檔案。

4. 複製 *.wsp*遠端 SharePoint 系統的檔案。

5. 使用 PowerShell`Add-SPUserSolution`命令，以將套件安裝在遠端 SharePoint 安裝。 (用於陣列方案`Add-SPSolution`命令。)

     例如，`Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`。

6. 使用 PowerShell`Install-SPUserSolution`命令來部署解決方案。 (用於陣列方案`Install-SPSolution`命令。)

     例如，`Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`。

     如需有關遠端部署的詳細資訊，請參閱[使用的解決方案](http://go.microsoft.com/fwlink/?LinkId=217680)並[加入和部署的方案，在 SharePoint 2010 中使用 PowerShell](http://go.microsoft.com/fwlink/?LinkId=217682)。

## <a name="next-steps"></a>後續步驟

您可以深入了解如何自訂和部署 SharePoint 方案，從下列主題：

- [逐步解說： 建立適用於 SharePoint 的網站資料行、 內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [如何： 建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)

- [SharePoint Server 2010 的 Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=217684)

## <a name="see-also"></a>另請參閱
[封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
