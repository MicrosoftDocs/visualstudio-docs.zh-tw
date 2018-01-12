---
title: "逐步解說： 建立和 SharePoint 工作流程方案進行偵錯 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 687116b1fc7f3ad935583b41ff9c19d2d5d13613
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-and-debugging-a-sharepoint-workflow-solution"></a>逐步解說：建立並偵錯 SharePoint 工作流程方案
  本逐步解說示範如何建立基本的循序工作流程範本。 工作流程會檢查共用的文件庫來判斷是否經過審閱文件的屬性。 如果已檢閱文件，工作流程完成。  
  
 這個逐步解說將說明下列工作：  
  
-   建立 SharePoint 清單定義循序工作流程專案中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
-   建立工作流程活動。  
  
-   處理工作流程活動事件。  
  
> [!NOTE]  
>  雖然本逐步解說使用循序工作流程專案，程序是相同的狀態機器工作流程專案。  
>   
>  此外，您的電腦可能會顯示不同的名稱或位置的某些 Visual Studio 使用者介面項目中的下列指示。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Microsoft Windows 和 SharePoint 版本。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## <a name="adding-properties-to-the-sharepoint-shared-documents-library"></a>將屬性加入至 SharePoint 共用文件庫  
 若要追蹤的文件中的檢閱狀態**共用文件**程式庫，我們會在 SharePoint 網站上建立共用文件的三個新屬性： `Status`， `Assignee`，和`Review Comments`。 我們會定義中的這些屬性**Shared Documents**程式庫。  
  
#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>若要將屬性加入至 SharePoint 共用文件庫  
  
1.  開啟 SharePoint 網站，例如 http://\<系統名稱 > / SitePages/Home.aspx，網頁瀏覽器中的。  
  
2.  在 快速啟動 列上選擇  **SharedDocuments**。  
  
3.  選擇**文件庫**上**文件庫工具**功能區，然後選擇 **建立資料行**来建立新的資料行的功能區上的按鈕。  
  
4.  名稱資料行**文件狀態**，將其類型設**選擇 （功能表可從中選擇）**，並指定下列三種選擇，然後選擇**確定**按鈕：  
  
    -   **需要檢視**  
  
    -   **完成檢閱**  
  
    -   **變更要求**  
  
5.  建立兩個的多個資料行並將它們命名**Assignee**和**檢閱註解**。 設定 Assignee 資料行類型為單行文字，並檢閱註解的資料行類型為多行文字。  
  
## <a name="enabling-documents-to-be-edited-without-requiring-a-check-out"></a>啟用編輯而不需要簽出文件  
 它是您可以編輯的文件，而不需要簽出時，測試工作流程範本的工作變得更容易。在下一個程序中，您可以設定 SharePoint 網站，若要啟用的。  
  
#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>若要啟用簽出才能編輯的文件  
  
1.  在 快速啟動 列上選擇  **Shared Documents**連結。  
  
2.  在**文件庫工具**功能區中，選擇**文件庫**索引標籤，然後選擇 [**文件庫設定**] 按鈕以顯示**文件庫設定**頁面。  
  
3.  在**一般設定**區段中，選擇**版本設定**連結可以顯示**版本設定**頁面。  
  
4.  確認設定**需要先簽出才能進行編輯的文件**是**否**。 如果不是，將它變更為**否**，然後選擇 [**確定**] 按鈕。  
  
5.  關閉瀏覽器。  
  
## <a name="creating-a-sharepoint-sequential-workflow-project"></a>建立 SharePoint 循序工作流程專案  
 循序工作流程是一組步驟，直到最後一個活動完成執行順序。 在此程序中，我們建立循序工作流程，會套用至我們的共用文件清單。 工作流程精靈可讓您與網站定義或清單定義關聯工作流程，並可讓您決定當工作流程會開始。  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>若要建立 SharePoint 循序工作流程專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上選擇 [**檔案**，**新增**，**專案**顯示**新專案**] 對話方塊。  
  
3.  展開**SharePoint**節點之下**Visual C#**或**Visual Basic**，然後選擇  **2010年**節點。  
  
4.  在**範本** 窗格中，選擇**SharePoint 2010 專案**範本。  
  
5.  在**名稱**方塊中，輸入**MySharePointWorkflow** ，然後選擇 [**確定**] 按鈕。  
  
     **SharePoint 自訂精靈**隨即出現。  
  
6.  在**指定偵錯的網站和安全性層級**頁面上，選擇**部署為伺服陣列方案**選項按鈕，然後再選擇**完成**接受按鈕信任層級和預設站台。  
  
     此步驟會設定為伺服器陣列方案，唯一可用的選項的工作流程專案方案的信任層級。 如需詳細資訊，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
