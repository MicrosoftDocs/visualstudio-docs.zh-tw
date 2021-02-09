---
title: 建立支援簡單資料系結的使用者控制項
description: 瞭解如何使用 Visual Studio 中的 DefaultBindingPropertyAttribute 類別，建立支援簡單資料系結的 Windows Forms 使用者控制項。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 30f6d338b4e27677c14dfa4e5ff8793e67f4c6ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867109"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>建立支援簡單資料繫結的 Windows Forms 使用者控制項

在 Windows 應用程式的表單上顯示資料時，您可以從 [工具箱] 中選擇現有控制項；或者，如果應用程式需要標準控制項中未提供的功能，您也可以撰寫自訂控制項。 這個逐步解說顯示如何建立可實作 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> 的控制項。 可實作 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> 的控制項可以包含一個可繫結至資料的屬性。 這類控制項類似 <xref:System.Windows.Forms.TextBox> 或 <xref:System.Windows.Forms.CheckBox>。

如需控制項撰寫的詳細資訊，請參閱 [在設計階段開發 Windows Forms 控制項](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)。

撰寫控制項以用於資料系結情節時，您應該執行下列其中一個資料系結屬性：

|資料系結屬性使用方式|
| - |
|對顯示資料之單一資料行 (或屬性) 的簡單控制項 (如 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>)，實作 <xref:System.Windows.Forms.TextBox> (這個逐步解說頁面會描述此流程)。|
|對顯示資料之清單 (或資料表) 的控制項 (如 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>)，實作 <xref:System.Windows.Forms.DataGridView> 如需詳細資訊，請參閱 [建立支援複雜資料系結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)。|
|對顯示資料之清單 (或資料表) 但也需要呈現單一資料行或屬性的控制項 (如 <xref:System.ComponentModel.LookupBindingPropertiesAttribute>)，實作 <xref:System.Windows.Forms.ComboBox>。 如需詳細資訊，請參閱 [建立支援查閱資料系結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。|

這個逐步解說會建立簡單控制項，以顯示來自資料表中單一資料行的資料。 此範例使用 Northwind 範例資料庫中 `Phone` 資料表的 `Customers` 資料行。 簡單的使用者控制項會使用， <xref:System.Windows.Forms.MaskedTextBox> 並將遮罩設定為電話號碼，以標準的電話號碼格式顯示客戶的電話號碼。

在這個逐步解說期間，您將了解如何：

- 建立新的 **Windows Forms 應用程式**。

- 將新 [使用者控制項] 新增至您的專案。

- 透過視覺化方式設計使用者控制項。

- 實作 `DefaultBindingProperty` 屬性。

- 使用 [ **資料來源** 設定] 建立資料集。

- 在 [資料來源] 視窗中設定 [電話] 資料行，以使用新的控制項。

- 建立表單以顯示新控制項中的資料。

## <a name="prerequisites"></a>必要條件

本逐步解說使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1. 如果您沒有 LocalDB SQL Server Express，請從 [SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)或透過 **Visual Studio 安裝程式** 進行安裝。 在 **Visual Studio 安裝程式** 中，您可以安裝 SQL Server Express LocalDB 作為 **資料儲存和處理** 工作負載的一部分，或安裝為個別的元件。

2. 遵循下列步驟來安裝 Northwind 範例資料庫：

    1. 在 Visual Studio 中，開啟 [ **SQL Server 物件總管** ] 視窗。  (SQL Server 物件總管會安裝為 **Visual Studio 安裝程式** 中 **資料儲存和處理** 工作負載的一部分。 ) 展開 **SQL Server** 節點。 以滑鼠右鍵按一下您的 LocalDB 實例，然後選取 [追加 **查詢**]。

       [查詢編輯器] 視窗隨即開啟。

    2. 將 [Northwind transact-sql 腳本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 複製到剪貼簿。 此 T-sql 腳本會從頭開始建立 Northwind 資料庫，並在其中填入資料。

    3. 將 T-sql 腳本貼入 [查詢編輯器]，然後選擇 [ **執行** ] 按鈕。

       經過一小段時間之後，查詢就會完成執行，並建立 Northwind 資料庫。

## <a name="create-a-windows-forms-application"></a>建立 Windows Forms 應用程式

第一個步驟是建立 **Windows Forms 應用程式**：

1. 在 Visual Studio 中，於 [檔案]  功能表上選取 [新增]   > [專案]  。

2. 展開左側窗格中的 [ **Visual c #** ] 或 [ **Visual Basic** ]，然後選取 [ **Windows 桌面**]。

3. 在中間窗格中，選取 [ **Windows Forms 應用程式** ] 專案類型。

4. 將專案命名為 **SimpleControlWalkthrough**，然後選擇 **[確定]**。

     隨即建立 **SimpleControlWalkthrough** 專案，並將其新增至 [方案總管]。

## <a name="add-a-user-control-to-the-project"></a>將使用者控制項新增至專案

本逐步解說會從 **使用者控制項** 建立簡單的資料繫結控制項。 將 [ **使用者控制項** ] 專案加入至 **SimpleControlWalkthrough** 專案：

1. 從 [專案] 功能表中，選擇 [新增使用者控制項]。

2. 在 [名稱] 區域中鍵入 **PhoneNumberBox**，然後按一下 [新增]。

     [PhoneNumberBox] 控制項會新增至 [方案總管]，並且可在設計工具中開啟。

## <a name="design-the-phonenumberbox-control"></a>設計 PhoneNumberBox 控制項

本逐步解說會根據現有的 <xref:System.Windows.Forms.MaskedTextBox> 建立 **PhoneNumberBox** 控制項來進行擴充：

1. 將 <xref:System.Windows.Forms.MaskedTextBox> 從 [工具箱] 拖曳至使用者控制項的設計介面。

2. 在 <xref:System.Windows.Forms.MaskedTextBox> 上選取您剛剛拖曳的智慧標籤，並選擇 [設定遮罩]。

3. 在 [輸入遮罩] 對話方塊中，選取 [電話號碼]，然後按一下 [確定] 設定遮罩。

## <a name="add-the-required-data-binding-attribute"></a>新增必要的資料系結屬性

針對支援資料繫結的簡單控制項，實作 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>：

1. 將 **PhoneNumberBox** 控制項切換至程式碼視圖。 (在 [檢視] 功能表上，選擇 [程式碼]。)

2. 以下列程式碼取代 **PhoneNumberBox** 中的程式碼：

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3. 從 [ **組建** ] 功能表中，選擇 [ **建立方案**]。

## <a name="create-a-data-source-from-your-database"></a>從您的資料庫建立資料來源

此步驟會使用 [ **資料來源** 設定] 嚮導，根據 `Customers` Northwind 範例資料庫中的資料表建立資料來源。 您必須具有 Northwind 範例資料庫的存取權，才能建立連接。 如需設定 Northwind 範例資料庫的詳細資訊，請參閱 [如何：安裝範例資料庫](../data-tools/installing-database-systems-tools-and-samples.md)。

1. 若要開啟 [ **資料來源** ] 視窗，請按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。

2. 在 [ **資料來源** ] 視窗中，選取 [ **加入新的資料來源** ] 以啟動 [ **資料來源** 設定向導]。

3. 在 [選擇資料來源類型] 頁面上，選取 [資料庫]，然後按一下 [下一步]。

4. 在 [ **選擇您的資料連線** ] 頁面上，執行下列其中一項：

    - 如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。

    - 選取 [新增連線] 啟動 [新增/修改連線] 對話方塊。

5. 如果資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下 [下一步]。

6. 在 [ **將連接字串儲存到應用程式佈建檔** ] 頁面上，按 **[下一步]**。

7. 展開 [選擇您的資料庫物件] 頁面上的 [資料表] 節點。

8. 選取 `Customers` 資料表，然後按一下 [完成]。

     **NorthwindDataSet** 會加入至您的專案，且 `Customers` 資料表會出現在 [**資料來源**] 視窗中。

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>將電話資料行設定為使用 PhoneNumberBox 控制項

在 [資料來源] 視窗中，您可以設定在將項目拖曳至表單之前建立控制項：

1. 在設計工具中，開啟 **Form1**。

2. 在 [資料來源] 視窗中，展開 [客戶] 節點。

3. 按一下 [客戶] 節點上的下拉式箭頭，並從控制項清單中選擇 [詳細資料]。

4. 按一下 [電話] 資料行上的下拉式箭頭，並選擇 [自訂]。

5. 在 [資料 UI 自訂選項] 對話方塊中，從 [相關聯的控制項] 清單中選取 **PhoneNumberBox**。

6. 按一下 [電話] 資料行上的下拉式箭頭，並選擇 **PhoneNumberBox**。

## <a name="add-controls-to-the-form"></a>將控制項新增至表單

將項目從 [資料來源] 視窗拖曳至表單，以建立資料繫結控制項。

若要在表單上建立資料繫結控制項，請將 [主要 **Customers** ] 節點從 [ **資料來源** ] 視窗拖曳至表單，並確認 **PhoneNumberBox** 控制項是用來顯示 [ **Phone** ] 資料行中的資料。

會在表單上顯示具有描述性的資料繫結控制項，以及巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>)。 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、CustomersTableAdapter、<xref:System.Windows.Forms.BindingSource> 及 <xref:System.Windows.Forms.BindingNavigator> 會顯示在元件匣中。

## <a name="run-the-application"></a>執行應用程式

按 **F5** 執行應用程式。

## <a name="next-steps"></a>下一步

根據應用程式的需求，在建立支援資料繫結程序的控制項之後，可能會有幾個想要執行的步驟。 一些一般後續步驟包括：

- 將自訂控制項放入控制項程式庫，讓您可以在其他應用程式中重複予以使用。

- 建立支援更複雜資料繫結情節的控制項。 如需詳細資訊，請參閱 [建立支援複雜資料系結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) ，以及 [建立支援查閱資料系結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。

## <a name="see-also"></a>另請參閱

- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [設定從 [資料來源] 視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
