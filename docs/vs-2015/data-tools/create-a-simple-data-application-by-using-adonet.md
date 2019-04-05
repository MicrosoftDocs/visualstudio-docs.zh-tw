---
title: 使用 ADO.NET 建立簡單資料應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
caps.latest.revision: 46
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9f3c5dd921ab9c86d197d22aea63bad86264bb5b
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "58941521"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>使用 ADO.NET 建立簡單的資料應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
建立應用程式來管理資料庫中的資料時，您會執行基本工作，例如定義連接字串、插入資料及執行預存程序。 遵循本主題，您可以探索如何使用 Visual C# 或 Visual Basic 和 ADO.NET 與簡單的 Windows Forms 「 資料表單 」 應用程式內的資料庫互動。  所有的.NET 資料技術，包括資料集，LINQ to SQL 和 Entity Framework，最後執行非常類似於本文中所示的步驟。  
  
 這篇文章示範簡單的方式非常快速的方式取得移出資料庫的資料。 如果您的應用程式需要非一般的方式修改資料，並更新資料庫，您應該考慮使用 Entity Framework，並使用資料繫結至自動同步處理使用者介面控制項的基礎資料中的變更。  
  
> [!IMPORTANT]
>  為了簡化程式碼，它不會包含可實際執行的例外狀況處理。  
  
 **本主題內容**  
  
-   [設定範例資料庫](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)  
  
-   [建立表單，並加入控制項](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)  
  
-   [儲存連接字串](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)  
  
-   [擷取連接字串](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)  
  
-   [撰寫表單的程式碼](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)  
  
-   [測試您的應用程式](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)  
  
## <a name="prerequisites"></a>必要條件  
 若要建立應用程式，您需要：  
  
- Visual Studio Community 版本。  
  
- SQL Server Express LocalDB。  
  
- 您依照下列中的步驟建立的小型範例資料庫[使用指令碼中建立 SQL database](../data-tools/create-a-sql-database-by-using-a-script.md)。  
  
