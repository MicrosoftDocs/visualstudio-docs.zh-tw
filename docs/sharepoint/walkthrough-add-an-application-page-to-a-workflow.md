---
title: 逐步解說：將應用程式頁面加入至工作流程 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f54914e6676e0cc2400fa04ebb089fac08f58c3c
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015490"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>逐步解說：將應用程式頁面新增至工作流程
  本逐步解說示範如何將顯示從工作流程衍生之資料的應用程式頁面加入至工作流程專案。 它是根據[逐步解說：使用關聯與初始表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)主題中所述的專案來建立。

 本逐步解說將示範下列工作：

- 將 ASPX 應用程式頁面加入至 SharePoint 工作流程專案。

- 從工作流程專案取得資料並加以操作。

- 在應用程式頁面上的資料表中顯示資料。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- 支援的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。

- Visual Studio。

- 您也必須完成[逐步解說：使用關聯與初始表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)主題中的專案。

## <a name="ammend-the-workflow-code"></a>Ammend 工作流程程式碼
 首先，將一行程式碼新增至工作流程，將結果資料行的值設定為支出報表的金額。 此值稍後會用於費用報表摘要計算中。

#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>若要在工作流程中設定結果資料行的值

1. 從主題[逐步解說：使用關聯和初始表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)中，載入已完成的專案 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

2. 開啟*Workflow1.cs*或*workflow1.xaml*的程式碼（視您的程式設計語言而定）。

3. 在方法的底部 `createTask1_MethodInvoking` ，新增下列程式碼：

    ```vb
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =
      workflowProperties.InitiationData
    ```

    ```csharp
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =
      workflowProperties.InitiationData;
    ```

## <a name="create-an-application-page"></a>建立應用程式頁面
 接下來，將 ASPX 表單新增至專案。 此表單會顯示從費用報表工作流程專案取得的資料。 若要這麼做，您將加入應用程式頁面。 應用程式頁面會使用與其他 SharePoint 頁面相同的主版頁面，這表示它會類似 SharePoint 網站上的其他頁面。

#### <a name="to-add-an-application-page-to-the-project"></a>將應用程式頁面加入至專案

1. 選擇 [ExpenseReport] 專案，然後在功能表列上，選擇 [**專案**] [  >  **加入新專案**]。

2. 在 [**範本**] 窗格中，選擇 [**應用程式] 頁面**範本，使用專案專案的預設名稱（**ApplicationPage1 .aspx**），然後選擇 [**加入**] 按鈕。

