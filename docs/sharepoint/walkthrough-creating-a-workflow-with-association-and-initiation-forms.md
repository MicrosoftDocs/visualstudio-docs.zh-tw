---
title: 使用關聯與初始表單建立工作流程
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7946e48502ea4fd8e9e9382a20de3c8ce25987b3
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984685"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>逐步解說：使用關聯與初始表單建立工作流程
  本逐步解說示範如何建立結合使用關聯和初始表單的基本順序工作流程。 這些是 ASPX 格式，可讓您在工作流程第一次與 SharePoint 管理員（關聯表單）產生關聯，以及由使用者啟動工作流程（初始表單）時，將參數加入至工作流程。

 本逐步解說概述一個案例，使用者想要針對具有下列需求的費用報表建立核准工作流程：

- 當工作流程與清單相關聯時，系統管理員會以關聯表單提示，他們會在其中輸入支出報表的金額限制。

- 員工將其費用報表上傳至 [共用文件] 清單，啟動工作流程，然後在工作流程初始表單中輸入費用總計。

- 如果員工支出報表總計超過系統管理員預先定義的限制，就會為員工的經理建立工作來核准費用報表。 不過，如果員工的支出報表總計小於或等於費用限制，則自動核准的訊息會寫入至工作流程的歷程記錄清單。

  這個逐步解說將說明下列工作：

- 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中建立 SharePoint 清單定義的順序工作流程專案。

- 建立工作流程排程。

- 處理工作流程活動事件。

- 建立工作流程關聯和初始表單。

- 建立工作流程的關聯。

- 手動啟動工作流程。

> [!NOTE]
> 雖然本逐步解說使用的是連續的工作流程專案，但此程式對狀態機器工作流程而言是相同的。
>
> 此外，您的電腦可能會針對下列指示中的某些 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 使用者介面元素，顯示不同的名稱或位置。 您擁有的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 版本和您所使用的設定會決定這些元素。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>Prerequisites
 您需要下列元件才能完成此逐步解說：

- 支援的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。

- Visual Studio。

## <a name="create-a-sharepoint-sequential-workflow-project"></a>建立 SharePoint 順序工作流程專案
 首先，在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中建立連續的工作流程專案。 連續工作流程是一系列的步驟，會依序執行，直到最後一個活動完成為止。 在這個程式中，您將建立適用于 SharePoint 中共用文件清單的順序工作流程。 工作流程的 wizard 可讓您將工作流程與網站或清單定義建立關聯，並可讓您判斷工作流程何時啟動。

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>若要建立 SharePoint 順序工作流程專案

1. 在功能表列上 **，選擇 [** 檔案]  >  [**新增** > **專案**]，以顯示 [**新增專案**] 對話方塊。

