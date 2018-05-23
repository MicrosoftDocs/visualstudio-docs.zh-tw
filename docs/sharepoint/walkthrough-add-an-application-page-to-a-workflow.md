---
title: 逐步解說： 將應用程式頁面加入至工作流程 |Microsoft 文件
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
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8ed3278a237633cbf7f15806fa0efa9b3bc33bb6
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>逐步解說：將應用程式頁面新增到工作流程
  本逐步解說示範如何將應用程式頁面會顯示在工作流程專案從工作流程衍生的資料。 它是在專案中的主題描述基礎[逐步解說： 建立工作流程關聯與初始化表單與](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。  
  
 本逐步解說將示範下列工作：  
  
-   將 ASPX 應用程式頁面加入 SharePoint 工作流程專案。  
  
-   取得工作流程專案中的資料，並管理它。  
  
-   在應用程式頁面上的表格中顯示的資料。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的版本[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]和 SharePoint。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
-   您也必須完成本主題中的專案[逐步解說： 建立工作流程關聯與初始化表單與](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。  
  
## <a name="amending-the-workflow-code"></a>修改工作流程程式碼  
 首先，加入一行程式碼工作流程，以設定結果資料行值的經費支出報表數量。 稍後的經費支出報表摘要計算會使用此值。  
  
#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>在工作流程中設定結果資料行的值  
  
1.  載入已完成的專案，從主題[逐步解說： 建立工作流程關聯與初始化表單與](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)到[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  開啟程式碼 Workflow1.cs 或 Workflow1.vb （取決於您的程式語言）。  
  
3.  底部`createTask1_MethodInvoking`方法，加入下列程式碼：  
  
    ```vb  
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =   
      workflowProperties.InitiationData  
    ```  
  
    ```csharp  
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =   
      workflowProperties.InitiationData;  
    ```  
  
## <a name="creating-an-application-page"></a>建立應用程式頁面  
 接下來，將 ASPX 表單加入專案。 此表單會顯示取自經費支出報表工作流程專案的資料。 若要這樣做，您將加入的應用程式頁面。 應用程式頁面上會與其他 SharePoint 頁面，這表示看起來類似 SharePoint 網站上的其他頁面使用相同的主版頁面。  
  
#### <a name="to-add-an-application-page-to-the-project"></a>將應用程式頁面加入至專案  
  
1.  選擇 ExpenseReport 專案，然後在功能表列上選擇 **專案**，**加入新項目**。  
  
2.  在**範本** 窗格中，選擇**應用程式頁面上**範本，使用預設名稱為專案項目 (**ApplicaitonPage1.aspx**)，並選擇**新增** 按鈕。  
  
3.  在[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]的 ApplicationPage1.aspx，取代`PlaceHolderMain`有下列區段：  
  
    ```aspx-csharp  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
        <asp:Label ID="Label1" runat="server" Font-Bold="True"   
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>  
        <br />  
        <asp:Table ID="Table1" runat="server">  
        </asp:Table>  
    </asp:Content>  
    ```  
  
     此程式碼會將資料表加入至標題以及頁面。  
  
4.  加入應用程式頁面的標題來取代`PlaceHolderPageTitleInTitleArea`有下列區段：  
  
    ```aspx-csharp  
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >  
        Expense Report Summary  
    </asp:Content>  
    ```  
  
## <a name="coding-the-application-page"></a>程式碼撰寫的應用程式頁面  
 接下來，加入程式碼的經費支出報表摘要的應用程式頁面。 當您開啟頁面時，程式碼掃描中 SharePoint 工作清單中，超過已配置的消費限制的費用。 此報表會列出每個項目與費用的總和。  
  
#### <a name="to-code-the-application-page"></a>應用程式頁面上的程式碼  
  
1.  選擇**ApplicationPage1.aspx** ] 節點，然後在功能表列上選擇 [**檢視**，**程式碼**顯示應用程式頁面背後的程式碼。  
  
2.  取代**使用**或**匯入**（取決於您的程式語言） 陳述式具有下列類別的頂端：  
  
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
  
3.  將下列程式碼加入 `Page_Load` 方法：  
  
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
    >  請務必在程式碼中的"TestServer"取代執行 SharePoint 的有效伺服器名稱。  
  
## <a name="testing-the-application-page"></a>測試應用程式頁面  
 接下來，判斷是否應用程式頁面上顯示的費用資料正確。  
  
#### <a name="to-test-the-application-page"></a>若要測試應用程式頁面  
  
1.  選擇 F5 鍵執行，並將專案部署到 SharePoint。  
  
2.  選擇**首頁**按鈕，然後再選擇**Shared Documents**快速啟動列來顯示在 SharePoint 網站上的共用文件清單的連結。  
  
3.  若要表示經費支出報表，此範例中，某些新文件上傳文件的清單中選擇**文件**連結**LibraryTools** ] 索引標籤頂端的頁面，然後選擇 [ **上傳文件**工具功能區上的按鈕。  
  
4.  您上傳的某些文件之後，具現化工作流程選擇**文件庫**連結**LibraryTools**  索引標籤頂端的頁面，然後選擇**文件庫設定**工具功能區上的按鈕。  
  
5.  在**文件庫設定**頁面上，選擇**工作流程設定**中連結**權限與管理**> 一節。  
  
6.  在**工作流程設定**頁面上，選擇**加入工作流程**連結。  
  
7.  在**加入工作流程**頁面上，選擇**ExpenseReport-Workflow1**工作流程中，輸入工作流程的名稱，例如**ExpenseTest**，然後選擇 [ **下一步**] 按鈕。  
  
     工作流程關聯表單隨即出現。 您可以使用它來報告支出限制金額。  
  
8.  在關聯表單中，輸入**1000年**到**自動核准限制**方塊，然後再選擇**產生關聯的工作流程** 按鈕。  
  
9. 選擇**家用**按鈕返回 SharePoint 首頁上。  
  
10. 選擇**Shared Documents**快速啟動列上的連結。  
  
11. 選擇其中一個顯示下拉式箭號，選擇它，然後選擇 上傳文件**工作流程**項目。  
  
12. 選擇要顯示工作流程初始表單 ExpenseTest 旁邊映像。  
  
13. 在**費用總計** 文字方塊中，輸入大於 1000年的值，然後選擇**啟動工作流程** 按鈕。  
  
     當報告的費用超過已配置的支出金額時，工作會加入至工作清單。 名為資料行**ExpenseTest**值**已完成**也會加入至共用文件清單的經費支出報表項目。  
  
14. 重複步驟 11 – 13 與共用文件清單中的其他文件。 （文件的確切數目並不重要）。  
  
15. 在網頁瀏覽器中開啟下列 URL 顯示經費支出報表摘要的應用程式頁面上： **http://***系統名稱***/_layouts/ExpenseReport/ApplicationPage1.aspx**。  
  
     費用報表的 [摘要] 頁面會列出所有超過配置的量的費用報表、 它，超過的數量和所有報表的總金額。  
  
## <a name="next-steps"></a>後續步驟  
 如需 SharePoint 應用程式頁面的詳細資訊，請參閱[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
 您可以深入了解如何使用 Visual Studio 中的 Visual Web 設計工具，從下列主題來設計 SharePoint 網頁內容：  
  
-   [建立 SharePoint Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)。  
  
-   [為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 使用關聯與初始化表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [如何： 建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md)   
 [建立 SharePoint 應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  