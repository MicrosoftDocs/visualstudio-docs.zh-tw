---
title: 建立支援複雜資料繫結 Windows Forms 使用者控制項 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de22f93c6fd04f89360fdaf8a2f5d83bd373d93d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284254"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>建立支援複雜資料繫結 Windows Forms 使用者控制項
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
在 Windows 應用程式的表單上顯示資料，您可以選擇從現有的控制項**工具箱**，或者如果您的應用程式需要標準控制項中沒有的功能，您可以編寫自訂控制項。 這個逐步解說顯示如何建立可實作 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> 的控制項。 可實作 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> 的控制項包含可繫結至資料的 `DataSource` 和 `DataMember` 屬性。 這類控制項類似 <xref:System.Windows.Forms.DataGridView> 或 <xref:System.Windows.Forms.ListBox>。  
  
 如需控制項製作的詳細資訊，請參閱[在設計階段開發 Windows Forms 控制項](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829)。  
  
 製作控制項以用於資料繫結情節時您需要實作下列的資料繫結屬性的其中一個：  
  
|資料繫結屬性使用方式|  
|-----------------------------------|  
|對顯示資料之單一資料行 (或屬性) 的簡單控制項 (如 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>)，實作 <xref:System.Windows.Forms.TextBox> 如需詳細資訊，請參閱 <<c0> [ 建立支援簡單資料繫結 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)。|  
|對顯示資料之清單 (或資料表) 的控制項 (如 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>)，實作 <xref:System.Windows.Forms.DataGridView> (這個逐步解說頁面會描述此流程)。|  
|對顯示資料之清單 (或資料表) 但也需要呈現單一資料行或屬性的控制項 (如 <xref:System.ComponentModel.LookupBindingPropertiesAttribute>)，實作 <xref:System.Windows.Forms.ComboBox>。 如需詳細資訊，請參閱 <<c0> [ 建立支援查閱資料繫結 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。|  
  
 這個逐步解說會建立顯示資料表中資料列的複雜控制項。 此範例使用 Northwind 範例資料庫中的 `Customers` 資料表。 複雜使用者控制項將會在自訂控制項的 <xref:System.Windows.Forms.DataGridView> 中顯示 customers 資料表。  
  
 在這個逐步解說期間，您將了解如何：  
  
-   建立新**Windows 應用程式**。  
  
-   加入新**使用者控制項**至您的專案。  
  
-   透過視覺化方式設計使用者控制項。  
  
-   實作 `ComplexBindingProperty` 屬性。  
  
-   建立與資料集[資料來源組態精靈](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)。  
  
-   設定**客戶**資料表中[資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)使用新的複雜控制項。  
  
-   新增新的控制項將它從拖曳**資料來源 視窗**拖曳至**Form1**。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您將需要：  
  
-   Northwind 範例資料庫的存取權。 如需詳細資訊，請參閱 <<c0> [ 如何： 安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## <a name="create-a-windows-application"></a>建立 Windows 應用程式  
 第一個步驟是建立**Windows 應用程式**。  
  
#### <a name="to-create-the-new-windows-project"></a>建立新的 Windows 專案  
  
1.  在 Visual Studio 中，從**檔案** 功能表中，建立新**專案**。  
  
2.  將專案命名為**ComplexControlWalkthrough**。  
  
3.  選取  **Windows 應用程式**，然後按一下**確定**。 如需詳細資訊，請參閱 <<c0> [ 用戶端應用程式](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)。  
  
     **ComplexControlWalkthrough**專案時建立，並加入至**方案總管 中**。  
  
## <a name="add-a-user-control-to-the-project"></a>將使用者控制項加入至專案  
 因為本逐步解說會建立複雜的資料可繫結控制項，從**使用者控制項**，您必須新增**使用者控制**項目加入專案。  
  
#### <a name="to-add-a-user-control-to-the-project"></a>將使用者控制項加入至專案  
  
1.  從**專案**功能表上，選擇**加入使用者控制項**。  
  
2.  型別**ComplexDataGridView**中**名稱**區域，，然後按一下**新增**。  
  
     **ComplexDataGridView**控制項加入至**方案總管 中**，並在設計工具中開啟。  
  
## <a name="design-the-complexdatagridview-control"></a>設計 ComplexDataGridView 控制項  
 此步驟會將 <xref:System.Windows.Forms.DataGridView> 加入至使用者控制項。  
  
#### <a name="to-design-the-complexdatagridview-control"></a>設計 ComplexDataGridView 控制項  
  
-   拖曳<xref:System.Windows.Forms.DataGridView>從**工具箱**拖曳至使用者控制項的設計介面。  
  
## <a name="add-the-required-data-binding-attribute"></a>新增必要的資料繫結屬性  
 針對支援資料繫結的複雜控制項，您可以實作 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>。  
  
#### <a name="to-implement-the-complexbindingproperties-attribute"></a>實作 ComplexBindingProperties 屬性  
  
1.  交換器**ComplexDataGridView**程式碼 檢視的控制項。 (在**檢視**功能表上，選取**程式碼**。)  
  
2.  將 `ComplexDataGridView` 中的程式碼取代為下列內容：  
  
     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]  
  
3.  從 [ **建置** ] 功能表中，選擇 [ **建置方案**]。  
  
## <a name="creating-a-data-source-from-your-database"></a>從您的資料庫建立資料來源  
 此步驟中使用**資料來源組態**精靈來建立資料來源基礎`Customers`Northwind 範例資料庫中的資料表。 您必須具有 Northwind 範例資料庫的存取權，才能建立連接。 如需設定 Northwind 範例資料庫的詳細資訊，請參閱[安裝 SQL Server 範例資料庫](../data-tools/install-sql-server-sample-databases.md)。  
  
#### <a name="to-create-the-data-source"></a>若要建立資料來源  
  
1.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。  
  
2.  在 **資料來源**視窗中，選取**加入新的資料來源**來啟動**資料來源組態**精靈。  
  
3.  請選取 [ **選擇資料來源類型** ] 頁面上的 [ **資料庫** ]，再按 [ **下一步**]。  
  
4.  在 **選擇您的資料連接**頁面上，執行下列其中之一：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
    -   選取 [**新的連線**來啟動**加入/修改連接**] 對話方塊。  
  
5.  如果您的資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下**下一步**。  
  
6.  在 [**將連接字串儲存到應用程式組態檔**頁面上，按一下**下一步]**。  
  
7.  在 **選擇您的資料庫物件**頁面上，展開**資料表**節點。  
  
8.  選取 `Customers`資料表，然後按一下**完成**。  
  
     **NorthwindDataSet**新增至您的專案，而`Customers`資料表會出現在**Zdroje dat**視窗。  
  
## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>設定 Customers 資料表使用 ComplexDataGridView 控制項  
 內**Zdroje dat**  視窗中，您可以設定要在將項目拖曳至表單之前建立的控制項。  
  
#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>設定要繫結至 ComplexDataGridView 控制項的 Customers 資料表  
  
1.  開啟**Form1**設計工具中。  
  
2.  依序展開**客戶**中的節點**Zdroje dat**視窗。  
  
3.  按一下下拉箭號**客戶**節點，然後選擇**自訂**。  
  
4.  選取 [ **ComplexDataGridView**從清單中的**關聯的控制項**中**資料的 UI 自訂選項**] 對話方塊。  
  
5.  按一下下拉箭號`Customers`資料表，然後選擇  **ComplexDataGridView**從控制項清單。  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols 至表單  
 您可以建立資料繫結控制項項目從**Zdroje dat**視窗拖曳至表單。  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>在表單上建立資料繫結控制項  
  
-   主**客戶**從節點**Zdroje dat**視窗拖曳至表單。確認**ComplexDataGridView**控制項用來顯示資料表的資料。  
  
## <a name="running-the-application"></a>執行應用程式  
  
#### <a name="to-run-the-application"></a>若要執行應用程式  
  
-   按 F5 執行應用程式。  
  
## <a name="next-steps"></a>後續步驟  
 根據應用程式的需求，在建立支援資料繫結程序的控制項之後，可能會有幾個想要執行的步驟。 一些一般後續步驟包括：  
  
-   將自訂控制項放入控制項程式庫，讓您可以在其他應用程式中重複予以使用。  
  
-   建立支援查閱情節的控制項。 如需詳細資訊，請參閱 <<c0> [ 建立支援查閱資料繫結 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。  
  
## <a name="see-also"></a>另請參閱  
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [設定要從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Windows Forms 控制項](http://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)