7.  在**方案總管] 中**，選擇專案節點，然後在功能表列上選擇 [**專案**，**加入新項目**。  
  
8.  之下**Visual C#**或**Visual Basic**，依序展開**SharePoint** ] 節點，然後選擇 [ **2010年**節點。  
  
9. 在**範本** 窗格中，選擇**循序工作流程 （僅限陣列方案）**範本，然後選擇 **新增** 按鈕。  
  
     **SharePoint 自訂精靈**隨即出現。  
  
10. 在**指定偵錯的工作流程名稱**頁面上，接受預設名稱 (**MySharePointWorkflow-Workflow1**)。 保留預設流程範本類型值**清單工作流程**，然後選擇 [**下一步**] 按鈕。  
  
11. 在**您希望 Visual Studio 自動關聯工作流程偵錯工作階段中？**頁面上，選擇**下一步** 按鈕，接受所有預設設定。  
  
     此步驟會自動將共用文件庫與關聯工作流程。  
  
12. 在**指定條件的工作流程的啟動方式**頁面上，保留預設選項中選取**您要如何啟動工作流程？**區段，並選擇**完成**  按鈕。  
  
     此頁面可讓您指定您的工作流程啟動時執行。 根據預設，啟動工作流程是當使用者手動啟動它在 SharePoint，或建立工作流程的相關聯的項目時。  
  
## <a name="creating-workflow-activities"></a>建立工作流程活動  
 工作流程包含一或多個*活動*，代表要執行的動作。 使用工作流程設計工具來排列工作流程的活動。 在此程序中，我們將會加入兩個活動在工作流程： HandleExternalEventActivity 和 OnWorkFlowItemChanged。 這些活動監控中的文件的檢閱狀態**Shared Documents**清單  
  
#### <a name="to-create-workflow-activities"></a>若要建立工作流程活動  
  
1.  工作流程應該顯示在工作流程設計工具中。 如果不存在，然後開啟 [ **Workflow1.cs**或**Workflow1.vb**中**方案總管] 中**。  
  
2.  在設計工具中，選擇  **OnWorkflowActivated1**活動。  
  
3.  在**屬性**視窗中，輸入**onWorkflowActivated**旁**叫用**屬性，然後選擇 Enter 鍵。  
  
     程式碼編輯器隨即開啟，並將名為 onWorkflowActivated 的事件處理常式方法加入 Workflow1 程式碼檔案。  
  
4.  切換回到工作流程設計工具中，開啟工具箱，接著展開**Windows Workflow v3.0**節點。  
  
5.  在**Windows Workflow v3.0**節點**工具箱**，執行下列一組步驟：  
  
    1.  開啟快顯功能表**時**活動，然後選擇 **複製**。 在工作流程設計工具中，開啟 在下一行的捷徑功能表**onWorkflowActivated1**活動，然後選擇 **貼上**。  
  
    2.  拖曳**時**活動從**工具箱**至工作流程設計工具中，並連接到下一行的活動**onWorkflowActivated1**活動。  
  
6.  選擇**WhileActivity1**活動。  
  
7.  在**屬性**視窗中，將**條件**至程式碼的條件。  
  
8.  展開**條件**屬性中，輸入**isWorkflowPending**旁邊子**條件**屬性，然後選擇 Enter 鍵。  
  
     程式碼編輯器隨即開啟，並將名為 isWorkflowPending 的方法加入 Workflow1 程式碼檔案。  
  
9. 切換回到工作流程設計工具中，開啟工具箱，接著展開**SharePoint 工作流程**節點。  
  
10. 在**SharePoint 工作流程**節點**工具箱**，執行下列一組步驟：  
  
    -   開啟快顯功能表**OnWorkflowItemChanged**活動，然後選擇 **複製**。 在工作流程設計工具中，開啟 內的一行的捷徑功能表**whileActivity1**活動，然後選擇 **貼上**。  
  
    -   拖曳**OnWorkflowItemChanged**活動從**工具箱**至工作流程設計工具中，並連接活動內的一行來**whileActivity1**活動。  
  
11. 選擇**onWorkflowItemChanged1**活動。  
  
12. 在**屬性**視窗中，設定屬性下, 表所示。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**CorrelationToken**|**workflowToken**|  
    |**叫用**|**onWorkflowItemChanged**|  
  
## <a name="handling-activity-events"></a>處理活動事件  
 最後，檢查每個活動來自的文件的狀態。 如果已檢閱文件，工作流程已結束。  
  
#### <a name="to-handle-activity-events"></a>處理活動事件  
  
1.  在 Workflow1.cs 或 Workflow1.vb，將下列欄位加入至頂端`Workflow1`類別。 這個欄位是在活動中用來判斷是否已完成工作流程。  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  將下列方法加入 `Workflow1` 類別中。 這個方法會檢查值`Document Status`文件清單，以判斷是否經過審閱文件的屬性。 如果`Document Status`屬性設定為`Review Complete`，然後在`checkStatus`方法會設定`workflowPending`欄位設為**false**來指示工作流程已完成。  
  
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
  
3.  將下列程式碼加入`onWorkflowActivated`和`onWorkflowItemChanged`方法呼叫`checkStatus`方法。 當工作流程啟動時，`onWorkflowActivated`方法呼叫`checkStatus`方法，以判斷是否經過審閱文件。 如果它尚未檢視，會繼續工作流程。 儲存文件時，`onWorkflowItemChanged`方法呼叫`checkStatus`方法一次，判斷是否經過審閱文件。 雖然`workflowPending`欄位設定為**true**，工作流程會繼續執行。  
  
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
  
4.  將下列程式碼加入`isWorkflowPending`方法來檢查的狀態`workflowPending`屬性。 儲存文件時，每次**whileActivity1**活動呼叫`isWorkflowPending`方法。 這個方法會檢查<xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A>屬性<xref:System.Workflow.Activities.ConditionalEventArgs>物件，以判斷是否**WhileActivity1**活動事件應該繼續還是 [完成]。 如果屬性設定為**true**，活動會繼續。 否則，在活動完成，並在工作流程完成。  
  
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
  
5.  儲存專案。  
  
## <a name="testing-the-sharepoint-workflow-template"></a>測試 SharePoint 工作流程範本  
 當您啟動偵錯工具，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]將工作流程範本部署到 SharePoint 伺服器，並將相關聯的工作流程**Shared Documents**清單。 若要測試工作流程，開始的工作流程執行個體中的文件從**Shared Documents**清單。  
  
