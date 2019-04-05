---
title: 建立 Windows Forms 使用者控制項支援簡單資料繫結 |Microsoft Docs
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
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2929d4a524f0da60f2bc32b150b86fdf1ea0cb57
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945272"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>建立支援簡單資料繫結的 Windows Forms 使用者控制項
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
在 Windows 應用程式的表單上顯示資料時，您可以從 [工具箱] 中選擇現有控制項；或者，如果應用程式需要標準控制項中未提供的功能，您也可以撰寫自訂控制項。 這個逐步解說顯示如何建立可實作 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> 的控制項。 可實作 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> 的控制項可以包含一個可繫結至資料的屬性。 這類控制項類似 <xref:System.Windows.Forms.TextBox> 或 <xref:System.Windows.Forms.CheckBox>。  
  
 如需控制項製作的詳細資訊，請參閱[在設計階段開發 Windows Forms 控制項](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829)。  
  
 當製作控制項以用於資料繫結案例，您應該實作下列的資料繫結屬性的其中之一：  
  
|資料繫結屬性使用方式|  
|-----------------------------------|  
|對顯示資料之單一資料行 (或屬性) 的簡單控制項 (如 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>)，實作 <xref:System.Windows.Forms.TextBox> (這個逐步解說頁面會描述此流程)。|  
|對顯示資料之清單 (或資料表) 的控制項 (如 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>)，實作 <xref:System.Windows.Forms.DataGridView> 如需詳細資訊，請參閱 <<c0> [ 建立支援複雜資料繫結 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)。|  
|對顯示資料之清單 (或資料表) 但也需要呈現單一資料行或屬性的控制項 (如 <xref:System.ComponentModel.LookupBindingPropertiesAttribute>)，實作 <xref:System.Windows.Forms.ComboBox>。 如需詳細資訊，請參閱 <<c0> [ 建立支援查閱資料繫結 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。|  
  
 這個逐步解說會建立簡單控制項，以顯示來自資料表中單一資料行的資料。 此範例使用 Northwind 範例資料庫中 `Phone` 資料表的 `Customers` 資料行。 簡單使用者控制項將會顯示標準的電話號碼格式，客戶的電話號碼使用<xref:System.Windows.Forms.MaskedTextBox>並將遮罩設定為電話號碼。  
  
 在這個逐步解說期間，您將了解如何：  
  
-   建立新**Windows 應用程式**。  
  
-   將新 [使用者控制項] 新增至您的專案。  
  
-   透過視覺化方式設計使用者控制項。  
  
-   實作 `DefaultBindingProperty` 屬性。  
  
-   建立與資料集**資料來源組態**精靈。  
  
-   在 [資料來源] 視窗中設定 [電話] 資料行，以使用新的控制項。  
  
-   建立表單以顯示新控制項中的資料。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您將需要：  
  
-   Northwind 範例資料庫的存取權。
  
## <a name="create-a-windows-application"></a>建立 Windows 應用程式  
 第一個步驟是建立**Windows 應用程式**。  
  
#### <a name="to-create-the-new-windows-project"></a>建立新的 Windows 專案  
  
1.  在 Visual Studio 中，從**檔案** 功能表中，建立新**專案**。  
  
2.  將專案命名為**SimpleControlWalkthrough**。  
  
3.  選取  **Windows 應用程式**然後按一下**確定**。 如需詳細資訊，請參閱 <<c0> [ 用戶端應用程式](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)。  
  
     隨即建立 **SimpleControlWalkthrough** 專案，並將其新增至 [方案總管]。  
  
## <a name="add-a-user-control-to-the-project"></a>將使用者控制項新增至專案  
 此逐步解說會建立簡單資料繫結的控制項，從**使用者控制項**，因此加入**使用者控制**項目**SimpleControlWalkthrough**專案。  
  
#### <a name="to-add-a-user-control-to-the-project"></a>將使用者控制項加入至專案  
  
1.  從 [專案] 功能表中，選擇 [新增使用者控制項]。  
  
2.  型別`PhoneNumberBox`在 [名稱] 區域中，然後按一下**新增**。  
  
     [PhoneNumberBox] 控制項會新增至 [方案總管]，並且可在設計工具中開啟。  
  
## <a name="design-the-phonenumberbox-control"></a>設計 PhoneNumberBox 控制項  
 這個逐步解說會從現有 <xref:System.Windows.Forms.MaskedTextBox> 擴充，以建立 `PhoneNumberBox` 控制項。  
  
#### <a name="to-design-the-phonenumberbox-control"></a>設計 PhoneNumberBox 控制項  
  
1.  將 <xref:System.Windows.Forms.MaskedTextBox> 從 [工具箱] 拖曳至使用者控制項的設計介面。  
  
2.  在 <xref:System.Windows.Forms.MaskedTextBox> 上選取您剛剛拖曳的智慧標籤，並選擇 [設定遮罩]。  
  
3.  在 [輸入遮罩] 對話方塊中，選取 [電話號碼]，然後按一下 [確定] 設定遮罩。  
  
## <a name="add-the-required-data-binding-attribute"></a>新增必要的資料繫結屬性  
 針對支援資料繫結的簡單控制項，實作 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>。  
  
#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>實作 DefaultBindingProperty 屬性  
  
1.  將 `PhoneNumberBox` 控制項切換至程式碼檢視  (在 [檢視] 功能表上，選擇 [程式碼]。)  
  
2.  將 `PhoneNumberBox` 中的程式碼取代為下列內容：  
  
     [!code-csharp[VbRaddataDisplaying#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs#3)]
     [!code-vb[VbRaddataDisplaying#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb#3)]  
  
3.  從 [ **建置** ] 功能表中，選擇 [ **建置方案**]。  
  
## <a name="create-a-data-source-from-your-database"></a>從您的資料庫建立資料來源  
 此步驟使用 [資料來源組態精靈]，根據 Northwind 範例資料庫中的 `Customers` 資料表建立資料來源。 您必須具有 Northwind 範例資料庫的存取權，才能建立連接。
  
#### <a name="to-create-the-data-source"></a>若要建立資料來源  
  
1.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。  
  
2.  在 [資料來源] 視窗中，選取 [新增新資料來源]，以啟動 [資料來源組態精靈]。  
  
3.  在 [選擇資料來源類型] 頁面上，選取 [資料庫]，然後按一下 [下一步]。  
  
4.  在 [選擇您的資料連線] 頁面上，執行下列其中一項：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
    -   選取 [新增連線] 啟動 [新增/修改連線] 對話方塊。  
  
5.  如果資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下 [下一步]。  
  
6.  在 [**將連接字串儲存到應用程式組態檔**頁面上，按一下**下一步]**。  
  
7.  展開 [選擇您的資料庫物件] 頁面上的 [資料表] 節點。  
  
8.  選取 `Customers` 資料表，然後按一下 [完成]。  
  
     **NorthwindDataSet** 會新增至您的專案，且 `Customers` 資料表會出現在 [資料來源] 視窗中。  
  
## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>設定 phone 資料行使用 PhoneNumberBox 控制項  
 在 [資料來源] 視窗中，您可以設定在將項目拖曳至表單之前建立控制項。  
  
#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>設定要繫結至 PhoneNumberBox 控制項的 Phone 資料行  
  
1.  在設計工具中，開啟 **Form1**。  
  
2.  在 [資料來源] 視窗中，展開 [客戶] 節點。  
  
3.  按一下 [客戶] 節點上的下拉式箭頭，並從控制項清單中選擇 [詳細資料]。  
  
4.  按一下 [電話] 資料行上的下拉式箭頭，並選擇 [自訂]。  
  
5.  在 [資料 UI 自訂選項] 對話方塊中，從 [相關聯的控制項] 清單中選取 **PhoneNumberBox**。  
  
6.  按一下 [電話] 資料行上的下拉式箭頭，並選擇 **PhoneNumberBox**。  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols 至表單  
 將項目從 [資料來源] 視窗拖曳至表單，以建立資料繫結控制項。  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>在表單上建立資料繫結控制項  
  
-   主**客戶**從節點**Zdroje dat**視窗拖曳至表單，並確認`PhoneNumberBox`控制項用來顯示資料的`Phone`資料行。  
  
     會在表單上顯示具有描述性的資料繫結控制項，以及巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>)。 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、CustomersTableAdapter、<xref:System.Windows.Forms.BindingSource> 及 <xref:System.Windows.Forms.BindingNavigator> 會顯示在元件匣中。  
  
## <a name="run-the-application"></a>執行應用程式  
  
#### <a name="to-run-the-application"></a>若要執行應用程式  
  
-   按 F5 執行應用程式。  
  
## <a name="next-steps"></a>後續步驟  
 根據應用程式的需求，在建立支援資料繫結程序的控制項之後，可能會有幾個想要執行的步驟。 一些一般後續步驟包括：  
  
-   將自訂控制項放入控制項程式庫，讓您可以在其他應用程式中重複予以使用。  
  
-   建立支援更複雜資料繫結情節的控制項。 如需詳細資訊，請參閱 <<c0> [ 建立支援複雜資料繫結 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)並[建立支援查閱資料繫結 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。  
  
## <a name="see-also"></a>另請參閱  
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
