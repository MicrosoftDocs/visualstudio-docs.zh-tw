---
title: 建立支援簡單資料繫結的使用者控制項
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7e2ad0047ef4ddc71b85f5fc04c865a9753b7c19
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756989"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>建立支援簡單資料繫結 Windows Forms 使用者控制項
在 Windows 應用程式的表單上顯示資料，您可以選擇從現有的控制項**工具箱**，或者如果您的應用程式需要標準控制項中沒有的功能，您可以編寫自訂控制項。 這個逐步解說顯示如何建立可實作 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> 的控制項。 可實作 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> 的控制項可以包含一個可繫結至資料的屬性。 這類控制項類似 <xref:System.Windows.Forms.TextBox> 或 <xref:System.Windows.Forms.CheckBox>。

 如需控制項製作的詳細資訊，請參閱[在設計階段開發 Windows Forms 控制項](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)。

 當製作控制項以用於資料繫結案例，您應該實作下列的資料繫結屬性的其中之一：

|資料繫結屬性使用方式|
|-----------------------------------|
|對顯示資料之單一資料行 (或屬性) 的簡單控制項 (如 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>)，實作 <xref:System.Windows.Forms.TextBox> (這個逐步解說頁面會描述此流程)。|
|對顯示資料之清單 (或資料表) 的控制項 (如 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>)，實作 <xref:System.Windows.Forms.DataGridView> 如需詳細資訊，請參閱 <<c0> [ 建立支援複雜資料繫結 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)。|
|對顯示資料之清單 (或資料表) 但也需要呈現單一資料行或屬性的控制項 (如 <xref:System.ComponentModel.LookupBindingPropertiesAttribute>)，實作 <xref:System.Windows.Forms.ComboBox>。 如需詳細資訊，請參閱 <<c0> [ 建立支援查閱資料繫結 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。|

 這個逐步解說會建立簡單控制項，以顯示來自資料表中單一資料行的資料。 此範例使用 Northwind 範例資料庫中 `Phone` 資料表的 `Customers` 資料行。 簡單使用者控制項顯示標準的電話號碼格式，客戶的電話號碼，使用<xref:System.Windows.Forms.MaskedTextBox>並將遮罩設定為電話號碼。

 在這個逐步解說期間，您將了解如何：

-   建立新**Windows Forms 應用程式**。

-   加入新**使用者控制項**至您的專案。

-   透過視覺化方式設計使用者控制項。

-   實作 `DefaultBindingProperty` 屬性。

-   建立與資料集**資料來源組態**精靈。

-   設定**電話**中的資料行**Zdroje dat**視窗，以使用新的控制項。

-   建立表單以顯示新控制項中的資料。

## <a name="prerequisites"></a>必要條件
本逐步解說會使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1.  如果您沒有 SQL Server Express LocalDB，請將它安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)，或透過**Visual Studio 安裝程式**。 在  **Visual Studio 安裝程式**，您可以安裝 SQL Server Express LocalDB 做為一部分**資料儲存和處理**工作負載，或作為個別的元件。

