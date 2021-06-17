---
title: 使用 IntelliTrace 來將 SharePoint 應用程式進行偵錯工具
description: 使用 IntelliTrace 可更輕鬆地將 SharePoint 應用程式進行偵錯工具和修正。 建立程式碼，並將其加入至功能接收器。 測試專案。 收集 IntelliTrace 資料。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cf7fa6c7255e05c465d6c209db5e9581a49aee64
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112834"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>逐步解說：使用 IntelliTrace 來對 SharePoint 應用程式進行偵錯工具

藉由使用 IntelliTrace，您可以更輕鬆地進行 SharePoint 方案的偵錯工具。 傳統的偵錯工具目前只提供解決方案的快照。 不過，您可以使用 IntelliTrace 來檢查您的解決方案中發生的過去事件以及它們發生的內容，然後流覽至程式碼。

 本逐步解說示範如何使用 Microsoft Monitoring Agent，從已部署的應用程式收集 IntelliTrace 資料，以在 Visual Studio 中將 SharePoint 專案進行 debug 錯。 若要分析該資料，您必須使用 Visual Studio Enterprise。 此專案會併入功能接收器，在功能啟用時，會將工作新增至 [工作清單]，並將公告新增至 [公告] 清單。 停用此功能時，會將工作標示為已完成，並將第二個公告新增至公告清單中。 不過，此套裝程式含導致專案無法正確執行的邏輯錯誤。 藉由使用 IntelliTrace，您將會找出並更正錯誤。

 **適用于：** 本主題中的資訊適用于在 Visual Studio 中建立的 SharePoint 方案。

 本逐步解說將說明下列工作：

- [建立功能接收器](#create-a-feature-receiver)

- [將程式碼加入至功能接收器](#add-code-to-the-feature-receiver)

- [測試專案](#test-the-project)

- [使用 Microsoft Monitoring Agent 收集 IntelliTrace 資料](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [偵錯和修正 SharePoint 方案](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成這個逐步解說：

- 支援的 Windows 和 SharePoint 版本。

- Visual Studio Enterprise。

## <a name="create-a-feature-receiver"></a>建立功能接收器

首先，您要建立一個具有功能接收器的空白 SharePoint 專案。

1. 建立以您已安裝的 SharePoint 版本為目標的 SharePoint 方案專案，並將其命名為 **IntelliTraceTest**。

     [ **Sharepoint 自訂] Wizard** 隨即出現，您可以在其中指定專案的 SharePoint 網站和方案的信任層級。

2. 選擇 [ **部署為伺服器陣列方案** ] 選項按鈕，然後選擇 [ **完成]** 按鈕。

     IntelliTrace 只會在伺服器陣列方案上運作。

3. 在 **方案總管** 中，開啟 [ **功能** ] 節點的快捷方式功能表，然後選擇 [ **加入功能**]。

     *Feature1。功能* 隨即出現。

4. 開啟 Feature1 的快捷方式功能表，然後選擇 [ **加入事件接收器** ]，將程式碼模組加入至功能。

## <a name="add-code-to-the-feature-receiver"></a>將程式碼新增至功能接收器

接下來，將程式碼新增至功能接收器中的兩個方法： `FeatureActivated` 和 `FeatureDeactivating` 。 每次在 SharePoint 中啟用或停用功能時，都會觸發這些方法。

1. 在類別的頂端 `Feature1EventReceiver` ，新增下列程式碼，此程式碼會宣告指定 SharePoint 網站和子網站的變數：

    ```vb
    ' SharePoint site and subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site and subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

2. 以下列程式碼取代 `FeatureActivated` 方法：

    ```vb
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")
                    Dim taskList As SPList = web.Lists("Tasks")

                    ' Add an announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Add a task to the Task list.
                    Dim newTask As SPListItem = taskList.Items.Add()
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)
                    newTask.Update()
                End Using
            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureActivated(SPFeatureReceiverProperties properties)
    {
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList announcementsList = web.Lists["Announcements"];
                    SPList taskList = web.Lists["Tasks"];

                    // Add an announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Add a task to the Task list.
                    SPListItem newTask = taskList.Items.Add();
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;
                    newTask.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }

    }
    ```

3. 以下列程式碼取代 `FeatureDeactivating` 方法：

    ```vb
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)
        ' The following line induces an error to demonstrate debugging.
        ' Remove this line later for proper operation.
        Throw New System.InvalidOperationException("Serious error occurred!")
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim taskList As SPList = web.Lists("Tasks")
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add an announcement that the feature was deactivated.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Find the task that the feature receiver added to the Task list when the
                    ' feature was activated.
                    Dim qry As New SPQuery()
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)

                    For Each taskItem As SPListItem In taskItems
                        ' Mark the task as complete.
                        taskItem("PercentComplete") = 1
                        taskItem("Status") = "Completed"
                        taskItem.Update()
                    Next
                End Using

            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)
    {
        // The following line induces an error to demonstrate debugging.
        // Remove this line later for proper operation.
        throw new System.InvalidOperationException("A serious error occurred!");
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList taskList = web.Lists["Tasks"];
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add an announcement that the feature was deactivated.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Find the task that the feature receiver added to the Task list when the
                    // feature was activated.
                    SPQuery qry = new SPQuery();
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";
                    SPListItemCollection taskItems = taskList.GetItems(qry);

                    foreach (SPListItem taskItem in taskItems)
                    {
                        // Mark the task as complete.
                        taskItem["PercentComplete"] = 1;
                        taskItem["Status"] = "Completed";
                        taskItem.Update();
                    }
                }
            }

        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

