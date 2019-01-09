---
title: 資料繫結-Windows Form 控制項中使用查閱資料表 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: bcdfb4640e88289b02f2f8813c39b66eaad3827d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889419"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>建立支援查閱資料繫結的 Windows Forms 使用者控制項

在 Windows Forms 上顯示資料時，您可以從 [工具箱] 中選擇現有控制項；或者，如果應用程式需要標準控制項中未提供的功能，您也可以撰寫自訂控制項。 這個逐步解說顯示如何建立可實作 <xref:System.ComponentModel.LookupBindingPropertiesAttribute> 的控制項。 可實作 <xref:System.ComponentModel.LookupBindingPropertiesAttribute> 的控制項可以包含三個可繫結至資料的屬性。 這類控制項類似 <xref:System.Windows.Forms.ComboBox>。

如需控制項製作的詳細資訊，請參閱[開發 Windows Form 控制項在設計階段](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)。

製作控制項以用於資料繫結情節時，您需要實作下列其中一個資料繫結屬性：

|資料繫結屬性使用方式|
| - |
|對顯示資料之單一資料行 (或屬性) 的簡單控制項 (如 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>)，實作 <xref:System.Windows.Forms.TextBox> 如需詳細資訊，請參閱 <<c0> [ 建立支援簡單資料繫結 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)。|
|對顯示資料之清單 (或資料表) 的控制項 (如 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>)，實作 <xref:System.Windows.Forms.DataGridView> 如需詳細資訊，請參閱 <<c0> [ 建立支援複雜資料繫結 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)。|
|對顯示資料之清單 (或資料表) 但也需要呈現單一資料行或屬性的控制項 (如 <xref:System.ComponentModel.LookupBindingPropertiesAttribute>)，實作 <xref:System.Windows.Forms.ComboBox>。 (這個逐步解說頁面會描述此流程)。|

這個逐步解說會建立繫結至兩張資料表中資料的查閱控制項。 此範例使用 Northwind 範例資料庫中的 `Customers` 和 `Orders` 資料表。 查閱控制項所繫結`CustomerID`欄位從`Orders`資料表。 它會使用此值來查閱`CompanyName`從`Customers`資料表。

在這個逐步解說中，您將了解如何：

-   建立新的 **Windows Forms 應用程式**。

-   將新 [使用者控制項] 新增至您的專案。

-   透過視覺化方式設計使用者控制項。

-   實作 `LookupBindingProperty` 屬性。

-   建立與資料集**資料來源組態**精靈。

-   在 [資料來源] 視窗的 [訂單] 資料表上設定 [CustomerID] 資料行，以使用新的控制項。

-   建立表單以顯示新控制項中的資料。

## <a name="prerequisites"></a>必要條件

本逐步解說會使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1.  如果您沒有 SQL Server Express LocalDB，請將它安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)，或透過**Visual Studio 安裝程式**。 在  **Visual Studio 安裝程式**，您可以安裝 SQL Server Express LocalDB 做為一部分**資料儲存和處理**工作負載，或作為個別的元件。

