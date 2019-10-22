---
title: 建立支援複雜資料系結的 Windows Forms 使用者控制項 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99c4a20939ed2e3a036831930749bb59b5a42315
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670044"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>建立支援複雜資料繫結的 Windows Forms 使用者控制項
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Windows 應用程式的表單上顯示資料時，您可以從 [工具箱] 中選擇現有控制項；或者，如果應用程式需要標準控制項中未提供的功能，您也可以撰寫自訂控制項。 這個逐步解說顯示如何建立可實作 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> 的控制項。 可實作 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> 的控制項包含可繫結至資料的 `DataSource` 和 `DataMember` 屬性。 這類控制項類似 <xref:System.Windows.Forms.DataGridView> 或 <xref:System.Windows.Forms.ListBox>。

 如需控制項撰寫的詳細資訊，請參閱[在設計階段開發 Windows Forms 控制項](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829)。

 製作控制項以用於資料繫結情節時，您需要實作下列其中一個資料繫結屬性：

|資料系結屬性使用方式|
|-----------------------------------|
|對顯示資料之單一資料行 (或屬性) 的簡單控制項 (如 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>)，實作 <xref:System.Windows.Forms.TextBox> 如需詳細資訊，請參閱[建立支援簡單資料系結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)。|
|對顯示資料之清單 (或資料表) 的控制項 (如 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>)，實作 <xref:System.Windows.Forms.DataGridView> (這個逐步解說頁面會描述此流程)。|
|對顯示資料之清單 (或資料表) 但也需要呈現單一資料行或屬性的控制項 (如 <xref:System.ComponentModel.LookupBindingPropertiesAttribute>)，實作 <xref:System.Windows.Forms.ComboBox>。 如需詳細資訊，請參閱[建立支援查閱資料系結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。|

 這個逐步解說會建立顯示資料表中資料列的複雜控制項。 此範例使用 Northwind 範例資料庫中的 `Customers` 資料表。 複雜使用者控制項將會在自訂控制項的 <xref:System.Windows.Forms.DataGridView> 中顯示 customers 資料表。

 在這個逐步解說期間，您將了解如何：

- 建立新的**Windows 應用程式**。

- 將新 [使用者控制項] 新增至您的專案。

- 透過視覺化方式設計使用者控制項。

- 實作 `ComplexBindingProperty` 屬性。

- 使用[資料來源設定向導](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)來建立資料集。

- 將 [[資料來源] 視窗](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)中的 [ **Customers** ] 資料表設定為使用新的複雜控制項。

- 將新的控制項從 [**資料來源] 視窗**拖曳至 [ **Form1**]，以加入它。

## <a name="prerequisites"></a>Prerequisites
 若要完成這個逐步解說，您將需要：

- Northwind 範例資料庫的存取權。

## <a name="create-a-windows-application"></a>建立 Windows 應用程式
 第一個步驟是建立**Windows 應用程式**。

#### <a name="to-create-the-new-windows-project"></a>建立新的 Windows 專案

1. 在 Visual Studio 中，從 **[檔案**] 功能表建立新的**專案**。

2. 將專案命名為**ComplexControlWalkthrough**。

3. 選取 [ **Windows 應用程式**]，然後按一下 **[確定]** 。 如需詳細資訊，請參閱[用戶端應用程式](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)。

     隨即建立 **ComplexControlWalkthrough** 專案，並將它新增至 [方案總管]。

## <a name="add-a-user-control-to-the-project"></a>將使用者控制項新增至專案
 因為這個逐步解說會從**使用者控制項**建立複雜的資料可系結控制項，所以您必須將**使用者控制項**專案加入至專案。

#### <a name="to-add-a-user-control-to-the-project"></a>將使用者控制項加入至專案

1. 從 [專案] 功能表中，選擇 [新增使用者控制項]。

2. 在 [名稱] 區域中鍵入 **ComplexDataGridView**，然後按一下 [新增]。

     [ComplexDataGridView] 控制項會新增至 [方案總管]，並在設計工具中予以開啟。

## <a name="design-the-complexdatagridview-control"></a>設計 ComplexDataGridView 控制項
 此步驟會將 <xref:System.Windows.Forms.DataGridView> 加入至使用者控制項。

#### <a name="to-design-the-complexdatagridview-control"></a>設計 ComplexDataGridView 控制項

- 將 <xref:System.Windows.Forms.DataGridView> 從 [工具箱] 拖曳至使用者控制項的設計介面。

## <a name="add-the-required-data-binding-attribute"></a>新增必要的資料系結屬性
 針對支援資料繫結的複雜控制項，您可以實作 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>。

#### <a name="to-implement-the-complexbindingproperties-attribute"></a>實作 ComplexBindingProperties 屬性

1. 將 [ComplexDataGridView] 控制項切換至程式碼檢視 (在 [檢視] 功能表上，選取 [程式碼])。

2. 將 `ComplexDataGridView` 中的程式碼取代為下列內容：

     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]