- 您設定之後的資料庫連接字串。 您可以找到此值，藉由開啟**SQL Server 物件總管**，開啟資料庫的捷徑功能表，選取**屬性**，然後捲動至**ConnectionString**屬性。  
  
  本主題假設您熟悉 Visual Studio IDE 的基本功能，且可以建立 Windows Form 應用程式、將表單加入至該專案、將按鈕和其他控制項放置在這些表單上、設定這些控制項的屬性，以及編碼簡單事件。 如果您不熟悉這些工作，我們建議您先完成[Getting Started with Visual C# 和 Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md)再開始本主題。  
  
##  <a name="BKMK_setupthesampledatabase"></a> 設定範例資料庫  
 本逐步解說的範例資料庫包含 Customer 和 Orders 資料表。 資料表一開始不包含任何資料，但是當您執行建立的應用程式時，您會加入資料。 此資料庫也會有五個簡單的預存程序。 [使用指令碼中建立 SQL database](../data-tools/create-a-sql-database-by-using-a-script.md)包含建立資料表、 主要與外部索引鍵、 條件約束和預存程序的 TRANSACT-SQL 指令碼。  
  
##  <a name="BKMK_createtheformsandaddcontrols"></a> 建立表單，並加入控制項  
  
1. 建立 Windows Forms 應用程式的專案，並命名它 SimpleDataApp。  
  
    Visual Studio 會建立專案和數個檔案，包括名為 Form1 的空白 Windows Form。  
  
2. 將兩個 Windows 表單新增至專案，使其具有三種形式，然後提供下列名稱：  
  
   -   巡覽  
  
   -   NewCustomer  
  
   -   FillOrCancel  
  
3. 為每個表單加入下圖中顯示的文字方塊、按鈕和其他控制項。 對每個控制項設定資料表描述的屬性。  
  
   > [!NOTE]
   >  加入群組方塊和標籤控制項會更清楚，但是不在程式碼中使用。  
  
   **巡覽表單**  
  
   ![瀏覽對話方塊](../data-tools/media/simpleappnav.png "SimpleAppNav")  
  
|瀏覽表單的控制項|屬性|  
|--------------------------------------|----------------|  
|按鈕|Name = btnGoToAdd|  
|按鈕|Name = btnGoToFillOrCancel|  
|按鈕|Name = btnExit|  
  
 **NewCustomer 表單**  
  
 ![新增客戶以及下訂單](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")  
  
|NewCustomer 表單的控制項|屬性|  
|---------------------------------------|----------------|  
|TextBox|Name = txtCustomerName|  
|TextBox|Name = txtCustomerID<br /><br /> Readonly = True|  
|按鈕|Name = btnCreateAccount|  
|NumericUpdown|DecimalPlaces = 0<br /><br /> Maximum = 5000<br /><br /> Name = numOrderAmount|  
|DateTimePicker|Format = Short<br /><br /> Name = dtpOrderDate|  
|按鈕|Name = btnPlaceOrder|  
|按鈕|Name = btnAddAnotherAccount|  
|按鈕|Name = btnAddFinish|  
  
 **FillOrCancel 表單**  
  
 ![填寫或取消訂單](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")  
  
|FillOrCancel 表單的控制項|屬性|  
|----------------------------------------|----------------|  
|TextBox|Name = txtOrderID|  
|按鈕|Name = btnFindByOrderID|  
|DateTimePicker|Format = Short<br /><br /> Name = dtpFillDate|  
|DataGridView|Name = dgvCustomerOrders<br /><br /> Readonly = True<br /><br /> RowHeadersVisible = False|  
|按鈕|Name = btnCancelOrder|  
|按鈕|Name = btnFillOrder|  
|按鈕|Name = btnFinishUpdates|  
  
##  <a name="BKMK_storetheconnectionstring"></a> 儲存連接字串  
 當您的應用程式嘗試開啟資料庫的連接時，應用程式必須存取連接字串。 若要避免手動輸入字串，每個表單上，將字串儲存在應用程式組態檔，在您的專案，並建立從您的應用程式中的任何表單呼叫方法時，會傳回字串的方法。  
  
 您可以找到中的連接字串**SQL Server 物件總管**以滑鼠右鍵按一下資料庫，選取**屬性**，再尋找 ConnectionString 屬性。 您可以使用 Ctrl + A 來選取字串。  
  
1.  在 **方案總管**，選取**屬性**節點底下的專案，然後選取**Settings.settings**。  
  
2.  在 **名稱**資料行中，輸入`connString`。  
  
3.  在 **型別**清單中，選取 **（連接字串）**。  
  
4.  在 **領域**清單中，選取**應用程式**。  
  
5.  在 [**值**] 欄中，輸入您的連接字串 （不含任何外部引號括住），然後儲存變更。  
  
> [!NOTE]
>  在實際的應用程式中，您應該在連接字串安全地儲存中, 所述[連接字串和組態檔](http://msdn.microsoft.com/library/37df2641-661e-407a-a3fb-7bf9540f01e8)。  
  
##  <a name="BKMK_retrievetheconnectionstring"></a> 擷取連接字串  
  
1.  在功能表列上選取**專案** > **加入參考**，然後加入 System.Configuration.dll 的參考。  
  
2.  在功能表列上選取**專案** > **加入類別**若要將類別檔案新增至您的專案，然後將檔案命名`Utility`。  
  
     Visual Studio 會建立檔案，並顯示在**方案總管 中**。  
  
3.  在 [公用程式] 檔案中，將預留位置程式碼取代為下列程式碼。 請注意編號的註解 (以 Util- 為前置詞)，來識別程式碼區段。 下表顯示程式碼呼叫關鍵點。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.Threading.Tasks;  
    //Util-1 More namespaces.  
    using System.Configuration;   
  
    namespace SimpleDataApp  
    {  
        internal class Utility  
        {  
  
            //Get the connection string from App config file.  
            internal static string GetConnectionString()  
            {  
                //Util-2 Assume failure.  
                string returnValue = null;  
  
                //Util-3 Look for the name in the connectionStrings section.  
                ConnectionStringSettings settings =  
                ConfigurationManager.ConnectionStrings["SimpleDataApp.Properties.Settings.connString"];  
  
                //If found, return the connection string.  
                if (settings != null)  
                    returnValue = settings.ConnectionString;  
  
                return returnValue;  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.Linq  
    Imports System.Text  
    Imports System.Threading.Tasks  
    ' Util-1 More namespaces.  
    Imports System.Configuration  
  
    Namespace SimpleDataApp  
        Friend Class Utility  
  
            ' Get connection string from App config file.  
            Friend Shared Function GetConnectionString() As String  
  
                ' Util-2 Assume failure.  
                Dim returnValue As String = Nothing  
  
                ' Util-3 Look for the name in the connectionStrings section.  
                Dim settings As ConnectionStringSettings = ConfigurationManager.ConnectionStrings("SimpleDataApp.My.MySettings.connString")  
  
                ' If found, return the connection string.  
                If settings IsNot Nothing Then  
                    returnValue = settings.ConnectionString  
                End If  
  
                Return returnValue  
            End Function  
        End Class  
    End Namespace  
    ```  
  
    |註解|描述|  
    |-------------|-----------------|  
    |Util-1|加入 `System.Configuration` 命名空間。|  
    |Util-2|定義變數 `returnValue`，並將它初始化為 `null` (C#) 或 `Nothing` (Visual Basic)。|  
    |Util-3|即使您輸入`connString`中的連接字串的名稱作為**屬性**視窗中，您必須指定`"SimpleDataApp.Properties.Settings.connString"`(C#) 或`"SimpleDataApp.My.MySettings.connString"`(Visual Basic) 程式碼中。|  
  
##  <a name="BKMK_writethecodefortheforms"></a> 撰寫表單的程式碼  
 本章節包含每個表單的工作，而且會顯示建立表單之程式碼的簡短概觀。 編號的註解會識別程式碼區段。  
  
### <a name="navigation-form"></a>導覽表單  
 當您執行應用程式時，瀏覽表單隨即開啟。 [新增帳戶] 按鈕會開啟 NewCustomer 表單。 [填寫或取消訂單] 按鈕會開啟 FillOrCancel 表單。 [結束] 按鈕會關閉應用程式。  
  
#### <a name="make-the-navigation-form-the-startup-form"></a>讓瀏覽表單成為啟動表單  
 如果您使用 C# 中，在**方案總管**，開啟 Program.cs，並接著變更`Application.Run`這一行： `Application.Run(new Navigation());`  
  
 如果您使用 Visual Basic 中，在**方案總管**，開啟**屬性**視窗中，選取**應用程式**索引標籤，然後再選取  **SimpleDataApp.Navigation**中**啟動表單**清單。  
  
#### <a name="create-event-handlers"></a>建立事件處理常式  
 按兩下表單，以建立空白的事件處理常式方法上的三個按鈕。  
  
#### <a name="create-code-for-navigation"></a>建立導覽的程式碼  
 在導覽表單中，將現有程式碼取代為下面程式碼。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
  
namespace SimpleDataApp  
{  
    public partial class Navigation : Form  
    {  
        public Navigation()  
        {  
            InitializeComponent();  
        }  
  
        //Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.  
        private void btnGoToAdd_Click(object sender, EventArgs e)  
        {  
            Form frm = new NewCustomer();  
            frm.Show();  
        }  
  
        //Open the FillorCancel form as a dialog box.  
        private void btnGoToFillOrCancel_Click(object sender, EventArgs e)  
        {  
            Form frm = new FillOrCancel();  
            frm.ShowDialog();  
        }  
  
        //Close the application, not just the Navigation form.  
        private void btnExit_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
  
Namespace SimpleDataApp  
    Partial Public Class Navigation  
        Inherits Form  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.  
        Private Sub btnGoToAdd_Click() Handles btnGoToAdd.Click  
            Dim frm As Form = New NewCustomer()  
            frm.Show()  
        End Sub  
  
        ' Open the FillorCancel form as a dialog box.  
        Private Sub btnGoToFillOrCancel_Click() Handles btnGoToFillOrCancel.Click  
            Dim frm As Form = New FillOrCancel()  
            frm.ShowDialog()  
        End Sub  
  
        ' Close the application, not just the Navigation form.  
        Private Sub btnExit_Click() Handles btnExit.Click  
            Me.Close()  
        End Sub  
    End Class  
End Namespace  
  
```  
  
### <a name="newcustomer-form"></a>NewCustomer 表單  
 當您輸入客戶名稱，然後選取**建立帳戶**按鈕時，NewCustomer 表單建立客戶帳戶，並且與 SQL Server 會傳回 IDENTITY 值做為新的帳戶號碼。 您再訂購新的帳戶指定數量和訂單日期，然後選取**訂購** 按鈕。  
  
#### <a name="create-event-handlers"></a>建立事件處理常式  
 為表單上的每個按鈕建立空白 Click 事件處理常式。  
  
#### <a name="create-code-for-newcustomer"></a>建立 NewCustomer 的程式碼  
 將下列程式碼加入至 NewCustomer 表單。 使用程式碼之後的已編號的註解和資料表，以逐步執行每個程式碼區塊。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
//NC-1 More namespaces.  
using System.Data.SqlClient;  
using System.Configuration;  
  
namespace SimpleDataApp  
{  
    public partial class NewCustomer : Form  
    {  
        //NC-2 Storage for IDENTITY values returned from database.  
        private int parsedCustomerID;  
        private int orderID;  
  
        //NC-3 Specify a connection string.  
        string connstr = SimpleDataApp.Utility.GetConnectionString();  
  
        public NewCustomer()  
        {  
            InitializeComponent();  
        }  
  
        //NC-4 Create account.  
        private void btnCreateAccount_Click(object sender, EventArgs e)  
        {  
            //NC-5 Set up and run stored procedure only if Customer Name is present.  
            if (isCustomerName())  
            {  
  
                //NC-6 Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //NC-7 Create a SqlCommand, and identify it as a stored procedure.  
                SqlCommand cmdNewCustomer = new SqlCommand("Sales.uspNewCustomer", conn);  
                cmdNewCustomer.CommandType = CommandType.StoredProcedure;  
  
                //NC-8 Add input parameter from the stored procedure and specify what to use as its value.  
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerName", SqlDbType.NVarChar, 40));  
                cmdNewCustomer.Parameters["@CustomerName"].Value = txtCustomerName.Text;  
  
                //NC-9 Add output parameter.  
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));  
                cmdNewCustomer.Parameters["@CustomerID"].Direction = ParameterDirection.Output;  
  
                //NC-10 try-catch-finally  
                try  
                {  
                    //NC-11 Open the connection.  
                    conn.Open();  
  
                    //NC-12 Run the stored procedure.  
                    cmdNewCustomer.ExecuteNonQuery();  
  
                    //NC-13 Customer ID is an IDENTITY value from the database.   
                    this.parsedCustomerID = (int)cmdNewCustomer.Parameters["@CustomerID"].Value;  
                    this.txtCustomerID.Text = Convert.ToString(parsedCustomerID);  
  
                }  
                catch  
                {  
                    //NC-14 A simple catch.  
  
                    MessageBox.Show("Customer ID was not returned. Account could not be created.");  
                }  
                finally  
                {  
                    //NC-15 Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //NC-16 Verify that Customer Name is present.  
        private bool isCustomerName()  
        {  
            if (txtCustomerName.Text == "")  
            {  
                MessageBox.Show("Please enter a name.");  
                return false;  
            }  
            else  
            {  
                return true;  
            }  
        }  
  
        //NC-17 Place order.  
        private void btnPlaceOrder_Click(object sender, EventArgs e)  
        {  
            //NC-18 Set up and run stored procedure only if required input is present.  
            if (isPlaceOrderReady())  
            {  
                // Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //NC-19 Create SqlCommand and identify it as a stored procedure.  
                SqlCommand cmdNewOrder = new SqlCommand("Sales.uspPlaceNewOrder", conn);  
                cmdNewOrder.CommandType = CommandType.StoredProcedure;  
  
                //NC-20 @CustomerID, which was an output parameter from uspNewCustomer.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));  
                cmdNewOrder.Parameters["@CustomerID"].Value = this.parsedCustomerID;  
  
                //NC-21 @OrderDate.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@OrderDate", SqlDbType.DateTime, 8));  
                cmdNewOrder.Parameters["@OrderDate"].Value = dtpOrderDate.Value;  
  
                //NC-22 @Amount.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Amount", SqlDbType.Int));  
                cmdNewOrder.Parameters["@Amount"].Value = numOrderAmount.Value;  
  
                //NC-23 @Status. For a new order, the status is always O (open).  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Status", SqlDbType.Char, 1));  
                cmdNewOrder.Parameters["@Status"].Value = "O";  
  
                //NC-24 Add return value for stored procedure, which is orderID.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@RC", SqlDbType.Int));  
                cmdNewOrder.Parameters["@RC"].Direction = ParameterDirection.ReturnValue;  
  
                //try-catch-finally  
                try  
                {  
                    //Open connection.  
                    conn.Open();  
  
                    //Run the stored procedure.  
                    cmdNewOrder.ExecuteNonQuery();  
  
                    //NC-25 Display the order number.  
                    this.orderID = (int)cmdNewOrder.Parameters["@RC"].Value;  
                    MessageBox.Show("Order number " + this.orderID + " has been submitted.");  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("Order could not be placed.");  
                }  
                finally  
                {  
                    //Close connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //NC-26 Verify that order data is ready.  
        private bool isPlaceOrderReady()  
        {  
            // Verify that CustomerID is present.  
            if (txtCustomerID.Text == "")  
            {  
                MessageBox.Show("Please create customer account before placing order.");  
                return false;  
            }  
  
            // Verify that Amount isn't 0.   
            else if ((numOrderAmount.Value < 1))  
            {  
                MessageBox.Show("Please specify an order amount.");  
                return false;  
            }  
            else  
            {  
                // Order can be submitted.  
                return true;  
            }  
        }  
  
        //NC-27 Reset the form for another new account.  
        private void btnAddAnotherAccount_Click(object sender, EventArgs e)  
        {  
            this.ClearForm();  
        }  
  
        //NC-28 Clear values from controls.  
        private void ClearForm()  
        {  
            txtCustomerName.Clear();  
            txtCustomerID.Clear();  
            dtpOrderDate.Value = DateTime.Now;  
            numOrderAmount.Value = 0;  
            this.parsedCustomerID = 0;  
        }  
  
        //NC-29 Close the form.  
        private void btnAddFinish_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
  
    }  
}  
  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
' NC-1 More namespaces.  
Imports System.Data.SqlClient  
Imports System.Configuration  
  
Namespace SimpleDataApp  
    Partial Public Class NewCustomer  
        Inherits Form  
  
        ' NC-2 Storage for IDENTITY values returned from database.  
        Private parsedCustomerID As Integer  
        Private orderID As Integer  
  
        ' NC-3 Specify a connection string.  
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' NC-4 Create account.  
        Private Sub btnCreateAccount_Click() Handles btnCreateAccount.Click  
  
            ' NC-5 Set up and run stored procedure only if Customer Name is present.  
            If isCustomerName() Then  
  
                ' NC-6 Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' NC-7 Create a SqlCommand, and identify it as a stored procedure.  
                Dim cmdNewCustomer As New SqlCommand("Sales.uspNewCustomer", conn)  
                cmdNewCustomer.CommandType = CommandType.StoredProcedure  
  
                ' NC-8 Add input parameter from the stored procedure and specify what to use as its value.  
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerName", SqlDbType.NVarChar, 40))  
                cmdNewCustomer.Parameters("@CustomerName").Value = txtCustomerName.Text  
  
                ' NC-9 Add output parameter.  
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))  
                cmdNewCustomer.Parameters("@CustomerID").Direction = ParameterDirection.Output  
  
                ' NC-10 try-catch-finally  
                Try  
                    ' NC-11 Open the connection.  
                    conn.Open()  
  
                    ' NC-12 Run the stored procedure.  
                    cmdNewCustomer.ExecuteNonQuery()  
  
                    ' NC-13 Customer ID is an IDENTITY value from the database.   
                    Me.parsedCustomerID = CInt(cmdNewCustomer.Parameters("@CustomerID").Value)  
                    Me.txtCustomerID.Text = Convert.ToString(parsedCustomerID)  
  
                Catch  
                    ' NC-14 A simple catch.  
                    MessageBox.Show("Customer ID was not returned. Account could not be created.")  
                Finally  
                    ' NC-15 Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' NC-16 Verify that Customer Name is present.  
        Private Function isCustomerName() As Boolean  
            If txtCustomerName.Text = "" Then  
                MessageBox.Show("Please enter a name.")  
                Return False  
            Else  
                Return True  
            End If  
        End Function  
  
        ' NC-17 Place order.  
        Private Sub btnPlaceOrder_Click() Handles btnPlaceOrder.Click  
  
            ' NC-18 Set up and run stored procedure only if necessary input is present.  
            If isPlaceOrderReady() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' NC-19 Create SqlCommand and identify it as a stored procedure.  
                Dim cmdNewOrder As New SqlCommand("Sales.uspPlaceNewOrder", conn)  
                cmdNewOrder.CommandType = CommandType.StoredProcedure  
  
                ' NC-20 @CustomerID, which was an output parameter from uspNewCustomer.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))  
                cmdNewOrder.Parameters("@CustomerID").Value = Me.parsedCustomerID  
  
                ' NC-21 @OrderDate.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@OrderDate", SqlDbType.DateTime, 8))  
                cmdNewOrder.Parameters("@OrderDate").Value = dtpOrderDate.Value  
  
                ' NC-22 @Amount.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@Amount", SqlDbType.Int))  
                cmdNewOrder.Parameters("@Amount").Value = numOrderAmount.Value  
  
                ' NC-23 @Status. For a new order, the status is always O (open).  
                cmdNewOrder.Parameters.Add(New SqlParameter("@Status", SqlDbType.[Char], 1))  
                cmdNewOrder.Parameters("@Status").Value = "O"  
  
                ' NC-24 Add return value for stored procedure, which is orderID.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@RC", SqlDbType.Int))  
                cmdNewOrder.Parameters("@RC").Direction = ParameterDirection.ReturnValue  
  
                ' try-catch-finally  
                Try  
                    ' Open connection.  
                    conn.Open()  
  
                    ' Run the stored procedure.  
                    cmdNewOrder.ExecuteNonQuery()  
  
                    ' NC-25 Display the order number.  
                    Me.orderID = CInt(cmdNewOrder.Parameters("@RC").Value)  
                    MessageBox.Show("Order number " & (Me.orderID).ToString & " has been submitted.")  
  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("Order could  not be placed.")  
  
                Finally  
                    ' Close connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' NC-26 Verify that order data is ready.  
        Private Function isPlaceOrderReady() As Boolean  
  
            ' Verify that CustomerID is present.  
            If txtCustomerID.Text = "" Then  
                MessageBox.Show("Please create customer account before placing order.")  
                Return False  
  
                ' Verify that Amount isn't 0.   
            ElseIf (numOrderAmount.Value < 1) Then  
  
                MessageBox.Show("Please specify an order amount.")  
                Return False  
            Else  
                ' Order can be submitted.  
                Return True  
            End If  
        End Function  
  
        ' NC-27 Reset the form for another new account.  
        Private Sub btnAddAnotherAccount_Click() Handles btnAddAnotherAccount.Click  
            Me.ClearForm()  
        End Sub  
  
        ' NC-28 Clear values from controls.  
        Private Sub ClearForm()  
            txtCustomerName.Clear()  
            txtCustomerID.Clear()  
            dtpOrderDate.Value = DateTime.Now  
            numOrderAmount.Value = 0  
            Me.parsedCustomerID = 0  
        End Sub  
  
        ' NC-29 Close the form.  
        Private Sub btnAddFinish_Click() Handles btnAddFinish.Click  
            Me.Close()  
        End Sub  
  
    End Class  
End Namespace  
```  
  
|註解|描述|  
|-------------|-----------------|  
|NC-1|新增`System.Data.SqlClient`和`System.Configuration`命名空間的清單。|  
|NC-2|宣告您稍後將會使用的 `parsedCustomerID` 和 `orderID` 變數。|  
|NC-3|呼叫 `GetConnectionString` 方法從應用程式組態檔中取得連接字串，並且在 `connstr` 字串變數中儲存值。|  
|NC-4|為 `btnCreateAccount` 按鈕將程式碼加入至 Click 事件處理常式。|  
|NC-5|將呼叫包裝至 Click 事件處理常式周圍的 `isCustomerName`，讓 `uspNewCustomer` 只有在客戶名稱存在時執行。|  
|NC-6|建立 `SqlConnection` 物件 (`conn`)，並且在 `connstr` 中傳入連接字串。|  
|NC-7|建立 `SqlCommand` 物件 `cmdNewCustomer`。<br /><br /> -指定`Sales.uspNewCustomer`預存程序執行。<br />-使用`CommandType`屬性，以指定的命令是預存程序。|  
|NC-8|從預存程序加入 `@CustomerName` 輸入參數。<br /><br /> -將參數新增至`Parameters`集合。<br />-使用`SqlDbType`nvarchar(40) 為指定的參數類型的列舉。<br />-指定`txtCustomerName.Text`做為來源。|  
|NC-9|從預存程序加入輸出參數。<br /><br /> -將參數新增至`Parameters`集合。<br />-使用`ParameterDirection.Output`來識別做為輸出參數。|  
|NC-10|新增 Catch 的 Try-finally 區塊來開啟連線、 執行預存程序、 處理例外狀況，並再關閉連線。|  
|NC-11|開啟您在 NC-6 建立的連接 (`conn`)。|  
|NC-12|使用`ExecuteNonQuery`方法`cmdNewCustomer`執行`Sales.uspNewCustomer`預存程序。 這個預存程序執行`INSERT`陳述式中，不是查詢。|  
|NC-13|會從資料庫傳回 `@CustomerID` 值做為 IDENTITY 值。 因為它是一個整數，您必須將它轉換成字串，它顯示在**客戶識別碼**文字方塊。<br /><br /> -您宣告`parsedCustomerID`在 nc-2。<br />-儲存`@CustomerID`中的值`parsedCustomerID`供稍後使用。<br />-將傳回的客戶 ID 轉換為字串，並將它插入`txtCustomerID.Text`。|  
|NC-14|此範例中，加入簡單 （不實際執行品質） catch 子句。|  
|NC-15|使用完畢之後一律關閉連接，讓它可以釋放至連接集區。 請參閱[SQL Server 連接共用 (ADO.NET)](http://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx)。|  
|NC-16|定義方法以驗證客戶名稱會顯示出來。<br /><br /> -如果文字方塊是空的顯示一則訊息，並傳回`false`，因為若要建立的帳戶必須有名稱。<br />-如果文字方塊不是空的則傳回`true`。|  
|NC-17|為 `btnPlaceOrder` 按鈕將程式碼加入至 Click 事件處理常式。|  
|NC-18|將呼叫包裝至 `btnPlaceOrder_Click` 事件程式碼周圍的 `isPlaceOrderReady`，讓 `uspPlaceNewOrder` 在必要的輸入未顯示時不執行。|  
|NC-19 到 NC-25|這些程式碼區段類似於您為 `btnCreateAccount_Click` 事件處理常式加入的程式碼。<br /><br /> -   NC-19. 建立 `SqlCommand` 物件 `cmdNewOrder`，並且指定 `Sales.uspPlaceOrder` 為預存程序。<br />-Nc-20 到 nc-23 是預存程序的輸入的參數。<br />-   NC-24. `@RC` 將包含傳回值，這是從資料庫產生的順序 ID。 此參數的說明指定為 `ReturnValue`。<br />-   NC-25. 在您於 NC-2 宣告的 `orderID` 變數中儲存順序 ID 值，並且在訊息方塊中顯示值。|  
|NC-26|定義方法以驗證客戶 ID 存在，而且已在 `numOrderAmount` 中指定數量。|  
|NC-27|在 `btnAddAnotherAccount` Click 事件處理常式中呼叫 `ClearForm` 方法。|  
|NC-28|建立 `ClearForm` 方法，當您要加入其他客戶時，清除表單中的值。|  
|NC29|關閉 NewCustomer 表單，並將焦點返回到瀏覽表單。|  
  
### <a name="fillorcancel-form"></a>FillOrCancel 表單  
 FillorCancel 表單會執行查詢來傳回訂單，當您輸入訂單 ID，並選取**尋找訂單** 按鈕。 傳回的資料列會顯示在唯讀的資料格。 如果您選取，您可以將標記為已取消 (X) 的順序**取消訂單** 按鈕，或者您可以將訂單標示為已填寫 (F) 如果您選取**填寫訂單** 按鈕。 如果您選取**尋找訂單**同樣地，按鈕會顯示更新的資料列。  
  
#### <a name="create-event-handlers"></a>建立事件處理常式  
 為表單上的四個按鈕建立空白 Click 事件處理常式。  
  
#### <a name="create-code-for-fillorcancel"></a>建立 FillOrCancel 的程式碼  
 將下列程式碼加入至 FillOrCancel 表單。 使用程式碼之後已編號的註解和資料表，以逐步執行程式碼區塊。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
//FC-1 More namespaces.  
using System.Text.RegularExpressions;  
using System.Data.SqlClient;  
using System.Configuration;  
  
namespace SimpleDataApp  
{  
    public partial class FillOrCancel : Form  
    {  
        //FC-2 Storage for OrderID.  
        private int parsedOrderID;  
  
        //FC-3 Specify a connection string.  
        string connstr = SimpleDataApp.Utility.GetConnectionString();  
  
        public FillOrCancel()  
        {  
            InitializeComponent();  
        }  
  
        //FC-4 Find an order.  
        private void btnFindByOrderID_Click(object sender, EventArgs e)  
        {  
            //FC-5 Prepare the connection and the command.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //Define a query string that has a parameter for orderID.  
                string sql = "select * from Sales.Orders where orderID = @orderID";  
  
                //Create a SqlCommand object.  
                SqlCommand cmdOrderID = new SqlCommand(sql, conn);  
  
                //Define the @orderID parameter and its value.  
                cmdOrderID.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdOrderID.Parameters["@orderID"].Value = parsedOrderID;  
  
                //try-catch-finally  
                try  
                {  
                    //FC-6 Run the command and display the results.  
                    //Open the connection.  
                    conn.Open();  
  
                    //Run the command by using SqlDataReader.  
                    SqlDataReader rdr = cmdOrderID.ExecuteReader();  
  
                    //Create a data table to hold the retrieved data.  
                    DataTable dataTable = new DataTable();  
  
                    //Load the data from SqlDataReader into the data table.  
                    dataTable.Load(rdr);  
  
                    //Display the data from the data table in the data grid view.  
                    this.dgvCustomerOrders.DataSource = dataTable;  
  
                    //Close the SqlDataReader.  
                    rdr.Close();  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("The requested order could not be loaded into the form.");  
                }  
                finally  
                {  
                    //Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-7 Cancel an order.  
        private void btnCancelOrder_Click(object sender, EventArgs e)  
        {  
            //Set up and run stored procedure only if OrderID is ready.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                // Create command and identify it as a stored procedure.  
                SqlCommand cmdCancelOrder = new SqlCommand("Sales.uspCancelOrder", conn);  
                cmdCancelOrder.CommandType = CommandType.StoredProcedure;  
  
                cmdCancelOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdCancelOrder.Parameters["@orderID"].Value = parsedOrderID;  
  
                // try-catch-finally  
                try  
                {  
                    // Open the connection.  
                    conn.Open();  
  
                    // Run the cmdCancelOrder command.  
                    cmdCancelOrder.ExecuteNonQuery();  
                }  
                // A simple catch.  
                catch  
                {  
                    MessageBox.Show("The cancel operation was not completed.");  
                }  
                finally  
                {  
                    //Close connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-8 Fill an order.  
        private void btnFillOrder_Click(object sender, EventArgs e)  
        {  
            //Set up and run stored procedure only if OrderID is ready.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //Create command and identify it as a stored procedure.  
                SqlCommand cmdFillOrder = new SqlCommand("Sales.uspFillOrder", conn);  
                cmdFillOrder.CommandType = CommandType.StoredProcedure;  
  
                // Add input parameter from the stored procedure.  
                cmdFillOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdFillOrder.Parameters["@orderID"].Value = parsedOrderID;  
  
                //Add the second input parameter.  
                cmdFillOrder.Parameters.Add(new SqlParameter("@FilledDate", SqlDbType.DateTime, 8));  
                cmdFillOrder.Parameters["@FilledDate"].Value = dtpFillDate.Value;  
  
                //try-catch-finally  
                try  
                {  
                    //Open the connection.  
                    conn.Open();  
  
                    //Run the cmdFillOrder command.  
                    cmdFillOrder.ExecuteNonQuery();  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("The fill operation was not completed.");  
                }  
                finally  
                {  
                    //Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-9 Verify that OrderID is ready.  
        private bool isOrderID()  
        {  
  
            //Check for input in the Order ID text box.  
            if (txtOrderID.Text == "")  
            {  
                MessageBox.Show("Please specify the Order ID.");  
                return false;  
            }  
  
            // Check for characters other than integers.  
            else if (Regex.IsMatch(txtOrderID.Text, @"^\D*$"))  
            {  
               //Show message and clear input.  
                MessageBox.Show("Please specify integers only.");  
                txtOrderID.Clear();  
                return false;  
            }  
            else  
            {  
                //Convert the text in the text box to an integer to send to the database.  
                parsedOrderID = Int32.Parse(txtOrderID.Text);  
                return true;  
            }  
        }  
  
        //Close the form.  
        private void btnFinishUpdates_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
' FC-1 More namespaces.  
Imports System.Text.RegularExpressions  
Imports System.Data.SqlClient  
Imports System.Configuration  
  
Namespace SimpleDataApp  
    Partial Public Class FillOrCancel  
        Inherits Form  
        ' FC-2 Storage for OrderID.  
        Private parsedOrderID As Integer  
  
        ' FC-3 Specify a connection string.  
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' FC-4 Find an order.  
        Private Sub btnFindByOrderID_Click() Handles btnFindByOrderID.Click  
  
            ' FC-5 Prepare the connection and the command.  
  
            If isOrderID() Then  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Define the query string that has a parameter for orderID.  
                Dim sql As String = "select * from Sales.Orders where orderID = @orderID"  
  
                ' Create a SqlCommand object.  
                Dim cmdOrderID As New SqlCommand(sql, conn)  
  
                ' Define the @orderID parameter and its value.  
                cmdOrderID.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdOrderID.Parameters("@orderID").Value = parsedOrderID  
  
                ' try-catch-finally  
                Try  
                    ' FC-6 Run the command and display the results.  
                    ' Open connection.  
                    conn.Open()  
  
                    ' Run the command by using SqlDataReader.  
                    Dim rdr As SqlDataReader = cmdOrderID.ExecuteReader()  
  
                    ' Create a data table to hold the retrieved data.  
                    Dim dataTable As New DataTable()  
  
                    ' Load the data from SqlDataReader into the data table.  
                    dataTable.Load(rdr)  
  
                    ' Display the data from the data table in the data grid view.  
                    Me.dgvCustomerOrders.DataSource = dataTable  
  
                    ' Close the SqlDataReader.  
                    rdr.Close()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The requested order could not be loaded into the form.")  
                Finally  
                    ' Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-7 Cancel an order.  
        Private Sub btnCancelOrder_Click() Handles btnCancelOrder.Click  
  
            ' Set up and run stored procedure only if OrderID is ready.  
            If isOrderID() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Create the command and identify it as a stored procedure.  
                Dim cmdCancelOrder As New SqlCommand("Sales.uspCancelOrder", conn)  
                cmdCancelOrder.CommandType = CommandType.StoredProcedure  
  
                ' Add input parameter from the stored procedure.  
                cmdCancelOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdCancelOrder.Parameters("@orderID").Value = parsedOrderID  
  
                ' try-catch-finally  
                Try  
                    ' Open the connection.  
                    conn.Open()  
  
                    ' Run the cmdCancelOrder command.  
                    cmdCancelOrder.ExecuteNonQuery()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The cancel operation was not completed.")  
                Finally  
                    ' Close connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-8 Fill an order.  
        Private Sub btnFillOrder_Click() Handles btnFillOrder.Click  
  
            ' Set up and run stored procedure only if OrderID is ready.  
            If isOrderID() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Create command and identify it as a stored procedure.  
                Dim cmdFillOrder As New SqlCommand("Sales.uspFillOrder", conn)  
                cmdFillOrder.CommandType = CommandType.StoredProcedure  
  
                ' Add input parameter from the stored procedure.  
                cmdFillOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdFillOrder.Parameters("@orderID").Value = parsedOrderID  
  
                ' Add second input parameter.  
                cmdFillOrder.Parameters.Add(New SqlParameter("@FilledDate", SqlDbType.DateTime, 8))  
                cmdFillOrder.Parameters("@FilledDate").Value = dtpFillDate.Value  
  
                ' try-catch-finally  
                Try  
                    ' Open the connection.  
                    conn.Open()  
  
                    ' Run the cmdFillOrder command.   
                    cmdFillOrder.ExecuteNonQuery()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The fill operation was not completed.")  
                Finally  
                    ' Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-9 Verify that OrderID is ready.  
        Private Function isOrderID() As Boolean  
  
            ' Check for input in the Order ID text box.  
            If txtOrderID.Text = "" Then  
                MessageBox.Show("Please specify the Order ID.")  
                Return False  
  
                ' Check for characters other than integers.  
            ElseIf Regex.IsMatch(txtOrderID.Text, "^\D*$") Then  
  
                ' Show message and clear input.  
                MessageBox.Show("Please specify integers only.")  
                txtOrderID.Clear()  
                Return False  
  
            Else  
                ' Convert the text in the text box to an integer to send to the database.  
                parsedOrderID = Int32.Parse(txtOrderID.Text)  
                Return True  
  
            End If  
        End Function  
  
        ' Close the form.  
        Private Sub btnFinishUpdates_Click() Handles btnFinishUpdates.Click  
            Me.Close()  
        End Sub  
    End Class  
End Namespace  
```  
  
|註解|描述|  
|-------------|-----------------|  
|FC-1|新增`System.Data.SqlClient`， `System.Configuration`，和`System.Text.RegularExpressions`命名空間的清單。|  
|FC-2|宣告 `parsedOrderID` 變數。|  
|FC-3|呼叫 `GetConnectionString` 方法從應用程式組態檔中取得連接字串，並且在 `connstr` 字串變數中儲存值。|  
|FC-4|為 `btnFindOrderByID` 將程式碼加入至 Click 事件處理常式。|  
|FC-5|您嘗試執行 SQL 陳述式或預存程序之前，需要執行這些工作。<br /><br /> -建立`SqlConnection`物件。<br />定義 SQL 陳述式，或指定的預存程序名稱。 (在這個範例中，您將會執行 `SELECT` 陳述式。)<br />-建立`SqlCommand`物件。<br />定義 SQL 陳述式或預存程序的任何參數。|  
|FC-6|此程式碼使用 `SqlDataReader` 和 `DataTable` 以擷取及顯示查詢結果。<br /><br /> -開啟連接。<br />-建立`SqlDataReader`物件， `rdr`，藉由執行`ExecuteReader`方法`cmdOrderID`。<br />-建立`DataTable`物件來保存擷取的資料。<br />-從資料載入`SqlDataReader`物件插入`DataTable`物件。<br />-顯示資料的資料格檢視中藉由指定`DataTable`做為`DataSource`資料方格檢視。<br />-關閉`SqlDataReader`。|  
|FC-7|為 `btnCancelOrder` 將程式碼加入至 Click 事件處理常式。 此程式碼會執行 `Sales.uspCancelOrder` 預存程序。|  
|FC-8|為 `btnFillOrder` 將程式碼加入至 Click 事件處理常式。 此程式碼會執行 `Sales.uspFillOrder` 預存程序。|  
|FC-9|建立方法，以確認`OrderID`已準備好做為參數來提交`SqlCommand`物件。<br /><br /> -請確定已在中輸入 ID `txtOrderID`。<br />-使用`Regex.IsMatch`來定義非整數字元的簡單檢查。<br />-您宣告`parsedOrderID`在 fc-2 變數。<br />-如果輸入是有效的將文字轉換成整數，並將值儲存在`parsedOrderID`變數。<br />-包裝`isOrderID`方法周圍`btnFindByOrderID`， `btnCancelOrder`，和`btnFillOrder`Click 事件處理常式。|  
  
##  <a name="BKMK_testyourapplication"></a> 測試您的應用程式  
 選擇 F5 鍵以建置和測試您的應用程式之後您程式碼的每個 Click 事件處理常式，, 然後之後完成撰寫程式碼。