2.  安裝 Northwind 範例資料庫執行下列步驟：

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (SQL Server 物件總管 中已安裝的一部分**資料儲存和處理**中的工作負載**Visual Studio 安裝程式**。)依序展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢**。

       查詢編輯器視窗隨即開啟。

    2. 複製[Northwind 的 TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。

    3. 將 T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。

       短時間之後，查詢完成執行，並建立 Northwind 資料庫。

## <a name="create-a-windows-forms-application"></a>建立 Windows Forms 應用程式
 第一個步驟是建立**Windows Forms 應用程式**。

#### <a name="to-create-the-new-windows-project"></a>建立新的 Windows 專案

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增** > **專案**。

2. 展開  **Visual C#** 或是**Visual Basic**的左側窗格中，然後選取**Windows Desktop**。

3. 在中間窗格中，選取**Windows Forms 應用程式**專案類型。

4. 將專案命名為**SimpleControlWalkthrough**，然後選擇**確定**。

     **SimpleControlWalkthrough**專案時建立，並加入至**方案總管 中**。

## <a name="add-a-user-control-to-the-project"></a>將使用者控制項加入至專案
 此逐步解說會建立簡單資料繫結的控制項，從**使用者控制項**，因此加入**使用者控制**項目**SimpleControlWalkthrough**專案。

#### <a name="to-add-a-user-control-to-the-project"></a>將使用者控制項加入至專案

1.  從**專案**功能表上，選擇**加入使用者控制項**。

2.  型別`PhoneNumberBox`在 [名稱] 區域中，然後按一下**新增**。

     **PhoneNumberBox**控制項加入至**方案總管 中**，並在設計工具中開啟。

## <a name="design-the-phonenumberbox-control"></a>設計 PhoneNumberBox 控制項
 這個逐步解說會從現有 <xref:System.Windows.Forms.MaskedTextBox> 擴充，以建立 `PhoneNumberBox` 控制項。

#### <a name="to-design-the-phonenumberbox-control"></a>設計 PhoneNumberBox 控制項

1.  拖曳<xref:System.Windows.Forms.MaskedTextBox>從**工具箱**拖曳至使用者控制項的設計介面。

2.  在選取智慧標籤<xref:System.Windows.Forms.MaskedTextBox>剛剛拖曳出來，並選擇**設定遮罩**。

3.  選取 **電話號碼**中**輸入遮罩** 對話方塊中，然後按一下 **確定**設定遮罩。

## <a name="add-the-required-data-binding-attribute"></a>新增必要的資料繫結屬性
 針對支援資料繫結的簡單控制項，實作 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>。

#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>實作 DefaultBindingProperty 屬性

1.  將 `PhoneNumberBox` 控制項切換至程式碼檢視  (在**檢視**功能表上，選擇**程式碼**。)

2.  將 `PhoneNumberBox` 中的程式碼取代為下列內容：

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3.  從 [ **建置** ] 功能表中，選擇 [ **建置方案**]。

## <a name="create-a-data-source-from-your-database"></a>從您的資料庫建立資料來源
 此步驟中使用**資料來源組態**精靈來建立資料來源基礎`Customers`Northwind 範例資料庫中的資料表。 您必須具有 Northwind 範例資料庫的存取權，才能建立連接。 如需設定 Northwind 範例資料庫的詳細資訊，請參閱[如何： 安裝範例資料庫](../data-tools/installing-database-systems-tools-and-samples.md)。

#### <a name="to-create-the-data-source"></a>若要建立資料來源

1.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。

2.  在 **資料來源**視窗中，選取**加入新的資料來源**來啟動**資料來源組態**精靈。

3.  在 [**選擇資料來源類型**頁面上，選取**資料庫**，然後按一下**下一步]**。

4.  在 **選擇您的資料連接**頁面上，執行下列其中之一：

    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。

    -   選取 [**新的連線**來啟動**加入/修改連接**] 對話方塊。

5.  如果您的資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下**下一步**。

6.  在 [**將連接字串儲存到應用程式組態檔**頁面上，按一下**下一步]**。

7.  在 **選擇您的資料庫物件**頁面上，展開**資料表**節點。

8.  選取 `Customers`資料表，然後按一下**完成**。

     **NorthwindDataSet**新增至您的專案，而`Customers`資料表會出現在**Zdroje dat**視窗。

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>設定 phone 資料行使用 PhoneNumberBox 控制項
 內**Zdroje dat**  視窗中，您可以設定要在將項目拖曳至表單之前建立的控制項。

#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>設定要繫結至 PhoneNumberBox 控制項的 Phone 資料行

1.  開啟**Form1**設計工具中。

2.  依序展開**客戶**中的節點**Zdroje dat**視窗。

3.  按一下下拉箭號**客戶**節點，然後選擇**詳細資料**從控制項清單。

4.  按一下下拉箭號**電話**資料行，然後選擇**自訂**。

5.  選取 [ **PhoneNumberBox**從清單中的**關聯的控制項**中**資料的 UI 自訂選項**] 對話方塊。

6.  按一下下拉箭號**電話**資料行，然後選擇**PhoneNumberBox**。

## <a name="add-controls-to-the-form"></a>將控制項加入表單
 您可以建立資料繫結控制項項目從**Zdroje dat**視窗拖曳至表單。

#### <a name="to-create-data-bound-controls-on-the-form"></a>在表單上建立資料繫結控制項

-   主**客戶**從節點**Zdroje dat**視窗拖曳至表單，並確認`PhoneNumberBox`控制項用來顯示資料的`Phone`資料行。

     會在表單上顯示具有描述性標籤的資料繫結控制項，以及巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>)。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)，CustomersTableAdapter， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>會出現在元件匣。

## <a name="run-the-application"></a>執行應用程式

#### <a name="to-run-the-application"></a>若要執行應用程式

-   按 **F5** 執行應用程式。

## <a name="next-steps"></a>後續步驟
 根據應用程式的需求，在建立支援資料繫結程序的控制項之後，可能會有幾個想要執行的步驟。 一些一般後續步驟包括：

-   將自訂控制項放入控制項程式庫，讓您可以在其他應用程式中重複予以使用。

-   建立支援更複雜資料繫結情節的控制項。 如需詳細資訊，請參閱 <<c0> [ 建立支援複雜資料繫結 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)並[建立支援查閱資料繫結 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。

## <a name="see-also"></a>另請參閱

- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)