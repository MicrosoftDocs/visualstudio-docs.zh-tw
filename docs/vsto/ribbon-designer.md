---
title: 功能區設計工具
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e1c2941b0c088a832540fd3380c993fe2c380b44
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985618"
---
# <a name="ribbon-designer"></a>功能區設計工具
  功能區設計工具是一種視覺化設計畫布。 使用功能區設計工具，將自訂索引標籤、群組和控制項加入至 Microsoft Office 應用程式的功能區。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 若要開啟功能區設計工具，請將 **[功能區（視覺化設計工具）** ] 專案加入至您的專案。 接著，您可以使用設計工具進行下列工作：

- [設計功能區版面配置](#DesigningRibbonLayout)

- [處理事件及設定控制項屬性](#HandleEventsSetProperties)

- [將控制項新增至 Backstage 檢視](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
> 您可以使用功能區設計工具來完成一些工作。 如需這些工作及如何完成這些工作的詳細資訊，請參閱[功能區總覽](../vsto/ribbon-overview.md)。

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>將 [功能區（視覺化設計工具）] 專案加入至專案
 若要使用功能區設計工具，請將新的 **[功能區（視覺化設計工具）** ] 專案加入至您的專案。 如需詳細資訊，請參閱[如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。

 當您加入新的 **[功能區（視覺化設計工具）** ] 專案時，Visual Studio 會自動將下列檔案加入至您的專案：

- 功能區程式碼檔案。 這個檔案具有您在 [**加入新專案**] 對話方塊中為 [**功能區（視覺化設計工具）** ] 專案指定的名稱。 加入程式碼來處理這個檔案的功能區事件。

- 功能區設計工具程式碼檔案。 這個檔案包含功能區設計工具所產生的程式碼，不應直接編輯。

- 資源檔。 這個檔案包含功能區上每個控制項的屬性值。

  如果您已經有另一個專案的 **[功能區（視覺化設計工具）** ] 專案，您可以使用 [**加入現有專案**] 對話方塊在目前的專案中重複使用它。

## <a name="DesigningRibbonLayout"></a>設計功能區
 有三種方式可以開啟功能區設計工具：

- 在**方案總管**中，按兩下功能區程式碼檔案。

- 在**方案總管**中，以滑鼠右鍵按一下功能區程式碼檔案，然後按一下 [**視圖設計**工具]。

- 在**方案總管**中，選取功能區程式碼檔案，然後按一下 [**視圖**] 功能表上的 [**設計**工具]。

  功能區設計工具組含預設的索引標籤和群組。 您可以從功能區設計工具中移除預設的索引標籤和群組。 若要移除預設群組，請以滑鼠右鍵按一下 [ **Group1**]，然後按一下 [**刪除**]。 若要移除預設索引標籤，請在設計介面的空白區域上按一下滑鼠右鍵，然後按一下 [**移除功能區**索引標籤]。

  您也可以將自訂索引標籤、群組和控制項加入至功能區設計工具。 您可以在 [**工具箱**] 的 [ **Office 功能區控制項**] 群組中找到這些控制項。 有三種方式可將控制項從 [ **Office 功能區控制項**] 群組加入功能區設計工具中：

- 將控制項拖曳至功能區設計工具上的適當區域。

- 按一下控制項，然後按一下功能區設計工具中的適當區域。

- 在設計工具中選取適當的區域，然後在 [**工具箱**] 中按兩下控制項。

### <a name="ribbon-design-workflow"></a>功能區設計工作流程
 請遵循下列基本步驟來設計功能區版面配置：

1. [將 [自訂] 索引標籤加入功能區](#AddTabToRibbon)。

2. [將群組加入至](#AddGroupsToTab)索引標籤。

3. [將控制項加入至群組](#AddControlsToGroups)。

   控制項只能放在群組上;您無法將控制項直接拖曳到索引標籤或功能區。 群組只能放在索引標籤上;您無法將群組直接拖曳至功能區。

   藉由將控制項拖曳至正確的位置來排列它們。 您可以使用 [**屬性**] 視窗來設定控制項的屬性。

   您無法將控制項從某個索引標籤拖曳到功能區上的另一個索引標籤。 如果您想要將控制項移至另一個索引標籤，則必須使用 [**剪**下] 命令從一個索引標籤中移除控制項，然後將控制項貼入另一個索引標籤。如果您剪下控制項並將它貼上，事件處理常式就會停止運作。 您可以在 [**屬性**] 視窗中重新連接事件處理常式。 如需詳細資訊，請參閱[屬性視窗](../ide/reference/properties-window.md)。

### <a name="AddTabToRibbon"></a>將自訂索引標籤加入功能區
 有三種方式可將自訂索引標籤加入功能區：

- 從 [**工具箱**] 新增索引標籤。

- 以滑鼠右鍵按一下功能區設計工具，然後按一下 [**加入功能區**索引標籤]。

- 開啟 [索引標籤**集合編輯器]** ，然後按一下 [**新增**]。

   若要開啟 [索引標籤**集合編輯器]** ，請在 [**屬性**] 視窗中選取 [索引標籤] 屬性，然後按一下省略號按鈕 [ ![ASP.NET Mobile 設計](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")工具] [橢圓形 **]** 。

  加入索引標籤之後，您可以加入群組以包含控制項。

#### <a name="remove-custom-tabs-from-the-ribbon"></a>從功能區移除自訂索引標籤
 有三種方式可從功能區移除自訂索引標籤：

- 以滑鼠右鍵按一下設計工具，然後按一下 [**移除功能區**索引標籤]。

- 在 [**屬性**] 視窗的 [**命令**] 窗格中，按一下 [**移除功能區**索引標籤]。

- 開啟 [索引標籤**集合編輯器**]，選取索引標籤，然後按一下 [**移除**]。

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>變更功能區上索引標籤的位置
 您可以變更功能區上的自訂索引標籤順序。 您也可以將自訂索引標籤放置在功能區上的內建索引標籤之前或之後。 如需詳細資訊，請參閱[如何：變更功能區上](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)索引標籤的位置。

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>自訂功能區上的內建索引標籤
 內建索引標籤是已在 Microsoft Office 應用程式功能區上的索引標籤。 例如，[**資料**] 索引標籤是 Excel 中的內建索引標籤。

 您可以將群組和控制項加入至內建索引標籤。根據預設，自訂群組會顯示為內建索引標籤上的最後一個群組，但您可以在索引標籤上的任何內建組之前或之後移動該群組。

 您無法移除內建組。

 如需如何自訂內建索引標籤的詳細資訊，請參閱[如何：自訂內建](../vsto/how-to-customize-a-built-in-tab.md)索引標籤。

### <a name="AddGroupsToTab"></a>將群組加入至索引標籤
 群組會以邏輯方式組織功能區上的控制項。 將群組加入至索引標籤。 將所有其他控制項加入至群組。

### <a name="AddControlsToGroups"></a>將控制項新增至群組
 將一個或多個控制項加入至群組。 下表描述每個控制項。

|控制項|描述|
|-------------|-----------------|
|**Box**|在群組中組織控制項的容器。 除了分隔符號、群組或索引標籤之外，您還可以將任何控制項新增到方塊中。方塊可以是水準或垂直。|
|**Button**|啟動動作的按鈕。 您可以將按鈕新增至群組、按鈕群組、下拉式清單、圖庫、功能表或分割按鈕。|
|**ButtonGroup**|包含一或多個按鈕、切換按鈕、功能表、分割按鈕和圖庫的群組。 您可以將按鈕群組新增至群組或功能表。|
|**CheckBox**|選取或清除以開啟或關閉選項的方塊。|
|**ComboBox**|已附加清單方塊的編輯方塊。 使用者可以輸入或選取其選擇。 此方塊會顯示目前的選取專案。 在將功能區載入至 Office 應用程式之前或之後，使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> 屬性在執行時間新增和移除專案。|
|**清單**|使用者可以選取的專案清單。 使用者無法在下拉式清單中輸入新專案。<br /><br /> 使用 [<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A>] 屬性可將專案新增至清單。 您可以在執行時間加入和移除專案。<br /><br /> 使用 [<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A>] 屬性，將按鈕新增至清單。 不過，將功能區載入至 Office 應用程式之後，您就無法在執行時間加入和移除按鈕。|
|**EditBox**|使用者可以在其中輸入文字的方塊。|
|**圖庫**|顯示使用者可以從中選取之視覺效果選擇的陣列或方格的功能表。 您可以在功能表中控制選取範圍的版面配置。 使用 [<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>] 和 [<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> 屬性]，即可指定將顯示資源庫之專案和按鈕的資料列和資料行數目。|
|**標籤**|可用於識別功能區上控制項的文字。|
|**Menu**|可以包含下列任何控制項的下拉式清單：<br /><br /> -按鈕<br />-核取方塊<br />-圖庫<br />-Menu<br />-分割按鈕<br />-切換按鈕<br />-分隔符號<br /><br /> 若要將控制項加入功能區設計工具中的功能表，請按一下功能表中的向下箭號，以公開功能表設計介面。 接著，您可以從 [**工具箱**] 將 [功能區控制項] 拖曳至功能表上。 若要排列控制項，請將它們拖曳到想要的位置。<br /><br /> 若要在功能區載入至 Office 應用程式之後，將控制項加入至 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>，您必須先將 [<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A>] 屬性設為 [ **true** ]，才能載入功能區。 如需如何執行此動作的詳細資訊，請參閱[功能區物件模型總覽](../vsto/ribbon-object-model-overview.md)。|
|**Separator**|用來分隔清單中專案的精簡條。 加入至群組時，橫條會垂直。 加入至功能表時，橫條是水準的。|
|**SplitButton**|已附加功能表的按鈕。 分割按鈕可以包含下列任何控制項：<br /><br /> -按鈕<br />-核取方塊<br />-圖庫<br />-Menu<br />-分割按鈕<br />-切換按鈕<br />-分隔符號<br /><br /> 就像功能表一樣，[分割] 按鈕有自己的設計介面。 不過，與功能表不同的是，您只能在將功能區載入至 Office 應用程式之前，先更新分割按鈕中的專案。 如需如何更新分割按鈕中專案的詳細資訊，請參閱[功能區物件模型總覽](../vsto/ribbon-object-model-overview.md)。|
|**按鈕**|顯示為按下或未按下的按鈕。|

## <a name="HandleEventsSetProperties"></a>處理事件及設定屬性
 功能區設計工具可讓您使用 [**屬性**] 視窗，在設計階段設定控制項屬性。 此外，功能區會公開強型別物件模型，供您在執行時間用來取得和設定功能區控制項的屬性。

 您可以按兩下設計工具上的任何控制項，開啟控制項預設事件的事件處理常式。 您可以使用 [**屬性**] 視窗來建立所有其他控制項事件的事件處理常式。

 功能區事件和屬性位於 <xref:Microsoft.Office.Tools.Ribbon> 命名空間中。 [**功能區（視覺化設計工具）** ] 專案會自動將參考加入至專案中的這個元件，並在功能區程式碼檔案的頂端插入適當的**using**或**Imports**語句。

 如需在執行時間處理功能區事件及設定功能區控制項屬性的詳細資訊，請參閱[功能區物件模型總覽](../vsto/ribbon-object-model-overview.md)。

## <a name="CustomizingMicrosoftOfficeButton"></a>自訂 Backstage 檢視
 當您按一下 [檔案] 索引標籤時，您可以使用功能區設計工具將控制項新增至**開啟的功能表**。此功能表稱為 Backstage view。

 您無法使用功能區設計工具，在內建控制項的前後放置控制項。 內建控制項是已出現在 Backstage 檢視中的控制項。 如果您想要在內建控制項之前或之後放置控制項，則必須使用功能區 XML。 如需有關**功能區（XML）** 的詳細資訊，請參閱[功能區 XML](../vsto/ribbon-xml.md)。 如需自訂 Backstage 檢視的詳細資訊，請參閱[適用于開發人員的 office 2010 backstage 視圖簡介](/previous-versions/office/developer/office-2010/ee691833(v=office.14))和[為開發人員自訂 office 2010 backstage 視圖](/previous-versions/office/developer/office-2010/ee815851(v=office.14))。

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 如需如何將控制項加入至 Backstage 檢視的詳細資訊，請參閱[如何：將控制項加入至 backstage 視圖](../vsto/how-to-add-controls-to-the-backstage-view.md)。

## <a name="Accessibility"></a>功能區設計工具中的協助工具
 您可以使用鍵盤快速鍵，在功能區設計工具中移動控制項。 某些鍵盤快速鍵適用于所有控制項，有些則只適用于具有功能表的控制項。

 下表顯示適用于所有控制項的鍵盤快速鍵。

|動作|鍵盤快速鍵|
|------------|-----------------------|
|將控制項移到清單中的上一個控制項之前。|**Ctrl**+**向上**<br /><br /> **Ctrl**+**Left**|
|將控制項移至清單中的下一個控制項之後。|**Ctrl**+**向下**<br /><br /> **Ctrl**+**Right**|
|將選取範圍從一個控制項移至相同群組中的另一個。 針對下拉式面板，在父控制項和下拉式面板中的控制項之間移動。|**設定**<br /><br /> **按住**|
|向前反復查看所有控制項。|**Tab**|
|逐一查看所有控制項的反向。|**Shift**+**Tab**|
|刪除選取的控制項或控制項集合。|**刪除**|
|複製選取的控制項。|**Ctrl**+**C**|
|剪下選取的控制項。|**Ctrl**+**X**|
|貼上剪貼簿中的控制項。|**Ctrl**+**V**|
|選取 [**工具箱**]。|**Ctrl**+**Alt**+**X**|
|選取 [父系] 元件。|**Esc**|

 下表顯示僅適用于 [Microsoft Office] 功能表、[<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>] 和 [<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>] 的鍵盤快速鍵。

|動作|鍵盤快速鍵|
|------------|-----------------------|
|如果下拉式面板已開啟，而且在下拉式面板上已選取控制項，請選取父控制項。|**左邊**|
|如果下拉式面板已開啟且已選取 [父控制項]，請關閉下拉式面板。|**左邊**|
|開啟下拉式面板。|**右邊**|
|如果下拉式面板已開啟，請選取下拉式面板上的第一個控制項。|**右邊**|
|關閉下拉式面板。|**Esc**|

## <a name="see-also"></a>請參閱

- [功能區總覽](../vsto/ribbon-overview.md)
- [功能區 XML](../vsto/ribbon-xml.md)
- [逐步解說：使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [如何：從功能區設計工具將功能區匯出至功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [在執行時間存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)
