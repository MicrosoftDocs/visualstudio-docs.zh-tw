---
title: "逐步解說： 在 SharePoint 應用程式使用 IntelliTrace 偵錯 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 03afad9971a938a88df624f24e5553abbdc0f976
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-debugging-a-sharepoint-application-by-using-intellitrace"></a>逐步解說：使用 IntelliTrace 偵錯 SharePoint 應用程式
  藉由使用 IntelliTrace，您可以更輕鬆地偵錯 SharePoint 方案。 傳統偵錯工具可讓您方案的快照集在目前時間。 不過，您可以使用 IntelliTrace 來檢閱過去您方案中發生的事件和它們發生並巡覽至程式碼的內容。  
  
 本逐步解說示範如何使用 Microsoft Monitoring Agent 收集 IntelliTrace 資料，從已部署的應用程式偵錯在 Visual Studio Ultimate 中的 SharePoint 2010 或 SharePoint 2013 專案。 若要分析的資料，您必須使用 Visual Studio Ultimate。 此專案包含功能接收器，以便啟動此功能時，將工作加入工作清單以及公告來公告清單。 功能已停用時，工作會標示為已完成，以及公告清單中加入第二個宣告。 不過，此程序包含邏輯的錯誤，導致專案無法正確執行。 藉由使用 IntelliTrace，您將會找出並修正錯誤。  
  
 **適用於：**本主題資訊適用於 SharePoint 2010 和 SharePoint 2013 方案在 Visual Studio 中建立。  
  
 這個逐步解說將說明下列工作：  
  