3. 從 [ **建置** ] 功能表中，選擇 [ **建置方案**]。

## <a name="creating-a-data-source-from-your-database"></a>從您的資料庫建立資料來源
 此步驟使用 [資料來源組態精靈]，根據 Northwind 範例資料庫中的 `Customers` 資料表建立資料來源。 您必須具有 Northwind 範例資料庫的存取權，才能建立連接。 如需設定 Northwind 範例資料庫的詳細資訊，請參閱[安裝 SQL Server 範例資料庫](../data-tools/install-sql-server-sample-databases.md)。

#### <a name="to-create-the-data-source"></a>若要建立資料來源

1. 按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。

2. 在 [資料來源] 視窗中，選取 [新增新資料來源]，以啟動 [資料來源組態精靈]。

3. 請選取 [ **選擇資料來源類型** ] 頁面上的 [ **資料庫** ]，再按 [ **下一步**]。

4. 在 [選擇您的資料連線] 頁面上，執行下列其中一項：

    - 如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。

    - 選取 [新增連線] 啟動 [新增/修改連線] 對話方塊。

5. 如果資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下 [下一步]。

6. 在 [將**連接字串儲存到應用程式佈建檔**] 頁面上，按 **[下一步]** 。

7. 展開 [選擇您的資料庫物件] 頁面上的 [資料表] 節點。

8. 選取 `Customers` 資料表，然後按一下 [完成]。

     **NorthwindDataSet** 會新增至您的專案，且 `Customers` 資料表會出現在 [資料來源] 視窗中。

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>將 Customers 資料表設定為使用 ComplexDataGridView 控制項
 在 [資料來源] 視窗中，您可以設定在將項目拖曳至表單之前建立控制項。

#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>設定要繫結至 ComplexDataGridView 控制項的 Customers 資料表

1. 在設計工具中，開啟 **Form1**。

2. 在 [資料來源] 視窗中，展開 [客戶] 節點。

3. 按一下 [Customers] 節點上的下拉箭號，並選擇 [自訂]。

4. 在 [資料 UI 自訂選項] 對話方塊中，從 [相關聯的控制項] 清單選取 [ComplexDataGridView]。

5. 按一下 `Customers` 資料表上的下拉箭號，並從控制項清單中選擇 [ComplexDataGridView]。

## <a name="addcontrols-to-the-form"></a>Addcontrols 至表單
 您可以從 [資料來源] 視窗將項目拖曳至表單，以建立資料繫結控制項。

#### <a name="to-create-data-bound-controls-on-the-form"></a>在表單上建立資料繫結控制項

- 將 [ **Customers** ] 主節點從 [**資料來源**] 視窗拖曳至表單。確認**ComplexDataGridView**控制項是用來顯示資料表的資料。

## <a name="running-the-application"></a>執行應用程式

#### <a name="to-run-the-application"></a>若要執行應用程式

- 按 F5 執行應用程式。

## <a name="next-steps"></a>後續步驟
 根據應用程式的需求，在建立支援資料繫結程序的控制項之後，可能會有幾個想要執行的步驟。 一些一般後續步驟包括：

- 將自訂控制項放入控制項程式庫，讓您可以在其他應用程式中重複予以使用。

- 建立支援查閱情節的控制項。 如需詳細資訊，請參閱[建立支援查閱資料系結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。

## <a name="see-also"></a>請參閱
 將[Windows Forms 控制項系結至中的資料 Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [設定從 [資料來源] 視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md) [Windows Forms 控制項](https://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)
