---
title: "逐步解說： 建立工作流程關聯與初始化表單與 |Microsoft 文件"
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
ms.assetid: c8666d8c-b173-4245-8014-9c1cd6acb071
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa95c519ab24ba042b6a1adfa71c64499b18d4c9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-workflow-with-association-and-initiation-forms"></a>逐步解說：使用關聯與初始化表單建立工作流程
  本逐步解說示範如何建立基本的循序工作流程，其中包含使用關聯與初始化表單。 這是啟用參數加入至工作流程，以及使用者 （初始表單） 啟動工作流程時先到 SharePoint 系統管理員 （關聯表單） 相關聯的 ASPX 形式。  
  
 本逐步解說列出使用者要建立具有下列需求核准工作流程的經費支出報表的案例：  
  
-   在工作流程清單相關聯時，系統會提示系統管理員與關聯表單，在其中輸入貨幣限制的經費支出報表。  
  
-   員工會將其經費支出報表上傳至 Shared Documents 清單，啟動工作流程，，然後輸入工作流程初始表單中的總成本。  
  
-   如果員工的經費支出報表總計超過系統管理員的預先定義的限制，會建立一個工作個員工的經理核准的經費支出報表。 不過，如果員工的經費支出報表總計是否小於或等於支出限制，將自動核准訊息會寫入工作流程歷程清單。  
  
 這個逐步解說將說明下列工作：  
  
-   建立 SharePoint 清單定義循序工作流程專案中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
-   建立工作流程排程。  
  
-   處理工作流程活動事件。  
  
-   建立工作流程關聯與初始化表單。  
  
-   建立工作流程的關聯。  
  
-   手動啟動工作流程。  
  
> [!NOTE]  
>  雖然本逐步解說使用循序工作流程專案，程序也適用於狀態機器工作流程。  
>   
>  此外，您的電腦可能會顯示不同的名稱或位置的某些[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]下列指示中的使用者介面項目。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]您擁有的版本，以及您使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的版本[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]和 SharePoint。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## <a name="creating-a-sharepoint-sequential-workflow-project"></a>建立 SharePoint 循序工作流程專案  
 首先，建立循序工作流程專案中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 循序工作流程是一系列的步驟會依序執行的最後一個活動完成為止。 在此程序，您將建立適用於 SharePoint 中的共用文件清單的循序工作流程。 工作流程的精靈可讓您的網站或清單定義與關聯工作流程，並可讓您決定當工作流程會開始。  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>若要建立 SharePoint 循序工作流程專案  
  
1.  在功能表列上選擇 [**檔案**，**新增**，**專案**顯示**新專案**] 對話方塊。  
  
2.  展開**SharePoint**節點之下**Visual C#**或**Visual Basic**，然後選擇  **2010年**節點。  
  
3.  在**範本** 窗格中，選擇**SharePoint 2010 專案**專案範本。  
  
4.  在**名稱**方塊中，輸入**ExpenseReport** ，然後選擇 [**確定**] 按鈕。  
  
     **SharePoint 自訂精靈**隨即出現。  
  
5.  在**指定偵錯的網站和安全性層級**頁面上，選擇**部署為伺服陣列方案**選項按鈕，然後再選擇**完成**接受按鈕信任層級和預設站台。  
  
     這個步驟也會設定為伺服器陣列方案，也就是唯一可用的選項的工作流程專案的方案的信任層級。  
  
6.  在 [ **方案總管**] 中選擇專案節點。  
  
7.  在功能表列上選擇 **專案**，**加入新項目**。  
  
8.  之下**Visual C#**或**Visual Basic**，依序展開**SharePoint** ] 節點，然後選擇 [ **2010年**節點。  
  
9. 在**範本** 窗格中，選擇**循序工作流程 （僅限陣列方案）**範本，然後選擇 **新增** 按鈕。  
  
     **SharePoint 自訂精靈**隨即出現。  
  
10. 在**指定偵錯的工作流程名稱**頁面上，接受預設名稱 (**ExpenseReport-Workflow1**)。 保留預設流程範本類型值 (**清單工作流程)**。 選擇**下一步** 按鈕。  
  
