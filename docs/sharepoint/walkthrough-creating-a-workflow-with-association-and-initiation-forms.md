---
title: 使用關聯與初始表單建立工作流程
description: 在這個 SharePoint 逐步解說中，建立包含關聯和初始表單使用方式的基本連續工作流程。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cb759b155b119c29f20a39cdbf35338ec5a305b9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847735"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>逐步解說：使用關聯與初始表單建立工作流程
  本逐步解說示範如何建立包含關聯和初始表單使用方式的基本連續工作流程。 這些是 ASPX 表單，可在 SharePoint 系統管理員第一次將參數加入至工作流程時，將參數加入至工作流程中， () 的關聯表單，以及當使用者啟動工作流程) 時 (起始表單。

 本逐步解說將概述使用者想要針對符合下列需求的 expense reports 建立核准工作流程的案例：

- 當工作流程與清單相關聯時，系統管理員會收到關聯表單的提示，其中會輸入費用報告的貨幣限制。

- 員工將其支出報表上傳至共用文件清單、啟動工作流程，然後在工作流程初始表單中輸入費用總計。

- 如果員工費用報告總計超過系統管理員的預先定義限制，則會為員工的經理建立工作以核准費用報告。 但是，如果員工的支出報告總計小於或等於費用限制，則會將自動核准的訊息寫入工作流程的歷程記錄清單。

  本逐步解說將說明下列工作：

- 在中建立 SharePoint 清單定義的連續工作流程專案 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

- 建立工作流程排程。

- 處理工作流程活動事件。

- 建立工作流程關聯和初始表單。

- 關聯工作流程。

- 手動啟動工作流程。

> [!NOTE]
> 雖然本逐步解說使用連續的工作流程專案，但狀態機器工作流程的程式相同。
>
> 此外，您的電腦可能會 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 在下列指示中顯示某些使用者介面元素的不同名稱或位置。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]您擁有的版本和您所使用的設定會決定這些元素。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- 支援的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。

- Visual Studio。

## <a name="create-a-sharepoint-sequential-workflow-project"></a>建立 SharePoint 連續工作流程專案
 首先，在中建立連續的工作流程專案 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 連續工作流程是一系列的步驟，會在最後一個活動完成之前依序執行。 在此程式中，您將會建立套用至 SharePoint 中共用文件清單的順序工作流程。 工作流程的 wizard 可讓您將工作流程與網站或清單定義產生關聯，並可讓您判斷工作流程何時會開始。

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>若要建立 SharePoint 連續工作流程專案

1. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]，以顯示 [**新增專案**] 對話方塊。

