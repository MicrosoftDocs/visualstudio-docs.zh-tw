---
title: 功能區設計工具
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8cb8df33c89ce044572508918ba48edae2a6d75e
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693340"
---
# <a name="ribbon-designer"></a>功能區設計工具
  功能區設計工具是視覺效果設計畫布。 若要將自訂索引標籤、 群組和控制項加入 Microsoft Office 應用程式的功能區中使用功能區設計工具。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 若要開啟功能區設計工具，加入**功能區 （視覺化設計工具）** 至您的專案項目。 您接著可以使用設計工具進行下列工作：  
  
-   [設計功能區配置](#DesigningRibbonLayout)  
  
-   [處理事件，並設定控制項屬性](#HandleEventsSetProperties)  
  
-   [將控制項加入 Backstage 檢視](#CustomizingMicrosoftOfficeButton)  
  
> [!NOTE]  
>  有一些您無法使用功能區設計工具完成的工作。 如需這些工作和完成它們的詳細資訊，請參閱[功能區概觀](../vsto/ribbon-overview.md)。  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")相關的影片示範，請參閱[如何 i： 使用功能區設計工具自訂 Outlook 功能區？](http://go.microsoft.com/fwlink/?LinkID=130312)。  
  
## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>將功能區 （視覺化設計工具） 項目加入至專案  
 若要使用功能區設計工具，加入新**功能區 （視覺化設計工具）** 至您的專案項目。 如需詳細資訊，請參閱[How to： 開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
 當您新增新**功能區 （視覺化設計工具）** 項目、 Visual Studio 會自動將下列檔案加入您的專案：  
  
-   功能區程式碼檔案。 此檔案具有您指定的名稱**功能區 （視覺化設計工具）** 中的項目**加入新項目** 對話方塊。 加入程式碼以處理功能區事件，此檔案。  
  
-   功能區設計工具程式碼檔案。 這個檔案包含功能區設計工具所產生的程式碼，且不應直接編輯。  
  
-   資源檔。 此檔案包含功能區上的每個控制項的屬性值。  
  
 如果您已經有**功能區 （視覺化設計工具）** 項目從另一個專案，您可以重複使用它在目前專案中使用**加入現有項目** 對話方塊。  
  
##  <a name="DesigningRibbonLayout"></a> 設計功能區  
 有三種方式可開啟功能區設計工具：  
  
-   在**方案總管 中**，按兩下功能區程式碼檔案。  
  
-   在**方案總管 中**，以滑鼠右鍵按一下功能區程式碼檔案，然後按一下**檢視表設計工具**。  
  
-   在**方案總管] 中**選取功能區程式碼檔案，然後按一下 [**設計師**上**檢視**功能表。  
  
 功能區設計工具會包含預設索引標籤和群組。 您可以從功能區設計工具中移除預設索引標籤和群組。 若要移除預設的群組，以滑鼠右鍵按一下**Group1**，然後按一下 **刪除**。 若要移除預設索引標籤，以滑鼠右鍵按一下設計介面上的空白區域，然後按一下 **移除的功能區索引標籤**。  
  
 您也可以將自訂索引標籤、 群組和控制項加入至功能區設計工具。 您可以找到這些控制項在**工具箱**，請在**Office 功能區控制項**群組。 有三種方式將控制項從**Office 功能區控制項**群組加入功能區設計工具：  
  
-   將控制項拖曳至適當的區域中，功能區設計工具上。  
  
-   按一下控制項，然後按一下 功能區設計工具中適當的區域。  
  
-   在設計師中，選取適當的區域，然後按兩下 中的控制項**工具箱**。  
  
### <a name="ribbon-design-workflow"></a>功能區設計工作流程  
 請遵循以下基本步驟來設計功能區配置：  
  
1.  [將自訂索引標籤加入至功能區](#AddTabToRibbon)。  
  
2.  [索引標籤加入群組](#AddGroupsToTab)。  
  
3.  [將控制項新增至群組](#AddControlsToGroups)。  
  
 只有在群組; 上控制項可以卸除無法將拖曳控制項直接加入索引標籤或功能區。 只有在索引標籤; 上卸除群組您無法將群組拖曳至功能區直接。  
  
 排列控制項拖曳到正確的位置。 您可以設定控制項的屬性使用**屬性**視窗。  
  
 您無法將拖曳控制項從某個索引標籤之間在功能區上。 如果您想要將控制項移到另一個索引標籤，您必須使用**剪下**命令以移除控制項從某個索引標籤，並貼上另一個索引標籤的控制項。如果您執行剪下的控制項，並將它貼入，事件處理常式會停止運作。 您可以重新連線中的事件處理常式**屬性**視窗。 如需詳細資訊，請參閱[屬性 視窗](/visualstudio/ide/reference/properties-window)。  
  
###  <a name="AddTabToRibbon"></a> 加入自訂索引標籤加入功能區  
 有三種方式可將自訂索引標籤加入至功能區：  
  
-   加入索引標籤上，從**工具箱**。  
  
-   功能區設計工具中，以滑鼠右鍵按一下，然後按一下 **加入功能區索引標籤**。  
  
-   開啟**索引標籤集合編輯器**，然後按一下 **新增**。  
  
     若要開啟**索引標籤集合編輯器**，請在**屬性**視窗中，選取**索引標籤**屬性，然後按一下省略符號按鈕![ASP.NET Mobile設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")。  
  
 加入索引標籤之後，您可以加入群組，包含控制項。  
  
#### <a name="remove-custom-tabs-from-the-ribbon"></a>從功能區中移除自訂索引標籤  
 有三種方式可移除自訂索引標籤，從功能區：  
  
-   設計工具中，以滑鼠右鍵按一下，然後按一下 **移除的功能區索引標籤**。  
  
-   在**命令**窗格**屬性**視窗中，按一下 **移除的功能區索引標籤**。  
  
-   開啟**索引標籤集合編輯器**選取索引標籤，然後按一下 **移除**。  
  
#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>變更功能區上的索引標籤的位置  
 您可以變更自訂功能區上的索引標籤的順序。 之前或之後在功能區上的內建索引標籤，您也可以將自訂索引標籤。 如需詳細資訊，請參閱[如何： 變更功能區上的索引標籤的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)。  
  
#### <a name="customize-built-in-tabs-on-the-ribbon"></a>自訂功能區上的內建索引標籤  
 內建索引標籤是已在 Microsoft Office 應用程式的功能區的索引標籤。 例如，**資料** 索引標籤是在 Excel 中的內建索引標籤。  
  
 您可在內建索引標籤加入群組和控制項。根據預設，自訂群組會顯示為最後一個群組內建索引標籤上，雖然您可以移動它任何內建群組之前或之後的索引標籤上。  
  
 您無法移除內建群組。  
  
 如需有關如何自訂內建索引標籤的詳細資訊，請參閱[How to： 自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)。  
  
###  <a name="AddGroupsToTab"></a> 索引標籤加入群組  
 以邏輯方式群組可組織功能區上的控制項。 將群組加入至索引標籤。 加入群組中的所有其他控制項。  
  
###  <a name="AddControlsToGroups"></a> 將控制項新增至群組  
 將一或多個控制項加入至群組。 下表描述每個控制項。  
  
|控制項|描述|  
|-------------|-----------------|  
|**方塊**|組織的群組中的控制項容器。 您可以加入任何控制項，除了分隔符號、 群組或索引標籤中。方塊可以水平或垂直。|  
|**Button**|啟動動作的按鈕。 您可以將按鈕加入群組、 按鈕群組中，下拉式清單、 組件庫、 功能表上或分割按鈕。|  
|**ButtonGroup**|包含一或多個按鈕，切換按鈕、 功能表、 分割按鈕和組件庫的群組。 您可以加入群組或功能表按鈕群組。|  
|**CheckBox**|方塊，選取或清除，以開啟或關閉選項。|  
|**ComboBox**|編輯方塊與清單方塊。 使用者可以輸入或選取其選項。 方塊會顯示目前選取範圍。 使用<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A>新增和移除項目在執行階段之前或之後在功能區載入至 Office 應用程式的屬性。|  
|**下拉式清單**|使用者可以選取的項目清單。 使用者無法在下拉式清單中輸入新的項目。<br /><br /> 使用<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A>項目加入清單的屬性。 您可以加入和移除項目在執行階段。<br /><br /> 使用<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A>將按鈕加入清單的屬性。 不過，您無法在加入和移除按鈕功能區載入至 Office 應用程式之後，執行階段。|  
|**編輯方塊**|方塊，使用者可以在其中輸入文字。|  
|**圖庫**|功能表呈現的陣列或方格的視覺化使用者可以從中選取的選項。 您可以控制配置的功能表中選取項目。 使用<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>和<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A>屬性，以指定的資料列和資料行，會顯示項目數目和按鈕的組件庫。|  
|**Label**|您可以使用它來識別功能區上的控制項的文字。|  
|**Menu**|下拉式清單可包含下列控制項：<br /><br /> 按鈕<br />核取方塊<br />-組件庫<br />功能表<br />分割按鈕<br />切換按鈕<br />分隔<br /><br /> 若要將控制項加入的功能表功能區設計工具中，按一下功能表設計介面會公開在功能表中的向下箭頭。 然後，您可以將從功能區控制項**工具箱**到功能表。 若要排列控制項，請將它們拖曳到所要的位置。<br /><br /> 若要將控制項加入<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>區載入至 Office 應用程式之後，您必須設定<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A>屬性**true**區載入之前。 如需如何執行這項操作資訊，請參閱[功能區物件模型概觀](../vsto/ribbon-object-model-overview.md)。|  
|**Separator**|細長條，用來分隔清單中的項目。 新增至群組時，軸是垂直。 加入至功能表時，軸是水平。|  
|**SplitButton**|附有功能表按鈕。 分割按鈕可以包含下列控制項：<br /><br /> 按鈕<br />核取方塊<br />-組件庫<br />功能表<br />分割按鈕<br />切換按鈕<br />分隔<br /><br /> 功能表上，例如分割按鈕會有它自己的設計介面。 不過，不同於功能表上，您只能更新分割按鈕中的項目功能區載入至 Office 應用程式前。 如需如何更新分割按鈕中的項目資訊，請參閱[功能區物件模型概觀](../vsto/ribbon-object-model-overview.md)。|  
|**ToggleButton**|按鈕，按下還是未按下。|  
  
##  <a name="HandleEventsSetProperties"></a> 處理事件，並設定屬性  
 功能區設計工具可讓您在設計階段設定控制項屬性，使用**屬性**視窗。 此外，功能區公開強類型的物件模型可讓您取得和設定在執行階段的功能區控制項的屬性。  
  
 您可以按兩下以開啟控制項的預設事件的事件處理常式設計工具上的任何控制項。 您可以使用來建立所有其他的控制項事件的事件處理常式**屬性**視窗。  
  
 功能區事件和屬性皆位於<xref:Microsoft.Office.Tools.Ribbon>命名空間。 **功能區 （視覺化設計工具）** 項目會自動將此組件的參考加入專案中，並且插入適當**使用**或**匯入**上方的陳述式功能區程式碼檔案。  
  
 如需處理功能區事件，並在執行階段設定的功能區控制項的屬性資訊，請參閱[功能區物件模型概觀](../vsto/ribbon-object-model-overview.md)。  
  
##  <a name="CustomizingMicrosoftOfficeButton"></a> 自訂 Backstage 檢視  
 您可以使用功能區設計工具將控制項加入後按一下開啟功能表**檔案** 索引標籤。這個功能表會呼叫 Backstage 檢視。  
  
 您無法使用功能區設計工具內建控制項的前後放置控制項。 內建控制項是已經出現在 Backstage 檢視的控制項。 如果您想要調整控制項的位置之前或內建控制項之後，您必須使用功能區 XML。 如需有關**功能區 (XML)**，請參閱[功能區 XML](../vsto/ribbon-xml.md)。 如需自訂 Backstage 檢視的詳細資訊，請參閱[開發人員的 Office 2010 Backstage 檢視簡介](http://go.microsoft.com/fwlink/?LinkId=182189)和[自訂開發人員的 Office 2010 Backstage 檢視](http://go.microsoft.com/fwlink/?LinkId=182188)。  
  
 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]  
  
 如需如何將控制項加入 Backstage 檢視資訊，請參閱[How to： 將控制項加入 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)。  
  
##  <a name="Accessibility"></a> 功能區設計工具中的協助工具  
 您可以使用鍵盤快速鍵，在功能區設計工具中移動控制項。 某些鍵盤快速鍵適用於所有控制項，而且某些僅適用於具有功能表的控制項。  
  
 下表中，會顯示適用於所有控制項的鍵盤快速鍵。  
  
|動作|鍵盤快速鍵|  
|------------|-----------------------|  
|您可以將前一個控制項的控制項清單中。|**Ctrl**+**向上**<br /><br /> **Ctrl**+**左**|  
|在清單中的下一個控制項後移動控制項。|**Ctrl**+**向下**<br /><br /> **Ctrl**+**權限**|  
|將選取項目從一個控制項移到相同群組中的另一個。 下拉式面板，將父控制項和下拉式面板中的控制項之間移動。|**向上**<br /><br /> **向下**|  
|逐一查看轉寄所有控制項。|**Tab**|  
|逐一查看所有控制項反向。|**Shift**+**Tab**|  
|刪除選取的控制項或一組控制項。|**刪除**|  
|複製選取的控制項。|**Ctrl**+**C**|  
|剪下選取的控制項。|**Ctrl**+**X**|  
|貼上剪貼簿中的控制項。|**Ctrl**+**V**|  
|選取**工具箱**。|**Ctrl**+**Alt**+**X**|  
|選取父元件。|**Esc**|  
  
 僅適用於 Microsoft Office 功能表的鍵盤快速鍵<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>，和<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>下表所示。  
  
|動作|鍵盤快速鍵|  
|------------|-----------------------|  
|如果下拉式面板為開啟，且沒有下拉式面板上選取了控制項，請選取父控制項。|**左邊**|  
|如果下拉式面板為開啟，且已選取父控制項，請關閉下拉式面板。|**左邊**|  
|開啟下拉式面板。|**右邊**|  
|如果是開啟的下拉式面板，請選取下拉式面板上的第一個控制項。|**右邊**|  
|關閉下拉式面板。|**Esc**|  
  
## <a name="see-also"></a>另請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [功能區 XML](../vsto/ribbon-xml.md)   
 [逐步解說： 使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [如何： 將功能區設計工具功能區匯出至功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [如何： 開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [存取在執行階段的功能區](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  