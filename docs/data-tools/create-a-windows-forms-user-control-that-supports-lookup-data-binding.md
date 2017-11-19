---
title: "資料繫結的 Windows Form 控制項中使用查閱資料表 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f4eed84197589229940d0e18e261156128f37c63
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>建立支援查閱資料繫結的 Windows Form 使用者控制項
當 Windows Form 上顯示資料，您可以選擇從現有的控制項**工具箱**，或如果您的應用程式需要標準控制項中無法使用的功能，您可以編寫自訂控制項。 這個逐步解說顯示如何建立可實作 <xref:System.ComponentModel.LookupBindingPropertiesAttribute> 的控制項。 可實作 <xref:System.ComponentModel.LookupBindingPropertiesAttribute> 的控制項可以包含三個可繫結至資料的屬性。 這類控制項類似 <xref:System.Windows.Forms.ComboBox>。  
  
 如需有關撰寫控制項的詳細資訊，請參閱[在設計階段開發 Windows Form 控制項](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)。  
  
 製作控制項以用於資料繫結情節時您需要實作下列的資料繫結屬性的其中一個：  
  
|資料繫結屬性使用方式|  
|-----------------------------------|  
|對顯示資料之單一資料行 (或屬性) 的簡單控制項 (如 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>)，實作 <xref:System.Windows.Forms.TextBox>  如需詳細資訊，請參閱[建立支援簡單資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)。|  
|對顯示資料之清單 (或資料表) 的控制項 (如 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>)，實作 <xref:System.Windows.Forms.DataGridView>  如需詳細資訊，請參閱[建立支援複雜資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)。|  
|對顯示資料之清單 (或資料表) 但也需要呈現單一資料行或屬性的控制項 (如 <xref:System.ComponentModel.LookupBindingPropertiesAttribute>)，實作 <xref:System.Windows.Forms.ComboBox>。 (這個逐步解說頁面會描述此流程)。|  
  
 這個逐步解說會建立繫結至兩張資料表中資料的查閱控制項。 此範例使用 Northwind 範例資料庫中的 `Customers` 和 `Orders` 資料表。 查閱控制項將會繫結至 `CustomerID` 資料表中的 `Orders` 欄位。 它將會使用此值查閱 `CompanyName` 資料表中的 `Customers`。  
  
 在這個逐步解說期間，您將了解如何：  
  
-   建立新**Windows Forms 應用程式**。  
  
-   加入新**使用者控制項**至您的專案。  
  
-   透過視覺化方式設計使用者控制項。  
  
-   實作 `LookupBindingProperty` 屬性。  
  
-   建立資料集與**資料來源組態**精靈。  
  
-   設定**CustomerID**上的資料行**訂單**表格中，於**資料來源**視窗中，以使用新的控制項。  
  
-   建立表單以顯示新控制項中的資料。  
  
## <a name="prerequisites"></a>必要條件  
本逐步解說會使用 SQL Server Express LocalDB 與 Northwind 範例資料庫。  
  
1.  如果您沒有 SQL Server Express LocalDB，將其安裝從[SQL Server 版本的下載頁面](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)，或透過**Visual Studio 安裝程式**。 在 Visual Studio 安裝程式，可以安裝 SQL Server Express LocalDB 的一部份**資料儲存和處理**工作負載，或做為個別的元件。  
  
2.  安裝 Northwind 範例資料庫執行下列步驟：  

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (SQL Server 物件總管 中安裝的一部份**資料儲存和處理**在 Visual Studio 安裝程式工作負載。)展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢...**.  

       查詢編輯器視窗隨即開啟。  

    2. 複製[Northwind TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。  

    3. T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。  

       在一段時間之後, 查詢完成執行，並建立 Northwind 資料庫。  
  
## <a name="create-a-windows-forms-application"></a>建立 Windows Forms 應用程式  
 第一個步驟是建立**Windows Forms 應用程式**。  
  
#### <a name="to-create-the-new-windows-project"></a>建立新的 Windows 專案  
  
1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增**，**專案...**.  
  
2. 展開  **Visual C#**或**Visual Basic**左窗格中，然後選取**的傳統 Windows 桌面**。  

3. 在中間窗格中，選取**Windows Form 應用程式**專案類型。  

4. 將專案命名**LookupControlWalkthrough**，然後選擇 **確定**。 
  
     **LookupControlWalkthrough**專案時建立，並加入至**方案總管 中**。  
  
## <a name="add-a-user-control-to-the-project"></a>將使用者控制項加入專案  
 這個逐步解說中建立查閱控制項從**使用者控制項**，因此加入**使用者控制項**項目**LookupControlWalkthrough**專案。  
  
#### <a name="to-add-a-user-control-to-the-project"></a>將使用者控制項加入至專案  
  
1.  從**專案**功能表上，選取**加入使用者控制項**。  
  
2.  型別`LookupBox`中**名稱**區域，，然後按一下**新增**。  
  
     **LookupBox**控制項加入至**方案總管 中**，並在設計工具中開啟。  
  
## <a name="design-the-lookupbox-control"></a>設計 LookupBox 控制項  
  
#### <a name="to-design-the-lookupbox-control"></a>設計 LookupBox 控制項  
  
-   拖曳<xref:System.Windows.Forms.ComboBox>從**工具箱**拖曳至使用者控制項的設計介面。  
  
## <a name="add-the-required-data-binding-attribute"></a>加入必要的資料繫結屬性  
 針對支援資料繫結的查閱控制項，您可以實作 <xref:System.ComponentModel.LookupBindingPropertiesAttribute>。  
  
#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>實作 LookupBindingProperties 屬性  
  
1.  交換器**LookupBox**程式碼 檢視的控制項。 (在**檢視**功能表上，選擇**程式碼**。)  
  
2.  將 `LookupBox` 中的程式碼取代為下列內容：  
  
     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]  
  
