---
title: 功能區設計工具
description: 瞭解如何使用功能區設計工具，將自訂索引標籤、群組和控制項新增至 Microsoft Office 應用程式的功能區。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, about Ribbon Designer
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- customizing the Ribbon, about Ribbon Designer
- Ribbon [Office development in Visual Studio], visual designer
- customizing the Ribbon
- custom Ribbon
- designers [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon [Office development in Visual Studio], common tasks
- Ribbon Designer [Office development in Visual Studio]
- read-only properties
- Ribbon [Office development in Visual Studio], shortcut keys
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 06211bb22ae071132b4cfad67352daa46182d366
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940913"
---
# <a name="ribbon-designer"></a>功能區設計工具
  功能區設計工具是一種視覺化設計畫布。 您可以使用功能區設計工具，將自訂索引標籤、群組和控制項新增至 Microsoft Office 應用程式的功能區。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 若要開啟功能區設計工具，請將 **功能區 (的視覺化設計工具)** 專案加入至您的專案。 然後，您可以使用設計工具來執行下列工作：

- [設計功能區版面配置](#DesigningRibbonLayout)

- [處理事件並設定控制項屬性](#HandleEventsSetProperties)

- [將控制項新增至 Backstage 檢視](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
> 您可以使用功能區設計工具來完成一些工作。 如需這些工作以及如何完成這些工作的詳細資訊，請參閱 [功能區總覽](../vsto/ribbon-overview.md)。

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>將功能區 (視覺化設計工具) 專案加入至專案
 若要使用功能區設計工具，請在您的專案中加入新的 **功能區 (的視覺化設計工具)** 專案。 如需詳細資訊，請參閱 [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。

 當您加入新的 **功能區 (視覺化設計工具)** 專案時，Visual Studio 會自動將下列檔案加入至您的專案：

- 功能區程式碼檔案。 這個檔案的名稱是您在 [**加入新專案**] 對話方塊中， **(視覺化設計工具) 專案的功能區** 所指定的名稱。 加入程式碼來處理這個檔案的功能區事件。

- 功能區設計工具程式碼檔案。 這個檔案包含功能區設計工具所產生的程式碼，不應該直接編輯。

- 資源檔。 這個檔案包含功能區上每個控制項的屬性值。

  如果您已經有一個 **功能區 (視覺化設計工具)** 專案來自另一個專案，則可以使用 [ **加入現有專案** ] 對話方塊在目前的專案中重複使用它。

## <a name="design-a-ribbon"></a><a name="DesigningRibbonLayout"></a> 設計功能區
 開啟功能區設計工具的方法有三種：

- 在 **方案總管** 中，按兩下功能區程式碼檔案。

- 在 **方案總管** 中，以滑鼠右鍵按一下功能區程式碼檔案，然後按一下 [ **視圖設計** 工具]。

- 在 **方案總管** 中，選取功能區程式碼檔案，然後按一下 [ **View** ] 功能表上的 [**設計** 工具]。

  [功能區設計工具] 包含預設索引標籤和群組。 您可以從功能區設計工具中移除預設索引標籤和群組。 若要移除預設群組，請以滑鼠右鍵按一下 [ **Group1**]，然後按一下 [ **刪除**]。 若要移除預設索引標籤，請在設計介面的空白區域上按一下滑鼠右鍵，然後按一下 [ **移除功能區]** 索引標籤。

  您也可以將自訂索引標籤、群組和控制項加入至功能區設計工具。 您可以在 [ **工具箱**] 的 [ **Office 功能區控制項** ] 群組中找到這些控制項。 有三種方式可以將控制項從 **Office 功能區控制項** 群組加入至功能區設計工具：

- 將控制項拖曳至功能區設計工具上的適當區域。

- 按一下控制項，然後按一下功能區設計工具中的適當區域。

- 在設計工具中選取適當的區域，然後按兩下 [ **工具箱**] 中的控制項。

### <a name="ribbon-design-workflow"></a>功能區設計工作流程
 遵循下列基本步驟來設計功能區版面配置：

1. [將自訂索引標籤加入功能區](#AddTabToRibbon)。

2. [將群組加入至](#AddGroupsToTab)索引標籤。

3. [將控制項加入至群組](#AddControlsToGroups)。

   只能將控制項放在群組上;您無法直接將控制項拖曳到索引標籤或功能區。 群組只能放在索引標籤上;您無法直接將群組拖曳至功能區。

   將控制項拖曳至正確的位置，以排列控制項。 您可以使用 [ **屬性** ] 視窗來設定控制項的屬性。

   您無法將控制項從某個索引標籤拖曳至功能區上的另一個索引標籤。 如果您想要將控制項移至另一個索引標籤，您必須使用 [ **剪** 下] 命令從一個索引標籤移除控制項，然後將控制項貼到另一個索引標籤上。如果您將控制項剪下並貼上，事件處理常式就會停止運作。 您可以在 [ **屬性** ] 視窗中重新連接事件處理常式。 如需詳細資訊，請參閱 [屬性視窗](../ide/reference/properties-window.md)。

### <a name="add-custom-tabs-to-the-ribbon"></a><a name="AddTabToRibbon"></a> 將自訂索引標籤新增至功能區
 有三種方式可以將自訂索引標籤新增至功能區：

- 從 [ **工具箱**] 新增索引標籤。

- 以滑鼠右鍵按一下 [功能區設計工具]，然後按一下 [ **加入功能區]** 索引標籤。

- 開啟 [索引標籤 **集合編輯器]**，然後按一下 [ **新增**]。

   若要開啟 [索引標籤 **集合編輯器**]，請在 [ **屬性** ] 視窗中 **選取 [索引** 標籤] 屬性，然後按一下省略號按鈕 ![ASP.NET Mobile Designer 橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")。

  加入索引標籤之後，您可以加入群組以包含控制項。

#### <a name="remove-custom-tabs-from-the-ribbon"></a>從功能區移除自訂索引標籤
 有三種方式可從功能區移除自訂索引標籤：

- 以滑鼠右鍵按一下設計工具，然後按一下 [ **移除功能區]** 索引標籤。

- 在 [**屬性**] 視窗的 [**命令**] 窗格中，按一下 [**移除功能區]** 索引標籤。

- 開啟 [索引標籤 **集合編輯器**]，選取索引標籤，然後按一下 [ **移除**]。

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>變更功能區上的索引標籤位置
 您可以變更功能區上的自訂索引標籤順序。 您也可以在功能區上的內建索引標籤之前或之後放置自訂索引標籤。 如需詳細資訊，請參閱 [如何：變更功能區上](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)的索引標籤位置。

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>自訂功能區上的內建索引標籤
 內建索引標籤是已在 Microsoft Office 應用程式功能區上的索引標籤。 例如，[ **資料** ] 索引標籤是 Excel 中的內建索引標籤。

 您可以將群組和控制項加入至內建索引標籤。依預設，自訂群組會顯示為內建索引標籤上的最後一個群組，不過您可以在索引標籤上的任何內建組之前或之後移動。

 您無法移除內建組。

 如需如何自訂內建索引標籤的詳細資訊，請參閱 [如何：自訂內建](../vsto/how-to-customize-a-built-in-tab.md)索引標籤。

### <a name="add-groups-to-a-tab"></a><a name="AddGroupsToTab"></a> 將群組加入至索引標籤
 群組會以邏輯方式組織功能區上的控制項。 將群組加入至索引標籤。 將所有其他控制項新增至群組。

### <a name="add-controls-to-groups"></a><a name="AddControlsToGroups"></a> 將控制項新增至群組
 將一或多個控制項加入至群組。 下表描述每個控制項。

|控制|描述|
|-------------|-----------------|
|**Box**|在群組中組織控制項的容器。 除了分隔符號、群組或索引標籤之外，您還可以將任何控制項新增至方塊。方塊可以是水準或垂直。|
|**按鈕**|啟動動作的按鈕。 您可以將按鈕加入至群組、按鈕群組、下拉式清單、資源庫、功能表或分割按鈕。|
|**ButtonGroup**|包含一或多個按鈕、切換按鈕、功能表、分割按鈕和圖庫的群組。 您可以將按鈕群組新增至群組或功能表。|
|**CheckBox**|選取或清除以開啟或關閉選項的方塊。|
|**ComboBox**|已附加清單方塊的編輯方塊。 使用者可以輸入或選取其選擇。 方塊會顯示目前的選取範圍。 在 <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> 功能區載入至 Office 應用程式之前或之後，使用屬性在執行時間加入和移除專案。|
|**拉**|使用者可以選取的專案清單。 使用者無法在下拉式清單中輸入新專案。<br /><br /> 您 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> 可以使用屬性將專案加入至清單。 您可以在執行時間加入和移除專案。<br /><br /> 您 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> 可以使用屬性，將按鈕加入至清單。 不過，在功能區載入至 Office 應用程式之後，您無法在執行時間加入和移除按鈕。|
|**編輯方塊**|使用者可以在其中輸入文字的方塊。|
|**主機庫**|此功能表會顯示使用者可以選取的視覺效果選擇的陣列或方格。 您可以控制功能表中選取專案的版面配置。 您 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> 可以使用和 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> 屬性，指定將顯示資源庫之專案和按鈕的資料列和資料行數目。|
|**標籤**|您可以用來識別功能區上控制項的文字。|
|**功能表**|可以包含下列任何控制項的下拉式清單：<br /><br /> -按鈕<br />-核取方塊<br />-資源庫<br />-功能表<br />-分割按鈕<br />-切換按鈕<br />-分隔符號<br /><br /> 若要將控制項加入至功能區設計工具中的功能表，請按一下功能表中的向下箭號，以公開功能表設計介面。 然後，您可以將功能區控制項從 [ **工具箱** ] 拖曳到功能表上。 若要排列控制項，請將其拖曳至想要的位置。<br /><br /> 若要在 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> 功能區載入至 Office 應用程式之後將控制項加入至，您必須在 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> 載入功能區之前將屬性設定為 **true** 。 如需如何進行此作業的詳細資訊，請參閱 [功能區物件模型總覽](../vsto/ribbon-object-model-overview.md)。|
|**Separator**|用來分隔清單中專案的精簡型列。 當加入至群組時，橫條會垂直。 當加入至功能表時，橫條是水準的。|
|**SplitButton**|已附加功能表的按鈕。 分割按鈕可以包含下列任何控制項：<br /><br /> -按鈕<br />-核取方塊<br />-資源庫<br />-功能表<br />-分割按鈕<br />-切換按鈕<br />-分隔符號<br /><br /> 如同功能表，[分割] 按鈕有自己的設計介面。 但是，與功能表不同的是，在功能區載入至 Office 應用程式之前，您只能在分割按鈕中更新專案。 如需如何更新分割按鈕中專案的詳細資訊，請參閱 [功能區物件模型總覽](../vsto/ribbon-object-model-overview.md)。|
|**ToggleButton**|顯示為已按下或未按下的按鈕。|

## <a name="handle-events-and-setting-properties"></a><a name="HandleEventsSetProperties"></a> 處理事件及設定屬性
 功能區設計工具可讓您使用 [ **屬性** ] 視窗，在設計階段設定控制項屬性。 此外，功能區也會公開強型別物件模型，您可以在執行時間用來取得和設定功能區控制項的屬性。

 您可以按兩下設計工具上的任何控制項，以開啟控制項預設事件的事件處理常式。 您可以使用 [ **屬性** ] 視窗，為所有其他控制項事件建立事件處理常式。

 功能區事件和屬性位於 <xref:Microsoft.Office.Tools.Ribbon> 命名空間中。 **功能區 (視覺化設計工具)** 專案會自動將參考加入至專案中的這個元件，並在功能區程式碼檔案的頂端插入適當的 **using** 或 **Imports** 語句。

 如需處理功能區事件，以及在執行時間設定功能區控制項屬性的詳細資訊，請參閱 [功能區物件模型總覽](../vsto/ribbon-object-model-overview.md)。

## <a name="customize-backstage-view"></a><a name="CustomizingMicrosoftOfficeButton"></a> 自訂 Backstage 檢視
 您可以使用功能區設計工具，將控制項加入至按一下 [檔案] 索引標籤時 **開啟的功能表** 。此功能表稱為 Backstage view。

 您無法使用功能區設計工具，將控制項放在內建控制項之前或之後。 內建控制項是在 Backstage view 中已顯示的控制項。 如果您想要在內建控制項之前或之後放置控制項，您必須使用功能區 XML。 如需 **功能區 (XML)** 的詳細資訊，請參閱 [功能區 xml](../vsto/ribbon-xml.md)。 如需自訂 Backstage 檢視的詳細資訊，請參閱 [適用于開發人員的 office 2010 Backstage 檢視簡介](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) 和 [自訂開發人員適用的 office 2010 backstage 視圖](/previous-versions/office/developer/office-2010/ee815851(v=office.14))。

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 如需有關如何將控制項加入至 Backstage 檢視的詳細資訊，請參閱 [如何：將控制項加入至 backstage 視圖](../vsto/how-to-add-controls-to-the-backstage-view.md)。

## <a name="accessibility-in-the-ribbon-designer"></a><a name="Accessibility"></a> 功能區設計工具中的協助工具
 您可以使用鍵盤快速鍵，在功能區設計工具中移動控制項。 某些鍵盤快速鍵適用于所有控制項，有些則只適用于具有功能表的控制項。

 下表顯示適用于所有控制項的鍵盤快速鍵。

|動作|鍵盤快速鍵|
|------------|-----------------------|
|將控制項移至清單中的上一個控制項之前。|**Ctrl** +**向上**<br /><br /> **Ctrl** +**左方**|
|將控制項移到清單中的下一個控制項之後。|**Ctrl** +**向下**<br /><br /> **Ctrl** +**Right**|
|將選取範圍從一個控制項移至相同群組中的另一個控制項。 針對下拉式面板，在父控制項和下拉式面板中的控制項之間移動。|**Up**<br /><br /> **向下**|
|逐一查看所有控制項。|**Tab**|
|反復查看所有控制項的反向。|**Shift** +**Tab**|
|刪除選取的控制項或控制項集。|**刪除**|
|複製選取的控制項。|**Ctrl** +**C**|
|剪下選取的控制項。|**Ctrl** +**X**|
|從剪貼簿貼上控制項。|**Ctrl** +**V**|
|選取 [ **工具箱**]。|**Ctrl** +**Alt** +**X**|
|選取父元件。|**Esc**|

 只適用于 Microsoft Office 功能表、和的鍵盤快速鍵，如下 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> 表所示。

|動作|鍵盤快速鍵|
|------------|-----------------------|
|如果下拉式面板已開啟，並已在下拉式面板上選取控制項，請選取父控制項。|**離開**|
|如果下拉式面板已開啟且已選取父控制項，請關閉下拉式面板。|**離開**|
|開啟下拉式面板。|**對**|
|如果下拉式面板已開啟，請選取下拉式面板上的第一個控制項。|**對**|
|關閉下拉式面板。|**Esc**|

## <a name="see-also"></a>另請參閱

- [功能區總覽](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [逐步解說：使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [如何：將功能區設計工具的功能區匯出至功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [在執行時間存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)