#### <a name="to-test-the-sharepoint-workflow-template"></a>若要測試 SharePoint 工作流程範本  
  
1.  在 Workflow1.cs 或 Workflow1.vb，設定中斷點旁**onWorkflowActivated**方法。  
  
2.  選擇 F5 鍵，建置並執行方案。  
  
     SharePoint 網站隨即出現。  
  
3.  在 SharePoint 中瀏覽窗格中，選擇  **Shared Documents**連結。  
  
4.  在**Shared Documents**頁面上，選擇**文件**連結**文件庫工具**索引標籤，然後選擇 **上傳文件**按鈕.  
  
5.  在**上傳文件**對話方塊方塊中，選擇**瀏覽**按鈕，選擇任何文件檔，選擇**開啟**按鈕，然後再選擇**確定**  按鈕。  
  
     這會將上傳到選取的文件**Shared Documents**清單，並啟動工作流程。  
  
6.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，確認，偵錯工具在中斷點停止旁`onWorkflowActivated`方法。  
  
7.  選擇 F5 鍵繼續執行。  
  
8.  您可以變更的設定文件，但保留這些預設值現在藉由選擇**儲存** 按鈕。  
  
     這時會回到**Shared Documents**預設 SharePoint 網站的網頁。  
  
9. 在**Shared Documents**頁面上，確認下方值**MySharePointWorkflow-Workflow1**資料行設為**進行中**。 這表示工作流程正在進行中，而且文件正在等候檢視。  
  
10. 在**Shared Documents**頁面上，選擇 文件，選擇箭號，隨即出現，然後選擇 **編輯內容**功能表項目。  
  
11. 設定**文件狀態**至**檢視完成**，然後選擇 [**儲存**] 按鈕。  
  
     這時會回到**Shared Documents**預設 SharePoint 網站的網頁。  
  
12. 在**共用文件**頁面上，確認下方值**文件狀態**資料行設為**檢視完成**。 重新整理**Shared Documents**頁面上，確認下方值**MySharePointWorkflow-Workflow1**資料行設為**已完成**。 這表示工作流程完成後，而且經過審閱文件。  
  
## <a name="next-steps"></a>後續步驟  
 您可以深入了解如何建立工作流程範本，從下列主題：  
  
-   若要深入了解 SharePoint 工作流程活動，請參閱[SharePoint foundation 工作流程活動](http://go.microsoft.com/fwlink/?LinkId=178992)。  
  
-   若要了解有關 Windows Workflow Foundation 活動的詳細資訊，請參閱[.net 命名空間](http://go.microsoft.com/fwlink/?LinkId=178993)。  
  
## <a name="see-also"></a>請參閱  
 [建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [SharePoint 專案與專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  