3.  從 [ **建置** ] 功能表中，選擇 [ **建置方案**]。  
  
## <a name="create-a-data-source-from-your-database"></a>從您的資料庫建立資料來源  
這個步驟會建立使用資料來源**資料來源組態**精靈，根據`Customers`和`Orders`Northwind 範例資料庫中的資料表。  
  
#### <a name="to-create-the-data-source"></a>若要建立資料來源  
  
1.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。  
  
2.  在**資料來源**視窗中，選取**加入新資料來源**啟動**資料來源組態**精靈。  
  
3.  請選取 [ **選擇資料來源類型** ] 頁面上的 [ **資料庫** ]，再按 [ **下一步**]。  
  
4.  在**選擇資料連線**頁面上，執行下列其中之一：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
    -   選取**新連線**啟動**新增/修改連接** 對話方塊。  
  
5.  如果您的資料庫需要密碼，選取選項來加入敏感性資料，然後按一下 **下一步**。  
  
6.  在**將連接字串儲存到應用程式組態檔**頁面上，按一下**下一步**。  
  
7.  在**選擇您的資料庫物件**頁面上，展開**資料表**節點。  
  
8.  選取`Customers`和`Orders`資料表，然後再按一下**完成**。  
  
     **NorthwindDataSet**加入至您的專案，而`Customers`和`Orders`資料表會出現在**資料來源**視窗。  
  
## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>設定要使用 LookupBox 控制項的 Orders 資料表的 CustomerID 資料行  
 內**資料來源**視窗中，您可以設定在將項目拖曳至表單之前建立控制項。  
  
#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>設定要繫結至 LookupBox 控制項的 CustomerID 資料行  
  
1.  開啟**Form1**設計工具中。  
  
2.  展開**客戶**節點**資料來源**視窗。  
  
3.  展開**訂單**節點 (中的一個**客戶**節點下面的**傳真**資料行)。  
  
4.  按一下下拉箭號**訂單**] 節點，然後選擇 [**詳細資料**的控制項清單中。  
  
5.  按一下下拉箭號**CustomerID**資料行 (在**訂單**節點)，然後選擇 **自訂**。  
  
6.  選取**LookupBox**從清單中**關聯的控制項**中**資料的 UI 自訂選項** 對話方塊。  
  
7.  按一下 [確定]。  
  
8.  按一下下拉箭號**CustomerID**資料行，然後選擇  **LookupBox**。  
  
## <a name="add-controls-to-the-form"></a>將控制項加入表單  
 您可以建立資料繫結控制項項目從**資料來源**視窗拖曳至**Form1**。  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>在 Windows Form 上建立資料繫結控制項  
  
-   拖曳**訂單**節點從**資料來源**視窗拖曳至 Windows Form 中，並確認**LookupBox**控制項用來顯示資料的`CustomerID`資料行。  
  
## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>繫結控制項以查閱 Customers 資料表中的 CompanyName  
  
#### <a name="to-setup-the-lookup-bindings"></a>設定查閱繫結  
  
-   選取主要**客戶**節點**資料來源**視窗中，然後拖曳到下拉式方塊中**CustomerIDLookupBox**上**Form1**.  
  
     這會設定資料繫結以顯示`CompanyName`從`Customers`資料表，同時維持`CustomerID`值`Orders`資料表。  
  
## <a name="running-the-application"></a>執行應用程式  
  
#### <a name="to-run-the-application"></a>若要執行應用程式  
  
-   按 F5 執行應用程式。  
  
-   瀏覽某些記錄，並確認`CompanyName`會出現在`LookupBox`控制項。  
  
## <a name="see-also"></a>另請參閱  
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