2.  安裝 Northwind 範例資料庫執行下列步驟：

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (SQL Server 物件總管 中已安裝的一部分**資料儲存和處理**Visual Studio 安裝程式中的工作負載。)依序展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢**。

       查詢編輯器視窗隨即開啟。

    2. 複製[Northwind 的 TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。

    3. 將 T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。

       短時間之後，查詢完成執行，並建立 Northwind 資料庫。

## <a name="create-a-windows-forms-app-project"></a>建立 Windows Forms 應用程式專案

第一個步驟是建立**Windows Forms 應用程式**專案。

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增** > **專案**。

2. 展開  **Visual C#** 或是**Visual Basic**左窗格中，然後選取**Windows Desktop**。

3. 在中間窗格中，選取**Windows Forms 應用程式**專案類型。

4. 將專案命名為**LookupControlWalkthrough**，然後選擇**確定**。

     隨即建立 **LookupControlWalkthrough** 專案，並將其新增至 [方案總管]。

## <a name="add-a-user-control-to-the-project"></a>將使用者控制項新增至專案

此逐步解說會從 [使用者控制項] 建立查閱控制項，進而將 [使用者控制項] 項目新增至 **LookupControlWalkthrough** 專案。

1.  從 [專案] 功能表選取 [新增使用者控制項]。

2.  型別`LookupBox`中**名稱**區域，，然後按一下**新增**。

     [LookupBox] 控制項會新增至 [方案總管]，並在設計工具中開啟。

## <a name="design-the-lookupbox-control"></a>設計 LookupBox 控制項

若要設計 LookupBox 控制項，拖曳<xref:System.Windows.Forms.ComboBox>從**工具箱**拖曳至使用者控制項的設計介面。

## <a name="add-the-required-data-binding-attribute"></a>新增必要的資料繫結屬性

針對支援資料繫結的查閱控制項，您可以實作 <xref:System.ComponentModel.LookupBindingPropertiesAttribute>。

1.  將 [LookupBox] 控制項切換至程式碼檢視。 (在 [檢視] 功能表上，選擇 [程式碼]。)

2.  將 `LookupBox` 中的程式碼取代為下列內容：

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3.  從 [ **建置** ] 功能表中，選擇 [ **建置方案**]。

## <a name="create-a-data-source-from-your-database"></a>從您的資料庫建立資料來源

此步驟使用 [資料來源組態精靈]，根據 Northwind 範例資料庫中的 `Customers` 和 `Orders` 資料表建立資料來源。

1.  若要開啟 **資料來源** 視窗，請在**資料**功能表上，按一下 **顯示資料來源**。

2.  在 [資料來源] 視窗中，選取 [新增新資料來源]，以啟動 [資料來源組態精靈]。

3.  請選取 [ **選擇資料來源類型** ] 頁面上的 [ **資料庫** ]，再按 [ **下一步**]。

4.  在 [選擇您的資料連線] 頁面上，執行下列其中一項：

    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。

    -   選取 [新增連線] 啟動 [新增/修改連線] 對話方塊。

5.  如果資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下 [下一步]。

6.  在 [**將連接字串儲存到應用程式組態檔**頁面上，按一下**下一步]**。

7.  展開 [選擇您的資料庫物件] 頁面上的 [資料表] 節點。

8.  選取 `Customers` 和 `Orders` 資料表，然後按一下 [完成]。

     **NorthwindDataSet** 會新增至您的專案，且 `Customers` 和 `Orders` 資料表會出現在 [資料來源] 視窗中。

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>設定要使用 LookupBox 控制項的 「 訂單 」 資料表的 CustomerID 資料行

在 [資料來源] 視窗中，您可以設定在將項目拖曳至表單之前建立控制項。

1.  在設計工具中，開啟 **Form1**。

2.  在 [資料來源] 視窗中，展開 [客戶] 節點。

3.  展開 [訂單] 節點 (位於 [客戶] 節點的 [傳真] 資料行下方)。

4.  按一下 [訂單] 節點上的下拉式箭頭，並從控制項清單中選擇 [詳細資料]。

5.  按一下 [CustomerID] 資料行 (位於 [訂單] 節點中) 上的下拉式箭頭，並選擇 [自訂]。

6.  在 [資料 UI 自訂選項] 對話方塊中，從 [相關聯的控制項] 清單中選取 **LookupBox**。

7.  按一下 [確定 **Deploying Office Solutions**]。

8.  按一下 [CustomerID] 資料行上的下拉式箭頭，並選擇 **LookupBox**。

## <a name="add-controls-to-the-form"></a>將控制項加入表單

將項目從 [資料來源] 視窗拖曳至 **Form1**，以建立資料繫結控制項。

若要建立 Windows 表單上的資料繫結控制項，拖曳**訂單**從節點**資料來源**視窗拖曳至 Windows Form 中，並確認**LookupBox**控制項用來顯示資料的`CustomerID`資料行。

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>繫結控制項以查閱 Customers 資料表中的公司名稱

若要設定查閱繫結，請選取 主**客戶**中的節點**Zdroje dat**視窗中，然後拖曳到下拉式方塊中**CustomerIDLookupBox**上**Form1**。

這會設定資料繫結以顯示 `Customers` 資料表中的 `CompanyName`，同時維護 `Orders` 資料表中的 `CustomerID` 值。

## <a name="run-the-application"></a>執行應用程式

-   按 **F5** 執行應用程式。

-   巡覽部分記錄，並確認 `CompanyName` 出現在 `LookupBox` 控制項中。

## <a name="see-also"></a>另請參閱

- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)