2. 展開 [**視覺效果C#**  ] 或 [ **Visual Basic**] 底下的 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 在 [**範本**] 窗格中，選擇 [ **SharePoint 2010 專案**] 專案範本。

4. 在 [**名稱**] 方塊中，輸入**ExpenseReport** ，然後選擇 [**確定]** 按鈕。

     [ **SharePoint 自訂嚮導]** 隨即出現。

5. 在 [**指定網站和安全性層級進行偵錯工具**] 頁面中，選擇 [**部署為數組方案**] 選項按鈕，然後選擇 [**完成]** 按鈕以接受信任層級和預設網站。

     此步驟也會將方案的信任層級設定為 [伺服器陣列方案]，這是工作流程專案唯一可用的選項。

6. 在 [ **方案總管**] 中選擇專案節點。

7. 在功能表列中，選擇 [專案] > [加入新項目]。

8. 在 [**視覺C#效果**] 或 [ **Visual Basic**] 底下，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

9. 在 [**範本**] 窗格中，選擇 [**順序工作流程（僅限陣列方案）** ] 範本，然後選擇 [**新增**] 按鈕。

     [ **SharePoint 自訂嚮導]** 隨即出現。

10. 在 [**指定用於偵錯工具的工作流程名稱**] 頁面中，接受預設名稱（**ExpenseReport-workflow1.xaml**）。 保留預設工作流程範本類型值（[**清單工作流程]）** 。 選擇 [下一步] 按鈕。

11. 在 [**您想要 Visual Studio 自動將工作流程關聯在偵錯工具嗎？** ] 頁面中，清除已核取工作流程範本時自動產生關聯的核取方塊。

     此步驟可讓您在稍後以手動方式將工作流程與共享文檔清單建立關聯，這會顯示關聯表單。

12. 選擇 [**完成]** 按鈕。

## <a name="add-an-association-form-to-the-workflow"></a>將關聯表單新增至工作流程
 接下來，建立。當 SharePoint 管理員第一次將工作流程與費用報表檔產生關聯時，所顯示的 ASPX 關聯表單。

#### <a name="to-add-an-association-form-to-the-workflow"></a>若要將關聯表單加入至工作流程

1. 選擇**方案總管**中的 [ **workflow1.xaml** ] 節點。

2. 在功能表列上，選擇 [**專案**] > [**加入新專案**] 以顯示 [**加入新專案**] 對話方塊。

3. 在對話方塊樹狀檢視中，展開 [**視覺效果C#**  ] 或 [ **Visual Basic** ] （視您的專案語言而定），展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

4. 在範本清單中，選擇 [**工作流程關聯] 表單**範本。

5. 在 [**名稱**] 文字方塊中，輸入**ExpenseReportAssocForm。**

6. 選擇 [**新增**] 按鈕，將表單新增至專案。

## <a name="designing-and-coding-the-association-form"></a>設計和撰寫關聯表單的程式碼
 在此程式中，您會將控制項和程式碼加入至關聯表單，藉以引進其功能。

#### <a name="to-design-and-code-the-association-form"></a>設計和撰寫關聯表單的程式碼

1. 在 [關聯] 表單（ExpenseReportAssocForm .aspx）中，找出具有 `ID="Main"`的 `asp:Content` 元素。

2. 直接在此內容專案的第一行之後，新增下列程式碼來建立標籤和文字方塊，以提示您輸入支出核准限制（*AutoApproveLimit*）：

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. 展開**方案總管**中的**ExpenseReportAssocForm** ，以顯示其相依檔案。

    > [!NOTE]
    > 如果您的專案在 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]中，您必須選擇 [**查看所有**檔案] 按鈕，才能執行此步驟。

4. 開啟 [ExpenseReportAssocForm] 檔案的快捷方式功能表，然後選擇 [ **View Code**]。

5. 以取代 `GetAssociationData` 方法：

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
 接下來，建立當使用者針對其費用報表執行工作流程時，所顯示的初始表單。

#### <a name="to-create-an-initiation-form"></a>若要建立初始表單

1. 選擇**方案總管**中的 [ **workflow1.xaml** ] 節點。

2. 在功能表列上，選擇 [**專案**] > [**加入新專案**]，顯示 [**加入新專案**] 對話方塊。

3. 在對話方塊樹狀檢視中，展開 [**視覺效果C#**  ] 或 [ **Visual Basic** ] （視您的專案語言而定），展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

4. 在範本清單中，選擇 [**工作流程初始表單**] 範本。

5. 在 [**名稱**] 文字方塊中，輸入**ExpenseReportInitForm。**

6. 選擇 [**新增**] 按鈕，將表單新增至專案。

## <a name="designing-and-coding-the-initiation-form"></a>設計和撰寫起始表單的程式碼
 接下來，藉由在其中加入控制項和程式碼，引進初始表單的功能。

#### <a name="to-code-the-initiation-form"></a>撰寫起始表單的程式碼

1. 在初始表單（ExpenseReportInitForm .aspx）中，找出包含 `ID="Main"`的 `asp:Content` 元素。

2. 直接在這個 content 元素的第一行之後，加入下列程式碼來建立標籤和文字方塊，以顯示在關聯表單中輸入的支出核准限制（*AutoApproveLimit*），以及另一個要提示的標籤和文字方塊費用總計（*ExpenseTotal*）：

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />
    <br /><br />
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />

    <asp:TextBox ID="ExpenseTotal" runat="server" />
    <br /><br />
    ```

3. 展開**方案總管**中的**ExpenseReportInitForm** ，以顯示其相依檔案。

4. 開啟 [ExpenseReportInitForm] 檔案的快捷方式功能表，然後選擇 [ **View Code**]。

5. 以下列範例取代 `Page_Load` 方法：

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

6. 以下列範例取代 `GetInitiationData` 方法：

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

1. 藉由在專案中開啟 Workflow1.xaml，在工作流程設計工具中顯示工作流程。

2. 在 [**工具箱**] 中，展開 [ **Windows Workflow v3.0** ] 節點，並找出 [ **IfElse** ] 活動。

3. 執行下列其中一個步驟，將此活動新增至工作流程：

    - 開啟 [ **IfElse** ] 活動的快捷方式功能表，選擇 [**複製**]，在工作流程設計工具中開啟 [ **onWorkflowActivated1** ] 活動下的行的快捷方式功能表，然後選擇 [**貼**上]。

    - 從 [工具箱] 拖曳 [ **IfElse** ] 活動，並將它連接到工作流程設計**工具**中 [ **onWorkflowActiviated1** ] 活動底下的那一行。

4. 在 [工具箱] 中，展開 [ **SharePoint 工作流程**] 節點，並找出 [ **CreateTask** ] 活動。

5. 執行下列其中一個步驟，將此活動新增至工作流程：

    - 開啟 [ **CreateTask** ] 活動的快捷方式功能表，選擇 [**複製**]，在工作流程設計工具的 [ **IfElseActivity1** ] 中，開啟兩個 [在**此處放置活動**的其中一個] 的快捷方式功能表，然後選擇 [**貼**上]。

    - 將 [ **CreateTask** ] 活動從 [**工具箱**] 拖曳至**IfElseActivity1**內的兩個 [**放置活動**] 區域中的其中一個。

6. 在 [**屬性**] 視窗的 [ **CorrelationToken** ] 屬性中，輸入*taskToken*的屬性值。

7. 藉由選擇旁邊的加號（![TreeView 加號](../sharepoint/media/plus.gif "TreeView 加號")）來展開 [ **CorrelationToken** ] 屬性。

8. 選擇 [ **OwnerActivityName** ] 子屬性的下拉箭號，然後設定*workflow1.xaml*值。

9. 選擇 [ **TaskId** ] 屬性，然後選擇省略號（![ASP.NET Mobile 設計](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")工具省略號）按鈕，以顯示 [系結**屬性**] 對話方塊。

10. 選擇 [系結**至新成員**] 索引標籤，選擇 [**建立欄位**] 選項按鈕，然後選擇 [**確定]** 按鈕。

11. 選擇 [ **TaskProperties** ] 屬性，然後選擇省略號（![ASP.NET Mobile 設計](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")工具省略號）按鈕，以顯示 [系結**屬性**] 對話方塊。

12. 選擇 [系結**至新成員**] 索引標籤，選擇 [**建立欄位**] 選項按鈕，然後選擇 [**確定]** 按鈕。

13. 在 [**工具箱**] 中，展開 [ **SharePoint 工作流程**] 節點，然後找出 [ **LogToHistoryListActivity** ] 活動。

14. 執行下列其中一個步驟，將此活動新增至工作流程：

    - 開啟 [ **LogToHistoryListActivity** ] 活動的快捷方式功能表，選擇 [**複製**]，在工作流程設計工具的 [ **IfElseActivity1** ] 中開啟其他 [卸載**活動**] 區域的快捷方式功能表，然後選擇 [貼上].

    - 從 [**工具箱**] 拖曳 [ **LogToHistoryListActivity** ] 活動，並將它放到**IfElseActivity1**內的其他 [卸載**活動**] 區域。

## <a name="add-code-to-the-workflow"></a>將程式碼加入至工作流程
 接下來，將程式碼新增至工作流程，以提供其功能。

#### <a name="to-add-code-to-the-workflow"></a>若要將程式碼加入至工作流程

1. 在工作流程設計工具中開啟 [ **createTask1** ] 活動的快捷方式功能表，然後選擇 [ **View Code**]。

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
    > 在程式碼中，將 `somedomain\\someuser` 取代為要建立工作的網域和使用者名稱，例如「`Office\\JoeSch`」。 若要進行測試，最簡單的方法是使用您所開發的帳戶。

3. 在 `MethodInvoking` 方法底下，新增下列範例：

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

5. 在 [**屬性**] 視窗中，選擇 [ **Condition** ] 屬性的下拉箭號，然後設定 [程式*代碼條件*] 值。

6. 藉由選擇旁邊的加號（![TreeView 加號](../sharepoint/media/plus.gif "TreeView 加號")）來展開 [**條件**] 屬性，然後將其值設定為 [ *checkApprovalNeeded*]。

7. 在工作流程設計工具中，開啟 [ **logToHistoryListActivity1** ] 活動的快捷方式功能表，然後選擇 [**產生處理常式**]，為 `MethodInvoking` 事件產生空的方法。

8. 將 `MethodInvoking` 的程式碼取代為下列內容：

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

9. 選擇**F5**鍵以進行程式的 debug。

     這會編譯應用程式、封裝它、部署、啟動其功能、回收 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 的應用程式集區，然後在 [**網站 Url** ] 屬性中指定的位置啟動瀏覽器。

## <a name="associating-the-workflow-to-the-documents-list"></a>將工作流程與檔案清單產生關聯
 接下來，將工作流程與 SharePoint 網站上的 [ **SharedDocuments** ] 清單建立關聯，以顯示工作流程關聯表單。

#### <a name="to-associate-the-workflow"></a>若要建立工作流程的關聯

1. 選擇 [快速啟動] 列上的 [**共用文件**] 連結。

2. 選擇 [連結**庫工具**] 索引標籤上的 [連結**庫**]，然後選擇 [文檔**庫設定**] 功能區按鈕。

3. 在 [**許可權與管理**] 區段中，選擇 [**工作流程設定**] 連結，然後選擇 [**工作流程**] 頁面上的 [**新增工作流程**] 連結。

4. 在 [工作流程設定] 頁面的頂端清單中，選擇 [ **ExpenseReport-workflow1.xaml** ] 範本。

5. 在下一個欄位中，輸入**ExpenseReportWorkflow** ，然後選擇 [**下一步]** 按鈕。

     這會將工作流程與**共用文件**清單產生關聯，並顯示工作流程關聯表單。

6. 在 [**自動核准限制**] 文字方塊中，輸入**1200** ，然後選擇 [**關聯工作流程**] 按鈕。

## <a name="start-the-workflow"></a>啟動工作流程
 接下來，將工作流程與 [**共用文件**] 清單中的其中一個檔產生關聯，以顯示工作流程初始表單。

#### <a name="to-start-the-workflow"></a>若要啟動工作流程

1. 在 [SharePoint] 頁面上，選擇 [**首頁**] 按鈕。

2. 選擇 [快速啟動] 列上的 [**共用文件**] 連結，以顯示 [**共用文件**] 清單。

3. 選擇頁面頂端 [連結**庫工具**] 索引標籤上的 [**檔**] 連結，然後選擇功能區上的 [**上傳檔**] 按鈕，將新的檔上傳至 [**共用文件**] 清單中。

4. 在 [**上傳檔**] 對話方塊中，選擇 [**流覽]** 按鈕，選擇任何檔檔，選擇 [**開啟**] 按鈕，然後選擇 [**確定]** 按鈕。

     您可以在此對話方塊中變更檔的設定，但請選擇 [**儲存**] 按鈕，將其保留為預設值。

5. 選擇上傳的檔，選擇顯示的下拉箭號，然後選擇 [**工作流程**] 專案。

6. 選擇 [ExpenseReportWorkflow] 旁的影像。

     這會顯示工作流程初始表單。 （請注意，顯示在 [**自動核准限制**] 方塊中的值是唯讀的，因為它是在 [關聯] 表單中輸入）。

7. 在 [**支出總計**] 文字方塊中，輸入**1600**，然後選擇 [**啟動工作流程**] 按鈕。

     這會再次顯示 [**共用文件**] 清單。 名為**ExpenseReportWorkflow**且值為**Completed**的新資料行會新增至工作流程剛啟動的專案。

8. 選擇上傳檔旁的下拉式箭號，然後選擇 [**工作流程**] 專案以顯示 [工作流程狀態] 頁面。 選擇 [**已完成的工作流程**] 底下的 [**完成**] 值。 工作會列在 **[工作]** 區段底下。

9. 選擇工作的標題，以顯示其工作詳細資料。

10. 返回**SharedDocuments**清單，並使用相同的檔或不同的來重新開機工作流程。

11. 在起始頁面上輸入小於或等於 [關聯] 頁面上輸入金額的金額（**1200**）。

     發生這種情況時，會建立記錄清單中的專案，而不是工作。 專案會顯示在 [工作流程狀態] 頁面的 [**工作流程歷程記錄**] 區段中。 請注意歷程記錄事件之 [**結果**] 資料行中的訊息。 它包含在 `logToHistoryListActivity1.MethodInvoking` 事件中輸入的文字，其中包含已自動核准的數量。

## <a name="next-steps"></a>後續步驟
 您可以從下列主題深入瞭解如何建立工作流程範本：

- 若要深入瞭解 SharePoint 工作流程，請參閱[Windows Sharepoint Services 中的工作流程](/previous-versions/office/developer/sharepoint-2010/ms416312(v=office.14))。

## <a name="see-also"></a>請參閱
- [建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [逐步解說：將應用程式頁面新增至工作流程](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