3. 在 ApplicationPage1 的中 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ，將區段取代為 `PlaceHolderMain` 下列內容：

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
        <asp:Label ID="Label1" runat="server" Font-Bold="True"
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>
        <br />
        <asp:Table ID="Table1" runat="server">
        </asp:Table>
    </asp:Content>
    ```

     此程式碼會將資料表連同標題一起加入至頁面。

4. 將區段取代為下列專案，以將標題新增至應用程式頁面 `PlaceHolderPageTitleInTitleArea` ：

    ```aspx-csharp
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >
        Expense Report Summary
    </asp:Content>
    ```

## <a name="code-the-application-page"></a>編寫應用程式頁面
 接下來，將程式碼加入至 [支出報表摘要] 應用程式頁面。 當您開啟頁面時，程式碼會掃描 SharePoint 中的工作清單是否有超過配置消費限制的費用。 此報表會將每個專案與費用的總和一起列出。

#### <a name="to-code-the-application-page"></a>編碼應用程式頁面

1. 選擇 [ **ApplicationPage1** ] 節點，然後在功能表列上選擇 [ **View**  >  **Code** ]，以顯示應用程式頁面背後的程式碼。

2. 在類別的頂端，以下列內容取代**using**或**Import**語句（視您的程式設計語言而定）：

    ```vb
    Imports System
    Imports Microsoft.SharePoint
    Imports Microsoft.SharePoint.WebControls
    Imports System.Collections
    Imports System.Data
    Imports System.Web.UI
    Imports System.Web.UI.WebControls
    Imports System.Web.UI.WebControls.WebParts
    Imports System.Drawing
    Imports Microsoft.SharePoint.Navigation
    ```

    ```csharp
    using System;
    using Microsoft.SharePoint;
    using Microsoft.SharePoint.WebControls;
    using System.Collections;
    using System.Data;
    using System.Web.UI;
    using System.Web.UI.WebControls;
    using System.Web.UI.WebControls.WebParts;
    using System.Drawing;
    using Microsoft.SharePoint.Navigation;
    ```

3. 將下列程式碼新增至 `Page_Load` 方法：

    ```vb
    Try
        ' Reference the Tasks list on the SharePoint site.
        ' Replace "TestServer" with a valid SharePoint server name.
        Dim site As SPSite = New SPSite("http://TestServer")
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")
        ' string text = "";
        Dim sum As Integer = 0
        Table1.Rows.Clear()
        ' Add table headers.
        Dim hr As TableHeaderRow = New TableHeaderRow
        hr.BackColor = Color.LightBlue
        Dim hc1 As TableHeaderCell = New TableHeaderCell
        Dim hc2 As TableHeaderCell = New TableHeaderCell
        hc1.Text = "Expense Report Name"
        hc2.Text = "Amount Exceeded"
        hr.Cells.Add(hc1)
        hr.Cells.Add(hc2)
        ' Add the TableHeaderRow as the first item
        ' in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr)
        ' Iterate through the tasks in the Task list and collect those
        ' that have values in the "Related Content" and "Outcome" fields
        ' - the fields written to when expense approval is required.
        For Each item As SPListItem In list.Items
            Dim s_relContent As String = ""
            Dim s_outcome As String = ""
            Try
                ' Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related Content")
                s_outcome = item.GetFormattedValue("Outcome")
            Catch erx As System.Exception
                ' Task does not have fields - skip it.
                Continue For
            End Try
            ' Convert amount to an int and keep a running total.
            If (Not String.IsNullOrEmpty(s_relContent) And Not
              String.IsNullOrEmpty(s_outcome)) Then
                sum = (sum + Convert.ToInt32(s_outcome))
                Dim relContent As TableCell = New TableCell
                relContent.Text = s_relContent
                Dim outcome As TableCell = New TableCell
                outcome.Text = ("$" + s_outcome)
                Dim dataRow2 As TableRow = New TableRow
                dataRow2.Cells.Add(relContent)
                dataRow2.Cells.Add(outcome)
                Table1.Rows.Add(dataRow2)
            End If
        Next
        ' Report the sum of the reports in the table footer.
        Dim tfr As TableFooterRow = New TableFooterRow
        tfr.BackColor = Color.LightGreen
        ' Create a TableCell object to contain the
        ' text for the footer.
        Dim ftc1 As TableCell = New TableCell
        Dim ftc2 As TableCell = New TableCell
        ftc1.Text = "TOTAL: "
        ftc2.Text = ("$" + Convert.ToString(sum))
        ' Add the TableCell object to the Cells
        ' collection of the TableFooterRow.
        tfr.Cells.Add(ftc1)
        tfr.Cells.Add(ftc2)
        ' Add the TableFooterRow to the Rows
        ' collection of the table.
        Table1.Rows.Add(tfr)
    Catch errx As Exception
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))
    End Try
    ```

    ```csharp
    try
    {
        // Reference the Tasks list on the SharePoint site.
        // Replace "TestServer" with a valid SharePoint server name.
        SPSite site = new SPSite("http://TestServer");
        SPList list = site.AllWebs[0].Lists["Tasks"];

        // string text = "";
        int sum = 0;

        Table1.Rows.Clear();

        // Add table headers.
        TableHeaderRow hr = new TableHeaderRow();
        hr.BackColor = Color.LightBlue;
        TableHeaderCell hc1 = new TableHeaderCell();
        TableHeaderCell hc2 = new TableHeaderCell();
        hc1.Text = "Expense Report Name";
        hc2.Text = "Amount Exceeded";
        hr.Cells.Add(hc1);
        hr.Cells.Add(hc2);
        // Add the TableHeaderRow as the first item
        // in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr);

        // Iterate through the tasks in the Task list and collect those
        // that have values in the "Related Content" and "Outcome"
        // fields - the fields written to when expense approval is
        // required.
        foreach (SPListItem item in list.Items)
        {
            string s_relContent = "";
            string s_outcome = "";

            try
            {
                // Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related
                  Content");
                s_outcome = item.GetFormattedValue("Outcome");
            }
            catch
            {
                // Task does not have fields - skip it.
                continue;
            }

            if (!String.IsNullOrEmpty(s_relContent) &&
              !String.IsNullOrEmpty(s_outcome))
            {
                // Convert amount to an int and keep a running total.
                sum += Convert.ToInt32(s_outcome);
                TableCell relContent = new TableCell();
                relContent.Text = s_relContent;
                TableCell outcome = new TableCell();
                outcome.Text = "$" + s_outcome;
                TableRow dataRow2 = new TableRow();
                dataRow2.Cells.Add(relContent);
                dataRow2.Cells.Add(outcome);
                Table1.Rows.Add(dataRow2);
            }
        }

        // Report the sum of the reports in the table footer.
           TableFooterRow tfr = new TableFooterRow();
        tfr.BackColor = Color.LightGreen;

        // Create a TableCell object to contain the
        // text for the footer.
        TableCell ftc1 = new TableCell();
        TableCell ftc2 = new TableCell();
        ftc1.Text = "TOTAL: ";
        ftc2.Text = "$" + Convert.ToString(sum);

        // Add the TableCell object to the Cells
        // collection of the TableFooterRow.
        tfr.Cells.Add(ftc1);
        tfr.Cells.Add(ftc2);

        // Add the TableFooterRow to the Rows
        // collection of the table.
        Table1.Rows.Add(tfr);
    }

    catch (Exception errx)
    {
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());
    }
    ```

    > [!WARNING]
    > 請務必將程式碼中的 "TestServer" 取代為執行 SharePoint 的有效伺服器名稱。

## <a name="test-the-application-page"></a>測試應用程式頁面
 接下來，判斷 [應用程式] 頁面是否會正確顯示費用資料。

#### <a name="to-test-the-application-page"></a>若要測試應用程式頁面

1. 選擇**F5**鍵以執行專案，並將其部署至 SharePoint。

2. 選擇 [**首頁**] 按鈕，然後選擇 [快速啟動] 列上的 [**共用文件**] 連結，以在 SharePoint 網站上顯示 [共用文件] 清單。

3. 若要代表此範例的費用報表，請在頁面頂端的 [ **LibraryTools** ] 索引標籤上選擇 [**檔**] 連結，然後選擇工具功能區上的 [**上傳檔**] 按鈕，將一些新檔上傳到 [檔] 清單中。

4. 上傳一些檔之後，請在頁面頂端的 [ **LibraryTools** ] 索引標籤上選擇 [文檔**庫**] 連結，然後選擇工具功能區上的 [文檔**庫設定**] 按鈕，以具現化工作流程。

5. 在 [**文件庫設定**] 頁面中，選擇 [**許可權與管理**] 區段中的 [**工作流程設定**] 連結。

6. 在 [**工作流程設定**] 頁面中，選擇 [**新增工作流程**] 連結。

7. 在 [**新增工作流程**] 頁面中，選擇 [ **ExpenseReport-workflow1.xaml** ] 工作流程，輸入工作流程的名稱（例如**ExpenseTest**），然後選擇 [**下一步]** 按鈕。

    [工作流程關聯] 表單隨即出現。 使用它來報告支出限制金額。

8. 在 [關聯] 表單的 [**自動核准限制**] 方塊中，輸入**1000** ，然後選擇 [**關聯工作流程**] 按鈕。

9. 選擇 [**首頁**] 按鈕以返回 SharePoint 首頁。

10. 選擇 [快速啟動] 列上的 [**共用文件**] 連結。

11. 選擇其中一個已上傳的檔以顯示下拉箭號，然後選擇 [**工作流程**] 專案。

12. 選擇 ExpenseTest 旁的影像，以顯示工作流程初始表單。

13. 在 [**支出總計**] 文字方塊中，輸入大於1000的值，然後選擇 [**啟動工作流程**] 按鈕。

     當回報的費用超過配置的支出金額時，就會將工作新增至工作清單。 名為**ExpenseTest**且值為**Completed**的資料行也會加入至 [共用文件] 清單中的 [費用報表] 專案。

14. 在 [共用文件] 清單中，對其他檔重複步驟 11-13。 （確切的檔數目並不重要）。

15. 在網頁瀏覽器中開啟下列 URL，以顯示 [費用報表摘要應用程式] 頁面： **Http://**<em>SystemName</em>**/_layouts/expensereport/applicationpage1.aspx**。

     [費用報表摘要] 頁面會列出超過配置金額的所有費用報表、其超過其數量，以及所有報表的總金額。

## <a name="next-steps"></a>後續步驟
 如需 SharePoint 應用程式頁面的詳細資訊，請參閱[建立 sharepoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。

 您可以在下列主題中，使用 Visual Studio 的 Visual Web 設計工具，進一步瞭解如何設計 SharePoint 網頁內容：

- [建立 SharePoint 的 web 元件](../sharepoint/creating-web-parts-for-sharepoint.md)。

- [為 web 元件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)。

## <a name="see-also"></a>另請參閱

- [逐步解說：使用關聯與初始表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [如何：建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md)
- [建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)