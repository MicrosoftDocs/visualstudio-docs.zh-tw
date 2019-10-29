---
title: 建立 & 的 debug SharePoint 工作流程方案
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0e62226147fc160c6d967115fbd3aaa52dd69995
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985070"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>逐步解說：建立和調試 SharePoint 工作流程方案
  本逐步解說示範如何建立基本的順序工作流程範本。 工作流程會檢查共用文件庫的屬性，以判斷是否已審核檔。 如果檔已經過審核，工作流程就會完成。

 這個逐步解說將說明下列工作：

- 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中建立 SharePoint 清單定義的順序工作流程專案。

- 建立工作流程活動。

- 處理工作流程活動事件。

> [!NOTE]
> 雖然本逐步解說使用的是連續的工作流程專案，但狀態機器工作流程專案的程式是相同的。
>
> 此外，您的電腦可能會針對下列指示中的某些 Visual Studio 使用者介面元素，顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>Prerequisites
 您需要下列元件才能完成此逐步解說：

- 支援的 Microsoft Windows 和 SharePoint 版本。

- Visual Studio。

## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>將屬性加入至 SharePoint 共用文件庫
 為了追蹤**共用文件**庫中檔的審核狀態，我們將在 SharePoint 網站上建立共用檔的三個新屬性： `Status`、`Assignee`和 `Review Comments`。 我們會在**共用文件**庫中定義這些屬性。

#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>將屬性加入至 SharePoint 共用文件庫

1. 在網頁瀏覽器中開啟 SharePoint 網站，例如 HTTP://\<系統名稱 >/SitePages/Home.aspx。

2. 在 [快速啟動] 列上，選擇 [ **SharedDocuments**]。

3. 選擇 [文檔**庫工具**] 功能區上的 [連結**庫**]，然後選擇功能區上的 [**建立資料行**] 按鈕來建立新的資料行

4. 將資料行命名為 [**檔狀態**]，將其 [類型] 設定為 **[選擇] （可選擇的功能表）** ，指定下列三個選項，然後選擇 [**確定]** 按鈕：

    - **需要審查**

    - **審查完成**

    - **要求的變更**

5. 建立兩個以上的資料行，並將其命名為**受託**人和**審核批註**。 將 [受託人] 資料行類型設定為單行文字，並將 [審核批註] 資料行類型設為多行文字。

## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>讓檔在不需要簽出的情況下進行編輯
 當您可以編輯檔，而不需要將它們簽出時，測試工作流程範本會比較容易。在下一個程式中，您會設定 SharePoint 網站來啟用該功能。

#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>若要讓檔在不簽出的情況下進行編輯

1. 在 [快速啟動] 列上，選擇 [**共用檔**] 連結。

2. 在 [連結**庫工具**] 功能區上，選擇 [連結**庫**] 索引標籤，然後選擇 [連結**庫設定**] 按鈕以顯示 [**文件庫設定**] 頁面。

3. 在 [**一般設定**] 區段中，選擇 [**版本設定**] 連結，以顯示**版本設定**頁面。

4. 確認 [**需要先簽出檔才可編輯**] 的設定為 [**否**]。 如果不是，請將它變更為 [**否**]，然後選擇 [**確定]** 按鈕。

5. 關閉瀏覽器。

## <a name="create-a-sharepoint-sequential-workflow-project"></a>建立 SharePoint 順序工作流程專案
 連續工作流程是一組依序執行的步驟，直到最後一個活動完成為止。 在此程式中，我們會建立將套用至我們的共用文件清單的順序工作流程。 [工作流程] wizard 可讓您將工作流程與網站定義或清單定義產生關聯，並讓您判斷工作流程何時會開始。

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>若要建立 SharePoint 順序工作流程專案

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在功能表列上 **，選擇 [** 檔案]  >  [**新增** > **專案**]，以顯示 [**新增專案**] 對話方塊。