## <a name="test-the-project"></a>測試專案

現在已將程式碼新增至功能接收器，且資料收集器正在執行，請部署和執行 SharePoint 方案來測試它是否正常運作。

> [!IMPORTANT]
> 在此範例中，FeatureDeactivating 事件處理常式中會擲回錯誤。 稍後在此逐步解說中，您會使用資料收集器所建立的 .Itrace 檔案來找出此錯誤。

1. 將方案部署到 SharePoint，然後在瀏覽器中開啟 SharePoint 網站。

     這項功能會自動啟動，使其功能接收器新增公告和工作。

2. 顯示 [公告] 和 [工作] 清單的內容。

     公告清單應該會有一個名為「已啟動 **功能： IntelliTraceTest_Feature1**」的新宣告，而 [工作] 清單應該有一個名為 [ **停用功能： IntelliTraceTest_Feature1**] 的新工作。 如果其中一個專案遺失，請確認此功能是否已啟用。 如果未啟用，請加以啟用。

3. 藉由執行下列步驟來停用功能：

   1. 在 SharePoint 的 [ **網站動作** ] 功能表上，選擇 [ **網站設定**]。

   2. 在 [ **網站動作**] 下，選擇 [ **管理網站功能** ] 連結。

   3. 選擇 [ **IntelliTraceTest Feature1**] 旁的 [ **停用** ] 按鈕。

   4. 在 [警告] 頁面上，選擇 [ **停用此功能** ] 連結。

      FeatureDeactivating () 事件處理常式會擲回錯誤。

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>使用 Microsoft Monitoring Agent 收集 IntelliTrace 資料

如果您將 Microsoft Monitoring Agent 安裝在執行 SharePoint 的系統上，您可以使用比 IntelliTrace 傳回的一般資訊更明確的資料，來對 SharePoint 方案進行 debug。 當您的 SharePoint 方案執行時，代理程式會使用 PowerShell Cmdlet 來捕捉 debug 資訊，以在 Visual Studio 外部運作。

> [!NOTE]
> 本節中的設定資訊是此範例特有的。 如需其他設定選項的詳細資訊，請參閱 [使用 IntelliTrace 獨立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)。

1. 在執行 SharePoint 的電腦上， [設定 Microsoft Monitoring Agent 並開始監視您的解決方案](../debugger/using-the-intellitrace-stand-alone-collector.md)。

2. 停用功能：

   1. 在 SharePoint 的 [ **網站動作** ] 功能表上，選擇 [ **網站設定**]。

   2. 在 [ **網站動作**] 下，選擇 [ **管理網站功能** ] 連結。

   3. 選擇 [ **IntelliTraceTest Feature1**] 旁的 [ **停用** ] 按鈕。

   4. 在 [警告] 頁面上，選擇 [ **停用此功能** ] 連結。

      在此情況下， (發生錯誤，因為在 FeatureDeactivating () 事件處理常式) 中擲出錯誤。

3. 在 PowerShell 視窗中，執行 [stop-webapplicationmonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) 命令來建立 .itrace 檔案、停止監視，然後重新開機您的 SharePoint 方案。

     **Stop-webapplicationmonitoring***" \<SharePointSite> \\<SharePointAppName \> "*  

## <a name="debug-and-fix-the-sharepoint-solution"></a>偵錯工具並修正 SharePoint 方案

現在您可以在 Visual Studio 中查看 IntelliTrace 記錄檔，以尋找並修正 SharePoint 方案中的錯誤。

1. 在 [\IntelliTraceLogs] 資料夾中，開啟 Visual Studio 中的 .Itrace 檔案。

     [ **IntelliTrace 摘要** ] 頁面隨即出現。 因為未處理錯誤，所以 GUID)  (的 SharePoint 相互關聯識別碼會出現在 [ **分析** ] 區段的未處理例外狀況區域中。 如果您想要查看發生錯誤的呼叫堆疊，請選擇 [ **呼叫堆疊** ] 按鈕。

2. 選擇 [ **Debug 例外** 狀況] 按鈕。

     如果出現提示，請載入符號檔。 在 [ **IntelliTrace** ] 視窗中，例外狀況會反白顯示為「擲回：發生嚴重錯誤！」。

     在 [IntelliTrace] 視窗中，選擇例外狀況以顯示失敗的程式碼。

3. 若要修正錯誤，請開啟 SharePoint 方案，然後在 FeatureDeactivating () 程式頂端批註化或移除 **throw** 語句。

4. 在 Visual Studio 中重建方案，然後將它重新部署到 SharePoint。

5. 藉由執行下列步驟來停用功能：

    1. 在 SharePoint 的 [ **網站動作** ] 功能表上，選擇 [ **網站設定**]。

    2. 在 [ **網站動作**] 下，選擇 [ **管理網站功能** ] 連結。

    3. 選擇 [ **IntelliTraceTest Feature1**] 旁的 [ **停用** ] 按鈕。

    4. 在 [警告] 頁面上，選擇 [ **停用此功能** ] 連結。

6. 開啟 [工作清單]，並確認 [停用] 工作的 [ **狀態** ] 值為 [已完成]，而且其 [ **完成的百分比** ] 值為100%。

     程式碼現在會正確執行。

## <a name="see-also"></a>另請參閱

- [驗證和偵錯工具代碼](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [逐步解說：使用單元測試來驗證 SharePoint 程式碼](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))