2. 展開 [ **Visual c #** ] 或 [ **Visual Basic**] 底下的 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 在 [ **範本** ] 窗格中，選擇 [ **SharePoint 2010 專案** ] 專案範本。

4. 在 [ **名稱** ] 方塊中，輸入 **ExpenseReport** ，然後選擇 [ **確定]** 按鈕。

     [ **SharePoint 自訂] Wizard** 隨即出現。

5. 在 [ **指定偵錯工具的網站和安全性層級** ] 頁面中，選擇 [ **部署為伺服器陣列方案** ] 選項按鈕，然後選擇 [ **完成]** 按鈕以接受信任層級和預設網站。

     此步驟也會將解決方案的信任層級設定為伺服器陣列方案，這是工作流程專案的唯一可用選項。

6. 在 [ **方案總管**] 中選擇專案節點。

7. 在功能表列上，選擇 [ **Project**  >  **加入新專案**]。

8. 在 [ **Visual c #** ] 或 [ **Visual Basic**] 下，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

9. 在 [ **範本** ] 窗格中，選擇 [ **僅限順序的工作流程 (伺服器陣列方案])** 範本，然後選擇 [ **加入** ] 按鈕。

     [ **SharePoint 自訂] Wizard** 隨即出現。

10. 在 [ **指定用於偵錯工具的工作流程名稱** ] 頁面上，接受預設名稱 (**ExpenseReport-workflow1.xaml**) 。 保留預設工作流程範本類型值 (**清單工作流程)**。 選擇 [下一步] 按鈕。

11. 在 [ **您希望 Visual Studio 自動關聯偵錯工具的工作流程嗎？** ] 頁面上，清除已核取您的工作流程範本的方塊。

     此步驟可讓您在稍後手動將工作流程與共享檔案清單產生關聯，以顯示關聯表單。

12. 選擇 [完成] 按鈕。

## <a name="add-an-association-form-to-the-workflow"></a>將關聯表單新增至工作流程
 接著，建立。當 SharePoint 系統管理員第一次將工作流程與支出報表檔建立關聯時，所顯示的 ASPX 關聯表單。

#### <a name="to-add-an-association-form-to-the-workflow"></a>將關聯表單新增至工作流程

1. 選擇 **方案總管** 中的 [ **workflow1.xaml** ] 節點。

2. 在功能表列上 **，選擇 [**  >  **加入新** 專案]，以顯示 [**加入新專案**] 對話方塊。

3. 在對話方塊樹狀檢視中，依您的專案語言) 展開 [ **Visual c #** ] 或 [ **Visual Basic** (]，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

4. 在範本清單中，選擇 [ **工作流程關聯表單** ] 範本。

5. 在 [ **名稱** ] 文字方塊中，輸入 **ExpenseReportAssocForm .aspx**。

6. 選擇 [ **加入** ] 按鈕，將表單新增至專案。

## <a name="designing-and-coding-the-association-form"></a>設計與編碼關聯表單
 在此程式中，您會將控制項和程式碼新增至關聯表單，藉此引入其功能。

#### <a name="to-design-and-code-the-association-form"></a>設計及撰寫關聯表單的程式碼

1. 在 [關聯] 表單 ([ExpenseReportAssocForm]) 中，找出 `asp:Content` 具有的元素 `ID="Main"` 。

2. 直接在此內容專案的第一行之後，新增下列程式碼，以建立標籤和文字方塊，以提示 (*AutoApproveLimit*) 的費用核准限制：

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. 展開 **方案總管** 中的 **ExpenseReportAssocForm .aspx** 檔案，以顯示其相依的檔案。

    > [!NOTE]
    > 如果您的專案在中 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ，您必須選擇 [ **View All Files** ] 按鈕來執行此步驟。

4. 開啟 ExpenseReportAssocForm .aspx 檔案的快捷方式功能表，然後選擇 [ **View Code**]。

5. `GetAssociationData`以下列內容取代方法：

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

## <a name="add-an-initiation-form-to-the-workflow"></a>將初始表單新增至工作流程
 接下來，建立當使用者針對其支出報表執行工作流程時，所顯示的初始表單。

#### <a name="to-create-an-initiation-form"></a>建立初始表單

1. 選擇 **方案總管** 中的 [ **workflow1.xaml** ] 節點。

2. 在功能表列上，選擇 [ **Project**  >  **加入新專案**]，顯示 [**加入新專案**] 對話方塊。

3. 在對話方塊樹狀檢視中，依您的專案語言) 展開 [ **Visual c #** ] 或 [ **Visual Basic**  (]，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

4. 在範本清單中，選擇 [ **工作流程初始表單** ] 範本。

5. 在 [ **名稱** ] 文字方塊中，輸入 **ExpenseReportInitForm .aspx**。

6. 選擇 [ **加入** ] 按鈕，將表單新增至專案。

## <a name="designing-and-coding-the-initiation-form"></a>設計和撰寫初始表單的程式碼
 接下來，藉由將控制項和程式碼加入至初始表單來引入功能。

#### <a name="to-code-the-initiation-form"></a>撰寫初始表單的程式碼

1. 在初始表單 (ExpenseReportInitForm .aspx) 中，找出 `asp:Content` 包含的元素 `ID="Main"` 。

2. 直接在此內容專案的第一行之後，加入下列程式碼以建立標籤和文字方塊，以顯示在關聯表單中輸入 (*AutoApproveLimit*) 的費用核准限制，以及另一個標籤和文字方塊，以提示 (*ExpenseTotal*) 的費用總計：

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />
    <br /><br />
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />

    <asp:TextBox ID="ExpenseTotal" runat="server" />
    <br /><br />
    ```

3. 展開 **方案總管** 中的 **ExpenseReportInitForm .aspx** 檔案，以顯示其相依的檔案。

4. 開啟 ExpenseReportInitForm .aspx 檔案的快捷方式功能表，然後選擇 [ **View Code**]。

5. `Page_Load`以下列範例取代方法：

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

6. `GetInitiationData`以下列範例取代方法：

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

## <a name="cutomize-the-workflow"></a>Cutomize 工作流程
 接下來，自訂工作流程。 稍後，您會將兩個表單與工作流程產生關聯。

#### <a name="to-customize-the-workflow"></a>自訂工作流程

1. 在專案中開啟 Workflow1.xaml，以在工作流程設計工具中顯示工作流程。

2. 在 [ **工具箱**] 中，展開 [ **Windows Workflow v3.0** ] 節點並找出 [ **IfElse** ] 活動。

3. 藉由執行下列其中一個步驟，將此活動新增至工作流程：

    - 開啟 [ **IfElse** ] 活動的快捷方式功能表，選擇 [ **複製**]，在工作流程設計工具中的 [ **onWorkflowActivated1** ] 活動下，開啟該行的快捷方式功能表，然後選擇 [ **貼** 上]。

    - 從 [工具箱] 拖曳 [ **IfElse** ] 活動，然後將它連接到工作流程設計 **工具** 中 [ **onWorkflowActiviated1** ] 活動下的那一行。

4. 在 [工具箱] 中，展開 [ **SharePoint 工作流程** ] 節點，然後找出 [ **CreateTask** ] 活動。

5. 藉由執行下列其中一個步驟，將此活動新增至工作流程：

    - 開啟 **CreateTask** 活動的快捷方式功能表，選擇 [**複製**]，然後在 [工作流程設計工具] 的 [ **IfElseActivity1** ] 中，開啟這兩個 **放置活動** 中其中一個的快捷方式功能表，然後選擇 [**貼** 上]。

    - 將 [ **CreateTask** ] 活動從 [**工具箱**] 拖曳到 [ **IfElseActivity1**] 中的兩個 **放置活動** 區域的其中一個。

6. 在 [**屬性**] 視窗的 [ **CorrelationToken** ] 屬性中，輸入 *taskToken* 的屬性值。

7. 選擇加號 (![TreeView plus](../sharepoint/media/plus.gif "TreeView 加號")) 旁邊的加號，以展開 [ **CorrelationToken** ] 屬性。

8. 選擇 **OwnerActivityName** 子屬性上的下拉箭號，並設定 *workflow1.xaml* 值。

9. 選擇 [ **TaskId** ] 屬性，然後選擇省略號 (![ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形") 省略號) 按鈕，以顯示 [系結 **屬性** ] 對話方塊。

10. 選擇 [系結 **至新的成員** ] 索引標籤，選擇 [ **建立欄位** ] 選項按鈕，然後選擇 [ **確定]** 按鈕。

11. 選擇 [ **TaskProperties** ] 屬性，然後選擇省略號 (![ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形") 省略號) 按鈕，以顯示 [系結 **屬性** ] 對話方塊。

12. 選擇 [系結 **至新的成員** ] 索引標籤，選擇 [ **建立欄位** ] 選項按鈕，然後選擇 [ **確定]** 按鈕。

13. 在 [ **工具箱**] 中，展開 [ **SharePoint 工作流程** ] 節點，然後找出 [ **LogToHistoryListActivity** ] 活動。

14. 藉由執行下列其中一個步驟，將此活動新增至工作流程：

    - 開啟 **LogToHistoryListActivity** 活動的快捷方式功能表，選擇 [**複製**]，然後在 [工作流程設計工具] 中的 [ **IfElseActivity1** ] 區域內，開啟其他 **下拉式活動** 的快捷方式功能表，然後選擇 [**貼** 上]。

    - 從 [**工具箱**] 將 [ **LogToHistoryListActivity** ] 活動拖放到 [ **IfElseActivity1**] 中的 [其他 **放置活動**] 區域。

## <a name="add-code-to-the-workflow"></a>將程式碼加入至工作流程
 接下來，將程式碼加入至工作流程，以提供其功能。

#### <a name="to-add-code-to-the-workflow"></a>若要將程式碼加入至工作流程

1. 在工作流程設計工具中開啟 [ **createTask1** ] 活動的快捷方式功能表，然後選擇 [ **視圖程式碼**]。

2. 新增下列方法：

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
    > 在程式碼中， `somedomain\\someuser` 將取代為要建立工作的網域和使用者名稱，例如 " `Office\\JoeSch` "。 若要進行測試，最簡單的方式是使用您所開發的帳戶。

3. 在 `MethodInvoking` 方法下方，新增下列範例：

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

4. 在工作流程設計工具中，選擇 [ **ifElseBranchActivity1** ] 活動。

5. 在 [ **屬性** ] 視窗中，選擇 [ **條件** ] 屬性的下拉箭號，然後設定程式 *代碼條件* 值。

6. 選擇加號 (![TreeView plus](../sharepoint/media/plus.gif "TreeView 加號")) 旁邊的加號，然後將其值設定為 *checkApprovalNeeded*，以展開 [**條件**] 屬性。

7. 在工作流程設計工具中，開啟 [ **logToHistoryListActivity1** ] 活動的快捷方式功能表，然後選擇 [ **產生處理常式** ] 為事件產生空白的方法 `MethodInvoking` 。

8. `MethodInvoking`以下列程式碼取代程式碼：

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

9. 選擇 **F5** 鍵以進行程式的偵錯工具。

     這會編譯應用程式、封裝、部署應用程式、啟動其功能、回收 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 應用程式集區，然後在 [ **網站 Url** ] 屬性中指定的位置啟動瀏覽器。

## <a name="associating-the-workflow-to-the-documents-list"></a>將工作流程與檔案清單產生關聯
 接下來，將工作流程與 SharePoint 網站上的 **SharedDocuments** 清單產生關聯，以顯示工作流程關聯表單。

#### <a name="to-associate-the-workflow"></a>若要建立工作流程的關聯

1. 選擇快速啟動列上的 [ **共用文件** ] 連結。

2. 選擇 [文檔 **庫工具**] 索引標籤上的 [連結 **庫**] 連結，然後選擇 [文檔 **庫設定**] 功能區按鈕

3. 在 [**許可權與管理**] 區段中，選擇 [**工作流程設定**] 連結，然後選擇 [**工作** 流程] 頁面上的 [**新增工作流程**] 連結。

4. 在 [工作流程設定] 頁面的頂端清單中，選擇 [ **ExpenseReport-workflow1.xaml** ] 範本。

5. 在下一個欄位中，輸入 **ExpenseReportWorkflow** ，然後選擇 [ **下一步]** 按鈕。

     這會將工作流程與 **共用檔** 清單產生關聯，並顯示工作流程關聯表單。

6. 在 [ **自動核准限制** ] 文字方塊中，輸入 **1200** ，然後選擇 [ **關聯工作流程** ] 按鈕。

## <a name="start-the-workflow"></a>啟動工作流程
 接下來，將工作流程與 **共用文件** 清單中的其中一個檔建立關聯，以顯示工作流程初始表單。

#### <a name="to-start-the-workflow"></a>若要啟動工作流程

1. 在 SharePoint 頁面上，選擇 [ **首頁** ] 按鈕。

2. 選擇 [快速啟動] 列上的 [ **共用文件** ] 連結，以顯示 [ **共用的檔** ] 清單。

3. 選擇頁面頂端 [文檔 **庫工具**] 索引標籤上的 [**檔**] 連結，然後選擇功能區上的 [**上傳檔**] 按鈕，將新檔上傳至 **共用檔** 清單。

4. 在 [ **上傳檔** ] 對話方塊中，選擇 [ **流覽]** 按鈕，選擇任何檔檔案，選擇 [ **開啟** ] 按鈕，然後選擇 [ **確定]** 按鈕。

     您可以在此對話方塊中變更檔的設定，但請選擇 [ **儲存** ] 按鈕，將其保留為預設值。

5. 選擇已上傳的檔，選擇出現的下拉箭號，然後選擇 [ **工作流程** ] 專案。

6. 選擇 [ExpenseReportWorkflow] 旁的影像。

     這會顯示工作流程初始表單。  (請注意，[ **自動核准限制** ] 方塊中顯示的值是唯讀的，因為它是在關聯表單中輸入的。 ) 

7. 在 [ **費用總計** ] 文字方塊中，輸入 **1600**，然後選擇 [ **啟動工作流程** ] 按鈕。

     這會再次顯示 [ **共用的檔** ] 清單。 名為 **ExpenseReportWorkflow** 且已 **完成** 值的新資料行，會加入至工作流程剛開始的專案。

8. 選擇上傳檔旁邊的下拉箭號，然後選擇 [ **工作流程** ] 專案以顯示 [工作流程狀態] 頁面。 選擇 [**已完成工作流程**] 下的 [**已完成**] 值。 工作會列在 [工作 **] 區段底下** 。

9. 選擇工作的標題以顯示其工作詳細資料。

10. 返回 **SharedDocuments** 清單，然後使用相同的檔或不同的檔重新開機工作流程。

11. 在起始頁面上輸入小於或等於 [關聯] 頁面上輸入之數量 (**1200**) 的金額。

     發生這種情況時，會建立記錄清單中的專案，而不是工作。 專案會顯示在 [工作流程狀態] 頁面的 [ **工作流程歷程記錄** ] 區段中。 請注意歷程記錄事件 [ **結果** ] 資料行中的訊息。 它包含在事件中輸入的文字 `logToHistoryListActivity1.MethodInvoking` ，其中包含已自動核准的數量。

## <a name="next-steps"></a>下一步
 您可以從下列主題深入瞭解如何建立工作流程範本：

- 若要深入瞭解 SharePoint 工作流程，請參閱 [Windows Sharepoint Services 中的工作流程](/previous-versions/office/developer/sharepoint-2010/ms416312(v=office.14))。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [逐步解說：將應用程式頁面加入至工作流程](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