3. 展開 [**視覺效果C#**  ] 或 [ **Visual Basic**] 底下的 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

4. 在 [**範本**] 窗格中，選擇 [ **SharePoint 2010 專案**] 範本。

5. 在 [**名稱**] 方塊中，輸入**MySharePointWorkflow** ，然後選擇 [**確定]** 按鈕。

     [ **SharePoint 自訂嚮導]** 隨即出現。

6. 在 [**指定網站和安全性層級進行偵錯工具**] 頁面中，選擇 [**部署為數組方案**] 選項按鈕，然後選擇 [**完成]** 按鈕以接受信任層級和預設網站。

     此步驟會將解決方案的信任層級設定為伺服器陣列方案，這是工作流程專案的唯一可用選項。 如需詳細資訊，請參閱[沙箱化方案考慮](../sharepoint/sandboxed-solution-considerations.md)。

7. 在**方案總管**中，選擇專案節點，然後在功能表列上，選擇 [**專案** > **加入新專案**]。

8. 在 [**視覺C#效果**] 或 [ **Visual Basic**] 底下，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

9. 在 [**範本**] 窗格中，選擇 [**順序工作流程（僅限陣列方案）** ] 範本，然後選擇 [**新增**] 按鈕。

     [ **SharePoint 自訂嚮導]** 隨即出現。

10. 在 [**指定用於偵錯工具的工作流程名稱**] 頁面中，接受預設名稱（**MySharePointWorkflow-workflow1.xaml**）。 保留預設工作流程範本類型 [值]、[**清單工作流程**]，然後選擇 [**下一步]** 按鈕。

11. 在 [**您要 Visual Studio 自動將工作流程關聯到 debug 會話嗎？** ] 頁面中，選擇 [**下一步]** 按鈕接受所有預設設定。

     此步驟會自動將工作流程與共享文件庫產生關聯。

12. 在 [**指定工作流程的啟動方式**] 頁面中，保留在 [**您要如何啟動工作流程？** ] 區段中選取的預設選項，然後選擇 [**完成]** 按鈕。

     此頁面可讓您指定工作流程何時啟動。 根據預設，當使用者在 SharePoint 中手動啟動工作流程，或建立與工作流程相關聯的專案時，就會啟動工作流程。

## <a name="create-workflow-activities"></a>建立工作流程活動
 工作流程包含一或多個代表要執行之動作的*活動*。 使用工作流程設計工具來排列工作流程的活動。 在此程式中，我們會將兩個活動新增至工作流程： HandleExternalEventActivity 和 OnWorkFlowItemChanged。 這些活動會監視**共用文件**清單中檔的審查狀態

#### <a name="to-create-workflow-activities"></a>若要建立工作流程活動

1. 工作流程應該會顯示在工作流程設計工具中。 如果不是，請在**方案總管**中開啟**Workflow1.cs**或**workflow1.xaml** 。

2. 在設計工具中，選擇 [ **OnWorkflowActivated1** ] 活動。

3. 在 [**屬性**] 視窗中，于 [叫用 **] 屬性旁**輸入**onWorkflowActivated** ，然後選擇 enter 鍵。

     [程式碼編輯器] 隨即開啟，並在 Workflow1.xaml 程式碼檔案中加入名為 onWorkflowActivated 的事件處理常式方法。

4. 切換回工作流程設計工具，開啟 [工具箱]，然後展開 [ **Windows workflow v3.0** ] 節點。

5. 在 [**工具箱**] 的 [ **Windows Workflow v3.0** ] 節點中，執行下列其中一組步驟：

    1. 開啟**While**活動的快捷方式功能表，然後選擇 [**複製**]。 在工作流程設計工具中，開啟 [ **onWorkflowActivated1** ] 活動底下行的快捷方式功能表，然後選擇 [**貼**上]。

    2. 從 [工具箱] 將 [ **While** ] 活動拖曳至工作流程設計**工具**，並將活動連接至 [ **onWorkflowActivated1** ] 活動底下的那一行。

6. 選擇 [ **WhileActivity1** ] 活動。

7. 在 [**屬性**] 視窗中，將 [**條件**] 設定為 [程式碼條件]。

8. 展開 [**條件**] 屬性，在 [子**條件**] 屬性旁輸入**isWorkflowPending** ，然後選擇 enter 鍵。

     [程式碼編輯器] 隨即開啟，而且名為 isWorkflowPending 的方法會新增至 Workflow1.xaml 程式碼檔案。

9. 切換回工作流程設計工具，開啟 [工具箱]，然後展開 [ **SharePoint 工作流程**] 節點。

10. 在 [**工具箱**] 的 [ **SharePoint 工作流程**] 節點中，執行下列其中一組步驟：

    - 開啟 [ **OnWorkflowItemChanged** ] 活動的快捷方式功能表，然後選擇 [**複製**]。 在工作流程設計工具中，開啟 [ **whileActivity1** ] 活動內行的快捷方式功能表，然後選擇 [**貼**上]。

    - 將 [ **OnWorkflowItemChanged** ] 活動從 [工具箱] 拖曳至工作流程設計**工具**，並將活動連接至**whileActivity1**活動內的那一行。

11. 選擇 [ **onWorkflowItemChanged1** ] 活動。

12. 在 [**屬性**] 視窗中，設定如下表所示的屬性。

    |屬性|值|
    |--------------|-----------|
    |**CorrelationToken**|**workflowToken**|
    |**調用**|**onWorkflowItemChanged**|

## <a name="handle-activity-events"></a>處理活動事件
 最後，檢查每個活動的檔狀態。 如果檔已經過審核，則工作流程已完成。

#### <a name="to-handle-activity-events"></a>若要處理活動事件

1. 在*Workflow1.cs*或*workflow1.xaml*中，將下欄欄位新增至 `Workflow1` 類別的頂端。 活動中會使用此欄位來判斷工作流程是否已完成。

    ```vb
    Dim workflowPending As Boolean = True
    ```

    ```csharp
    Boolean workflowPending = true;
    ```

2. 將下列方法加入 `Workflow1` 類別。 這個方法會檢查 [檔] 清單中 [`Document Status`] 屬性的值，以判斷是否已審核檔。 如果 `Document Status` 屬性設定為 `Review Complete`，則 `checkStatus` 方法會將 `workflowPending` 欄位設定為**false** ，表示工作流程已準備好完成。

    ```vb
    Private Sub checkStatus()
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then
            workflowPending = False
        End If
    End Sub
    ```

    ```csharp
    private void checkStatus()
    {
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")
        workflowPending = false;
    }
    ```

3. 將下列程式碼新增至 `onWorkflowActivated` 和 `onWorkflowItemChanged` 方法，以呼叫 `checkStatus` 方法。 當工作流程啟動時，`onWorkflowActivated` 方法會呼叫 `checkStatus` 方法，以判斷檔是否已經過檢查。 如果尚未經過審核，工作流程就會繼續進行。 儲存檔時，`onWorkflowItemChanged` 方法會再次呼叫 `checkStatus` 方法，以判斷是否已審核檔。 當 [`workflowPending`] 欄位設定為 [ **true**] 時，工作流程會繼續執行。

    ```vb
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)
        checkStatus()
    End Sub

    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)
        checkStatus()
    End Sub
    ```

    ```csharp
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)
    {
        // Check the status.
        checkStatus();
    }

    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)
    {
        // Check the status.
        checkStatus();
    }
    ```

4. 將下列程式碼新增至 `isWorkflowPending` 方法，以檢查 `workflowPending` 屬性的狀態。 每次儲存檔時， **whileActivity1**活動都會呼叫 `isWorkflowPending` 方法。 這個方法會檢查 <xref:System.Workflow.Activities.ConditionalEventArgs> 物件的 <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> 屬性，以判斷**WhileActivity1**活動是否應該繼續或完成。 如果屬性設定為**true**，則活動會繼續。 否則，活動會完成，且工作流程會完成。

    ```vb
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)
        e.Result = workflowPending
    End Sub
    ```

    ```csharp
    private void isWorkflowPending(object sender, ConditionalEventArgs e)
    {
        e.Result = workflowPending;
    }
    ```

5. 儲存專案。

## <a name="test-the-sharepoint-workflow-template"></a>測試 SharePoint 工作流程範本
 當您啟動偵錯工具時，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將工作流程範本部署到 SharePoint 伺服器，並將工作流程與**共用文件**清單產生關聯。 若要測試工作流程，請從**共用文件**清單中的檔啟動工作流程的實例。

#### <a name="to-test-the-sharepoint-workflow-template"></a>測試 SharePoint 工作流程範本

1. 在*Workflow1.cs*或*workflow1.xaml*中，設定**onWorkflowActivated**方法旁的中斷點。

2. 選擇**F5**鍵以建立並執行方案。

     SharePoint 網站隨即出現。

3. 在 SharePoint 的流覽窗格中，選擇 [**共用文件**] 連結。

4. 在 [**共用檔**] 頁面中，選擇 [文檔**庫工具**] 索引標籤上的 [**檔**] 連結，然後選擇 [**上傳檔**] 按鈕。

5. 在 [**上傳檔**] 對話方塊中，選擇 [**流覽]** 按鈕，選擇任何檔檔，選擇 [**開啟**] 按鈕，然後選擇 [**確定]** 按鈕。

     這會將選取的檔上傳至 [**共用文件**] 清單並啟動工作流程。

6. 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中，確認偵錯工具會在 `onWorkflowActivated` 方法旁的中斷點停止。

7. 選擇**F5**鍵以繼續執行。

8. 您可以在這裡變更檔的設定，但現在請選擇 [**儲存**] 按鈕，將它們保留為預設值。

     這會回到預設 SharePoint 網站的 [**共用檔**] 頁面。

9. 在 [**共用檔**] 頁面中，確認 [ **MySharePointWorkflow-workflow1.xaml** ] 資料行底下的值已設定為 [**進行中**]。 這表示工作流程正在進行中，而且檔正在等待審核。

10. 在 [**共用檔**] 頁面中，選擇檔，選擇出現的箭號，然後選擇 [**編輯屬性**] 功能表項目。

11. 將 [**檔狀態**] 設定為 [**完整審查**]，然後選擇 [**儲存**] 按鈕。

     這會回到預設 SharePoint 網站的 [**共用檔**] 頁面。

12. 在 [**共用檔**] 頁面中，確認 [**檔狀態**] 欄底下的值已設定為 [**檢查完成**]。 重新整理 [**共用檔**] 頁面，並確認 [ **MySharePointWorkflow-workflow1.xaml** ] 資料行底下的值已設定為 [**已完成**]。 這表示工作流程已完成，而且已審核檔。

## <a name="next-steps"></a>後續步驟
 您可以從下列主題深入瞭解如何建立工作流程範本：

- 若要深入瞭解 SharePoint 工作流程活動，請參閱[Sharepoint Foundation 的工作流程活動](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14))。

- 若要深入瞭解 Windows Workflow Foundation 活動，請參閱[System.web 命名空間](/dotnet/api/system.workflow.activities&view=netframework-4.8)。

## <a name="see-also"></a>請參閱
- [建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [SharePoint 專案與專案專案範本](../sharepoint/sharepoint-project-and-project-item-templates.md)
- [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)
