---
title: 建立 Windows Forms 使用者控制項資料繫結
description: 瞭解如何藉由執行 ComplexBindingPropertiesAttribute 類別，建立支援複雜資料系結的 Windows Forms 使用者控制項。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ff8c641cc0b817b5f2a145af49c5e0accdc295d0
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216328"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>建立支援複雜資料繫結的 Windows Forms 使用者控制項

在 Windows 應用程式的表單上顯示資料，您可以選擇從現有的控制項 **工具箱**。 或者，如果您的應用程式需要標準控制項中沒有的功能，您可以編寫自訂控制項。 這個逐步解說顯示如何建立可實作 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> 的控制項。 可實作 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> 的控制項包含可繫結至資料的 `DataSource` 和 `DataMember` 屬性。 這類控制項類似 <xref:System.Windows.Forms.DataGridView> 或 <xref:System.Windows.Forms.ListBox>。

如需控制項製作的詳細資訊，請參閱[開發 Windows Form 控制項在設計階段](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)。

製作控制項以用於資料繫結情節時，您需要實作下列其中一個資料繫結屬性：

|資料系結屬性使用方式|
| - |
|對顯示資料之單一資料行 (或屬性) 的簡單控制項 (如 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>)，實作 <xref:System.Windows.Forms.TextBox> 如需詳細資訊，請參閱 [建立支援簡單資料系結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)。|
|對顯示資料之清單 (或資料表) 的控制項 (如 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>)，實作 <xref:System.Windows.Forms.DataGridView> (這個逐步解說頁面會描述此流程)。|
|對顯示資料之清單 (或資料表) 但也需要呈現單一資料行或屬性的控制項 (如 <xref:System.ComponentModel.LookupBindingPropertiesAttribute>)，實作 <xref:System.Windows.Forms.ComboBox>。 如需詳細資訊，請參閱 [建立支援查閱資料系結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。|

這個逐步解說會建立顯示資料表中資料列的複雜控制項。 此範例使用 Northwind 範例資料庫中的 `Customers` 資料表。 複雜使用者控制項將會在自訂控制項的 <xref:System.Windows.Forms.DataGridView> 中顯示 customers 資料表。

在這個逐步解說中，您將瞭解如何：

- 將新 [使用者控制項] 新增至您的專案。

- 透過視覺化方式設計使用者控制項。

- 實作 `ComplexBindingProperty` 屬性。

- 使用 [ [資料來源設定]](../data-tools/media/data-source-configuration-wizard.png)建立資料集。

- 在 [[資料來源] 視窗](add-new-data-sources.md#data-sources-window)中設定 [ **Customers** ] 資料表，以使用新的複雜控制項。

- 新增控制項，方法是將它從 [資料來源] 視窗拖曳至 [Form1]。

## <a name="prerequisites"></a>必要條件

本逐步解說使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1. 如果您沒有 LocalDB SQL Server Express，請從 [SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)或透過 **Visual Studio 安裝程式** 進行安裝。 在 **Visual Studio 安裝程式** 中，您可以安裝 SQL Server Express LocalDB 作為 **資料儲存和處理** 工作負載的一部分，或安裝為個別的元件。

1. 遵循下列步驟來安裝 Northwind 範例資料庫：

    1. 在 Visual Studio 中，開啟 [ **SQL Server 物件總管** ] 視窗。  (SQL Server 物件總管會安裝為 Visual Studio 安裝程式中 **資料儲存和處理** 工作負載的一部分。 ) 展開 **SQL Server** 節點。 以滑鼠右鍵按一下您的 LocalDB 實例，然後選取 [追加 **查詢**]。

       [查詢編輯器] 視窗隨即開啟。

    1. 將 [Northwind transact-sql 腳本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 複製到剪貼簿。 此 T-sql 腳本會從頭開始建立 Northwind 資料庫，並在其中填入資料。

    1. 將 T-sql 腳本貼入 [查詢編輯器]，然後選擇 [ **執行** ] 按鈕。

       經過一小段時間之後，查詢就會完成執行，並建立 Northwind 資料庫。

## <a name="create-a-windows-forms-app-project"></a>建立 Windows Forms 應用程式專案

第一個步驟是建立適用于 c # 或 Visual Basic 的 **Windows Forms 應用程式** 專案。 將專案命名為 **ComplexControlWalkthrough**。

## <a name="add-a-user-control-to-the-project"></a>將使用者控制項新增至專案

因為這個逐步解說會從 **使用者控制項** 建立複雜的資料可繫結控制項，所以請將 **使用者控制項** 專案加入至專案：

1. 從 [專案] 功能表中，選擇 [新增使用者控制項]。

1. 在 [名稱] 區域中鍵入 **ComplexDataGridView**，然後按一下 [新增]。

    [ComplexDataGridView] 控制項會新增至 [方案總管]，並在設計工具中予以開啟。

## <a name="design-the-complexdatagridview-control"></a>設計 ComplexDataGridView 控制項

若要將加入 <xref:System.Windows.Forms.DataGridView> 至使用者控制項，請將 <xref:System.Windows.Forms.DataGridView> 從 [ **工具箱** ] 拖曳至使用者控制項的設計介面。

## <a name="add-the-required-data-binding-attribute"></a>新增必要的資料系結屬性

針對支援資料繫結的複雜控制項，您可以實作 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>：

1. 將 [ComplexDataGridView] 控制項切換至程式碼檢視 (在 [檢視] 功能表上，選取 [程式碼])。

1. 將 `ComplexDataGridView` 中的程式碼取代為下列內容：

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs" id="Snippet4":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb" id="Snippet4":::

1. 從 [ **組建** ] 功能表中，選擇 [ **建立方案**]。

## <a name="create-a-data-source-from-your-database"></a>從您的資料庫建立資料來源

您可以使用 [ **資料來源** 設定] 建立資料來源，根據 `Customers` Northwind 範例資料庫中的資料表建立資料來源：

1. 若要開啟 [ **資料來源** ] 視窗，請按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。

2. 在 [ **資料來源** ] 視窗中，選取 [ **加入新的資料來源** ] 以啟動 [ **資料來源** 設定向導]。

3. 請選取 [ **選擇資料來源類型** ] 頁面上的 [ **資料庫** ]，再按 [ **下一步**]。

4. 在 [選擇您的資料連線] 頁面上，執行下列其中一項：

   - 如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。

   - 選取 [新增連線] 啟動 [新增/修改連線] 對話方塊。

5. 如果資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下 [下一步]。

6. 在 [ **將連接字串儲存到應用程式佈建檔** ] 頁面上，按 **[下一步]**。

7. 展開 [選擇您的資料庫物件] 頁面上的 [資料表] 節點。

8. 選取 `Customers` 資料表，然後按一下 [完成]。

   **NorthwindDataSet** 會加入至您的專案，且 `Customers` 資料表會出現在 [**資料來源**] 視窗中。

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>設定 Customers 資料表以使用 ComplexDataGridView 控制項

在 [資料來源] 視窗中，您可以設定在將項目拖曳至表單之前建立控制項：

1. 在設計工具中，開啟 **Form1**。

1. 在 [資料來源] 視窗中，展開 [客戶] 節點。

1. 按一下 [Customers] 節點上的下拉箭號，並選擇 [自訂]。

1. 在 [資料 UI 自訂選項] 對話方塊中，從 [相關聯的控制項] 清單選取 [ComplexDataGridView]。

1. 按一下 `Customers` 資料表上的下拉箭號，並從控制項清單中選擇 [ComplexDataGridView]。

## <a name="add-controls-to-the-form"></a>將控制項新增至表單

您可以從 [ **資料來源** ] 視窗將專案拖曳至表單，以建立資料繫結控制項。 將 [Customers] 主節點從 [資料來源] 視窗拖曳至表單。 確認 **ComplexDataGridView** 控制項是用來顯示資料表的資料。

## <a name="run-the-application"></a>執行應用程式

按 **F5** 執行應用程式。

## <a name="next-steps"></a>下一步

根據應用程式的需求，在建立支援資料繫結程序的控制項之後，可能會有幾個想要執行的步驟。 一些一般後續步驟包括：

- 將自訂控制項放入控制項程式庫，讓您可以在其他應用程式中重複予以使用。

- 建立支援查閱情節的控制項。 如需詳細資訊，請參閱 [建立支援查閱資料系結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。

## <a name="see-also"></a>另請參閱

- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [設定從 [資料來源] 視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Windows Forms 控制項](/dotnet/framework/winforms/controls/index)