11. 在**您希望 Visual Studio 自動關聯工作流程偵錯工作階段中？**頁面上，清除 自動將您的工作流程範本，如果已核取方塊。  
  
     這個步驟可讓您以手動方式將共用文件清單之後會顯示關聯表單的工作流程產生關聯。  
  
12. 選擇**完成** 按鈕。  
  
## <a name="adding-an-association-form-to-the-workflow"></a>加入至工作流程關聯表單  
 接下來，建立。ASPX 關聯表單，SharePoint 系統管理員第一次建立工作流程關聯的經費支出報表文件時，會出現。  
  
#### <a name="to-add-an-association-form-to-the-workflow"></a>若要加入至工作流程關聯表單  
  
1.  選擇**Workflow1**節點**方案總管 中**。  
  
2.  在功能表列上選擇 [**專案**，**加入新項目**顯示**加入新項目**] 對話方塊。  
  
3.  在對話方塊] 方塊中的 [樹狀] 檢視中，展開 [ **Visual C#**或**Visual Basic** （取決於您專案的語言），依序展開**SharePoint** ] 節點，然後選擇 [ **2010年**節點。  
  
4.  在範本清單中，選擇 **工作流程關聯表單**範本。  
  
5.  在**名稱**文字方塊中，輸入**ExpenseReportAssocForm.aspx**。  
  
6.  選擇**新增**按鈕，將表單加入至專案。  
  
## <a name="designing-and-coding-the-association-form"></a>設計和撰寫程式碼關聯表單  
 此程序，在您要新增控制項和程式碼來加入關聯表單的功能。  
  
#### <a name="to-design-and-code-the-association-form"></a>若要設計和程式碼關聯表單  
  
1.  在關聯表單 (ExpenseReportAssocForm.aspx) 中，找出`asp:Content`具有項目`ID="Main"`。  
  
2.  直接在此內容項目中的第一行之後, 加入下列程式碼，建立標籤和文字方塊提示的經費支出核准限制 (*AutoApproveLimit*):  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  展開**ExpenseReportAssocForm.aspx**檔案**方案總管 中**顯示與其相依的檔案。  
  
    > [!NOTE]  
    >  如果您的專案位於[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]，您必須選擇**檢視所有檔案**按鈕執行此步驟。  
  
4.  開啟 ExpenseReportAssocForm.aspx 檔案的捷徑功能表並選擇 **檢視程式碼**。  
  
5.  取代`GetAssociationData`方法：  
  
    ```vb  
    Private Function GetAssociationData() As String  
        ' TODO: Return a string that contains the association data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return Me.AutoApproveLimit.Text  
    End Function  
    ```  
  
    ```csharp  
    private string GetAssociationData()  
    {  
        // TODO: Return a string that contains the association data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.AutoApproveLimit.Text;  
    }  
    ```  
  
## <a name="adding-an-initiation-form-to-the-workflow"></a>加入至工作流程初始表單  
 接下來，建立會顯示當使用者對其的經費支出報表執行工作流程初始表單。  
  
#### <a name="to-create-an-initiation-form"></a>若要建立初始表單  
  
1.  選擇**Workflow1**節點**方案總管 中**。  
  
2.  在功能表列上選擇 [**專案**，**加入新項目**顯示**加入新項目**] 對話方塊。  
  
3.  在對話方塊] 方塊中的 [樹狀] 檢視中，展開 [ **Visual C#**或**Visual Basic** （取決於您專案的語言），依序展開**SharePoint** ] 節點，然後選擇 [ **2010年**節點。  
  
4.  在範本清單中，選擇 **工作流程初始表單**範本。  
  
5.  在**名稱**文字方塊中，輸入**ExpenseReportInitForm.aspx**。  
  
6.  選擇**新增**按鈕，將表單加入至專案。  
  
## <a name="designing-and-coding-the-initiation-form"></a>設計和編碼初始表單  
 接下來，新增控制項和程式碼，來介紹初始表單的功能。  
  
#### <a name="to-code-the-initiation-form"></a>初始表單的程式碼  
  
1.  在初始表單 (ExpenseReportInitForm.aspx) 中，找出`asp:Content`包含項目`ID="Main"`。  
  
2.  直接在此內容項目中的第一行之後, 加入下列程式碼建立的標籤和文字方塊中顯示的經費支出核准限制 (*AutoApproveLimit*) 的輸入關聯表單中，而且另一個標籤和費用總計提示您輸入的文字方塊中 (*ExpenseTotal*):  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  展開**ExpenseReportInitForm.aspx**檔案**方案總管 中**顯示與其相依的檔案。  
  
4.  開啟 ExpenseReportInitForm.aspx 檔案的捷徑功能表並選擇 **檢視程式碼**。  
  
5.  取代`Page_Load`方法，以下列範例：  
  
    ```vb  
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As   
      EventArgs) Handles Me.Load  
        InitializeParams()  
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New   
          Guid(associationGuid)).AssociationData  
        ' Optionally, add code here to pre-populate your form fields.  
    End Sub  
    ```  
  
    ```csharp  
    protected void Page_Load(object sender, EventArgs e)  
    {  
        InitializeParams();  
        this.AutoApproveLimit.Text =   
          workflowList.WorkflowAssociations[new   
          Guid(associationGuid)].AssociationData;  
    }  
    ```  
  
6.  取代`GetInitiationData`方法，以下列範例：  
  
    ```vb  
    ' This method is called when the user clicks the button to start the workflow.  
    Private Function GetInitiationData() As String  
        Return Me.ExpenseTotal.Text  
        ' TODO: Return a string that contains the initiation data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return String.Empty  
    End Function  
    ```  
  
    ```csharp  
    // This method is called when the user clicks the button to start the workflow.          
    private string GetInitiationData()  
    {  
        // TODO: Return a string that contains the initiation data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.ExpenseTotal.Text;  
    }  
    ```  
  
## <a name="customizing-the-workflow"></a>自訂工作流程  
 接下來，自訂工作流程。 稍後，您會將關聯工作流程的兩種形式。  
  
#### <a name="to-customize-the-workflow"></a>若要自訂工作流程  
  
1.  顯示在工作流程設計工具中的工作流程專案中開啟 Workflow1。  
  
2.  在**工具箱**，依序展開**Windows Workflow v3.0**節點並找出**IfElse**活動。  
  
3.  加入至工作流程的這項活動，藉由執行下列步驟：  
  
    -   開啟快顯功能表**IfElse**活動中，選擇**複製**，開啟下的那一行的捷徑功能表**onWorkflowActivated1**活動在工作流程設計工具然後選擇 **貼上**。  
  
    -   拖曳**IfElse**活動從**工具箱**，並將它連接至下一行**onWorkflowActiviated1**工作流程設計工具中的活動。  
  
4.  在 工具箱 中展開  **SharePoint 工作流程**節點並找出**CreateTask**活動。  
  
5.  加入至工作流程的這項活動，藉由執行下列步驟：  
  
    -   開啟快顯功能表**CreateTask**活動中，選擇**複製**，開啟捷徑功能表，其中兩個**置放活動**區域內**IfElseActivity1**中工作流程設計工具中，然後選擇 **貼上**。  
  
    -   拖曳**CreateTask**活動從**工具箱**個兩個的其中一個**置放活動**區域內**IfElseActivity1**。  
  
6.  在**屬性**視窗中，輸入屬性值為*taskToken*如**CorrelationToken**屬性。  
  
7.  展開**CorrelationToken**屬性選擇加號 (![TreeView 加號](../sharepoint/media/plus.gif "TreeView 加號")) 旁邊。  
  
8.  選擇下拉式箭號上**OwnerActivityName**子屬性，並設定*Workflow1*值。  
  
9. 選擇**TaskId**屬性，然後選擇省略符號 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) 按鈕，即可顯示**繫結屬性** 對話方塊。  
  