-   [建立功能接收器](#BKMK_CreateReceiver)  
  
-   [將程式碼加入至功能接收器](#BKMK_AddCode)  
  
-   [測試專案](#BKMK_Test1)  
  
-   [使用 Microsoft Monitoring Agent 收集 IntelliTrace 資料](#BKMK_CollectDiagnosticData)  
  
-   [偵錯和修正 SharePoint 方案](#BKMK_DebugSolution)  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Windows 版本和 SharePoint。 請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio Ultimate。  
  
##  <a name="BKMK_CreateReceiver"></a>建立功能接收器  
 首先，您會建立空白的 SharePoint 專案的功能接收器。  
  
#### <a name="to-create-a-feature-receiver"></a>若要建立功能接收器  
  
1.  建立 SharePoint 2010 或 SharePoint 2013 方案專案，並將其命名**IntelliTraceTest**。  
  
     **SharePoint 自訂精靈**出現時，您可以在此指定您的專案和方案的信任層級的 SharePoint 網站。  
  
2.  選擇**部署為伺服陣列方案**選項按鈕，然後再選擇**完成** 按鈕。  
  
     IntelliTrace 只會針對伺服器陣列方案運作。  
  
3.  在**方案總管 中**，開啟捷徑功能表**功能** 節點，然後選擇 **加入功能**。  
  
     Feature1.feature 隨即出現。  
  
4.  如 Feature1.feature，開啟捷徑功能表，然後選擇**加入事件接收器**来加入的程式碼模組的功能。  
  
##  <a name="BKMK_AddCode"></a>將程式碼加入至功能接收器  
 接下來，將程式碼加入至功能接收器中的兩個方法：`FeatureActivated`和`FeatureDeactivating`。 啟用或停用在 SharePoint 中，分別功能時，觸發程序這些方法。  
  
#### <a name="to-add-code-to-the-feature-receiver"></a>若要將程式碼加入至功能接收器  
  
1.  在頂端`Feature1EventReceiver`類別中，加入下列程式碼會宣告指定 SharePoint 網站和子網站的變數：  
  
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
  
2.  以下列程式碼取代 `FeatureActivated` 方法：  
  
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
  
3.  以下列程式碼取代 `FeatureDeactivating` 方法：  
  
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
  
##  <a name="BKMK_Test1"></a>測試專案  
 現在，程式碼會加入至功能接收器，並執行資料收集器，部署和執行 SharePoint 方案來測試是否運作正常。  
  
> [!IMPORTANT]  
>  例如，FeatureDeactivating 事件處理常式中擲回錯誤。 稍後在本逐步解說中，您可以找到此錯誤使用資料收集器建立.iTrace 檔案。  
  
#### <a name="to-test-the-project"></a>測試專案  
  
1.  將方案部署到 SharePoint，然後在瀏覽器中開啟 SharePoint 網站。  
  
     此功能會自動啟動，導致其功能接收器，將公告和工作。  
  
2.  顯示 公告 和 工作清單的內容。  
  
     公告清單應該有一項新公告，名為**啟動功能： IntelliTraceTest_Feature1**，而且 [工作] 清單應該會有新的工作，名為**停用功能： IntelliTraceTest_Feature1**。 如果任一項目遺失，請確認是否啟用此功能。 如果它是不會啟動，請將它啟用。  
  
3.  停用此功能藉由執行下列步驟：  
  
    1.  在**網站動作**功能表在 SharePoint 中，選擇 **站台設定**。  
  
    2.  在下**網站動作**，選擇**管理網站功能**連結。  
  
    3.  旁邊**IntelliTraceTest Feature1**，選擇**停用** 按鈕。  
  
    4.  在警告頁面上，選擇 **停用這項功能**連結。  
  
     FeatureDeactivating() 事件處理常式擲回錯誤。  
  
##  <a name="BKMK_CollectDiagnosticData"></a>使用 Microsoft Monitoring Agent 收集 IntelliTrace 資料  
 如果您執行 SharePoint 的系統上安裝 Microsoft Monitoring Agent，您可以使用 IntelliTrace 傳回的一般資訊比更特定的資料來偵錯 SharePoint 方案。 代理程式適用於 Visual Studio 之外，使用 PowerShell cmdlet 來擷取您的 SharePoint 方案執行時偵錯資訊。  
  
> [!NOTE]  
>  本節中的組態資訊是此範例中的特定項目。 如需其他組態選項的詳細資訊，請參閱[使用 IntelliTrace 獨立收集器](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector)。  
  
1.  執行 SharePoint，在電腦上[設定 Microsoft Monitoring Agent 並開始監視您的方案](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector)。  
  
2.  停用功能：  
  
    1.  在**網站動作**功能表在 SharePoint 中，選擇 **站台設定**。  
  
    2.  在下**網站動作**，選擇**管理網站功能**連結。  
  
    3.  旁邊**IntelliTraceTest Feature1**，選擇**停用** 按鈕。  
  
    4.  在警告頁面上，選擇 **停用這項功能**連結。  
  
     （在此情況下，由於 FeatureDeactivating() 事件處理常式中擲回的錯誤），就會發生錯誤。  
  
3.  在 PowerShell 視窗中，執行[Stop-webapplicationmonitoring](http://go.microsoft.com/fwlink/?LinkID=313687)建立.iTrace 檔案，停止監視，然後重新啟動您的 SharePoint 方案的命令。  
  
     **Stop-webapplicationmonitoring***"\<SharePointSite >\\< SharePointAppName\>"*   
  
##  <a name="BKMK_DebugSolution"></a>偵錯和修正 SharePoint 方案  
 現在您可以在 Visual Studio 中尋找和修正 SharePoint 方案中的錯誤檢視 IntelliTrace 記錄檔。  
  
#### <a name="to-debug-and-fix-the-sharepoint-solution"></a>若要偵錯和修正 SharePoint 方案  
  
1.  在 [\IntelliTraceLogs] 資料夾中，開啟 Visual Studio 中的.iTrace 檔案。  
  
     **IntelliTrace 摘要**頁面隨即出現。 未處理錯誤，因為 SharePoint 相互關聯識別碼 (GUID) 會出現在未處理例外狀況 區域中**分析**> 一節。 選擇**呼叫堆疊**按鈕，如果您想要檢視呼叫堆疊發生錯誤。  
  
2.  選擇**偵錯例外狀況** 按鈕。  
  
     如果出現提示，請載入符號檔。 在**IntelliTrace**視窗中，例外狀況會反白顯示為 「 擲回： 發生嚴重錯誤 ！"。  
  
     在 IntelliTrace 視窗中，選擇要顯示失敗的程式碼的例外狀況。  
  
3.  開啟 SharePoint 方案然後標記為註解或移除來修正錯誤**擲回**頂端 FeatureDeactivating() 程序的陳述式。  
  
4.  重建方案在 Visual Studio，然後將它重新部署至 SharePoint。  
  
5.  停用此功能藉由執行下列步驟：  
  
    1.  在**網站動作**功能表在 SharePoint 中，選擇 **站台設定**。  
  
    2.  在下**網站動作**，選擇**管理網站功能**連結。  
  
    3.  旁邊**IntelliTraceTest Feature1**，選擇**停用** 按鈕。  
  
    4.  在警告頁面上，選擇 **停用這項功能**連結。  
  
6.  開啟工作清單中，並確認**狀態**停用工作的值 「 已完成 」 及其**完成百分比**值為 100%。  
  
     程式碼現在會正確地執行。  
  
## <a name="see-also"></a>請參閱  
 [驗證及偵錯 SharePoint 程式碼](../sharepoint/verifying-and-debugging-sharepoint-code.md)   
 [IntelliTrace](/visualstudio/debugger/intellitrace)   
 [逐步解說： 使用單元測試驗證 SharePoint 程式碼](https://msdn.microsoft.com/en-us/library/gg599006(v=vs.100).aspx)  
  
  