10. 選擇**繫結到新成員**索引標籤上，選擇**建立欄位**選項按鈕，然後再選擇**確定** 按鈕。  
  
11. 選擇**TaskProperties**屬性，然後選擇省略符號 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) 按鈕，即可顯示**將屬性繫結** 對話方塊。  
  
12. 選擇**繫結到新成員**索引標籤上，選擇**建立欄位**選項按鈕，然後再選擇**確定** 按鈕。  
  
13. 在**工具箱**，依序展開**SharePoint 工作流程** 節點，並找出**LogToHistoryListActivity**活動。  
  
14. 加入至工作流程的這項活動，藉由執行下列步驟：  
  
    -   開啟快顯功能表**LogToHistoryListActivity**活動中，選擇**複製**，其他開啟的捷徑功能表**置放活動**內區域**IfElseActivity1**中工作流程設計工具中，然後選擇 **貼上**。  
  
    -   拖曳**LogToHistoryListActivity**活動從**工具箱**，拖放到其他**置放活動**區域內**IfElseActivity1**.  
  
## <a name="adding-code-to-the-workflow"></a>程式碼加入至工作流程  
 接下來，將程式碼加入至為它提供的功能工作流程。  
  
#### <a name="to-add-code-to-the-workflow"></a>若要將程式碼加入至工作流程  
  
1.  開啟快顯功能表**createTask1**活動在工作流程設計工具中，然後選擇 **檢視程式碼**。  
  
2.  將下列方法：  
  
    ```vb  
    Private Sub createTask1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        createTask1_TaskId1 = Guid.NewGuid  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report"  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed"  
    End Sub   
    ```  
  
    ```csharp  
    private void createTask1_MethodInvoking(object sender, EventArgs e)  
    {  
        createTask1_TaskId1 = Guid.NewGuid();  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report";  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed";  
    }   
    ```  
  
    > [!NOTE]  
    >  在程式碼，取代`somedomain\\someuser`網域和使用者名稱，其會建立工作，例如，"`Office\\JoeSch`"。 對測試很容易使用您所開發的帳戶。  
  
3.  下面`MethodInvoking`方法，加入下列的範例：  
  
    ```vb  
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As   
      ConditionalEventArgs)  
        Dim approval As Boolean = False  
        If (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData)) Then  
            approval = True  
        End If  
        e.Result = approval  
    End Sub   
    ```  
  
    ```csharp  
    private void checkApprovalNeeded(object sender, ConditionalEventArgs   
      e)  
    {  
        bool approval = false;  
        if (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData))  
        {  
            approval = true;  
        }  
        e.Result = approval;  
    }   
    ```  
  
4.  在工作流程設計工具中，選擇  **ifElseBranchActivity1**活動。  
  
5.  在**屬性**視窗中，選擇的下拉式箭號**條件**屬性，並將其設定*程式碼條件*值。  
  
6.  展開**條件**屬性選擇加號 (![TreeView 加號](../sharepoint/media/plus.gif "TreeView 加號"))，然後將其值設定為*checkApprovalNeeded*.  
  
7.  在工作流程設計工具中，開啟捷徑功能表的**logToHistoryListActivity1**活動，然後選擇 **產生的處理常式**來產生空白的方法，如`MethodInvoking`事件。  
  
8.  取代`MethodInvoking`以下列程式碼：  
  
    ```vb  
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto   
          approved for " + workflowProperties.InitiationData)  
    End Sub   
    ```  
  
    ```csharp  
    private void logToHistoryListActivity1_MethodInvoking(object sender,   
      EventArgs e)  
    {  
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was   
          auto approved for " + workflowProperties.InitiationData;  
    }   
    ```  
  
9. 選擇 F5 鍵偵錯的程式。  
  
     這會編譯應用程式、 將它包裝、 將其部署、 啟用其功能、 回收[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]應用程式集區，然後啟動瀏覽器的位置中指定**網站 Url**屬性。  
  
## <a name="associating-the-workflow-to-the-documents-list"></a>將工作流程，以在文件清單產生關聯  
 接下來，透過建立關聯的工作流程中顯示工作流程關聯表單**SharedDocuments** SharePoint 網站上的清單。  
  
#### <a name="to-associate-the-workflow"></a>關聯工作流程  
  
1.  選擇**Shared Documents**快速啟動列上的連結。  
  
2.  選擇**文件庫**連結**文件庫工具**索引標籤，然後選擇**文件庫設定**功能區按鈕。  
  
3.  在**權限與管理**區段中，選擇**工作流程設定**連結，然後選擇 **加入工作流程**連結**的工作流程**頁面。  
  
4.  在工作流程的 設定 頁面中最上層清單中，選擇  **ExpenseReport-Workflow1**範本。  
  
5.  在下一步 欄位中，輸入**ExpenseReportWorkflow** ，然後選擇 **下一步** 按鈕。  
  
     這樣會將關聯的工作流程**Shared Documents**清單，並顯示工作流程關聯表單。  
  
6.  在**自動核准限制**文字方塊中，輸入**1200年**，然後選擇 [**產生關聯的工作流程**] 按鈕。  
  
## <a name="starting-the-workflow"></a>啟動工作流程  
 接下來，將工作流程中的文件的其中一個**Shared Documents**清單來顯示工作流程初始表單。  
  
#### <a name="to-start-the-workflow"></a>若要啟動工作流程  
  
1.  在 SharePoint 頁面上，選擇 [**首頁**] 按鈕。  
  
2.  選擇**Shared Documents**快速啟動列來顯示連結**Shared Documents**清單。  
  
3.  選擇**文件**連結**文件庫工具**頂端的頁面上，索引標籤，然後選擇**上傳文件**要上傳到新的文件的功能區上的按鈕**Shared Documents**清單。  
  
4.  在**上傳文件**對話方塊方塊中，選擇**瀏覽**按鈕，選擇任何文件檔，選擇**開啟**按鈕，然後再選擇**確定**  按鈕。  
  
     您可以變更此對話方塊，請在文件的設定，但它們保留預設值選擇**儲存** 按鈕。  
  
5.  選擇 上傳的文件中，選擇的下拉式箭號，隨即出現，然後選擇 **工作流程**項目。  
  
6.  選擇旁邊 ExpenseReportWorkflow 映像。  
  
     這會顯示工作流程初始表單。 (請注意，這個值顯示在**自動核准限制**方塊是唯讀的則是因為輸入關聯表單中。)  
  
7.  在**費用總計**文字方塊中，輸入**1600年**，然後選擇 [**啟動工作流程**] 按鈕。  
  
     這會顯示**Shared Documents**列出一次。 新的資料行名為**ExpenseReportWorkflow**值**已完成**加入至工作流程將直接啟動項目。  
  
8.  選擇下拉式清單旁的箭號上傳的文件，然後選擇**工作流程**項目以顯示工作流程狀態頁面。 選擇**已完成**值下**完成的工作流程**。 該工作將列示在下**工作**> 一節。  
  
9. 選擇工作以顯示其工作詳細資料的標題。  
  
10. 請返回**SharedDocuments**清單，然後重新啟動工作流程，使用相同的文件或另一部。  
  
11. 小於或等於關聯 頁面上輸入量的起始頁面上輸入金額 (**1200年**)。  
  
     發生這種情況，而不是工作會建立歷程記錄清單中的項目。 項目會顯示在**工作流程歷程記錄**工作流程狀態頁面區段。 請注意在訊息**結果**記錄事件的資料行。 它包含在文字方塊中輸入`logToHistoryListActivity1.MethodInvoking`包含數量，已自動核准的事件。  
  
## <a name="next-steps"></a>後續步驟  
 您可以深入了解如何建立工作流程範本，從下列主題：  
  
-   若要了解有關 SharePoint 工作流程的詳細資訊，請參閱[Windows SharePoint Services 中的工作流程](http://go.microsoft.com/fwlink/?LinkID=166275)。  
  
## <a name="see-also"></a>另請參閱  
 [建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [逐步解說：將應用程式頁面新增到工作流程](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
  