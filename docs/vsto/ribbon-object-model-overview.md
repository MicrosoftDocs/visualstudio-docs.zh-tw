---
title: 功能區物件模型總覽
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6ca22704345fefb4944bda7dd9f71942fe8dfb50
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71256023"
---
# <a name="ribbon-object-model-overview"></a>功能區物件模型總覽
  會[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]公開強型別物件模型，您可以在執行時間用來取得和設定功能區控制項的屬性。 例如，您可以動態填入功能表控制項，或顯示和隱藏控制項內容。 您也可以將索引標籤、群組和控制項加入功能區中，但只有在 Office 應用程式載入功能區之前。 如需相關資訊，請參閱[設定變成隻讀的屬性](#SettingReadOnlyProperties)。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 這個功能區物件模型主要包含[功能區類別](#RibbonClass)、[功能區事件](#RibbonEvents)和[功能區控制項類別](#RibbonControlClasses)。

## <a name="RibbonClass"></a>功能區類別
 當您將新的 **[功能區（視覺化設計工具）** ] 專案加入至專案時，Visual Studio 會將**功能區**類別加入至您的專案。 **功能區**類別繼承自<xref:Microsoft.Office.Tools.Ribbon.RibbonBase>類別。

 這個類別會顯示為功能區程式碼檔案和功能區設計工具程式碼檔案之間分割的部分類別。

## <a name="RibbonEvents"></a>功能區事件
 **功能區**類別包含下列三個事件：

|Event - 事件|描述|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|當 Office 應用程式載入功能區自訂時引發。 <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>事件處理常式會自動加入至功能區程式碼檔案。 當功能區載入時，使用這個事件處理常式來執行自訂程式碼。|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|可讓您在功能區載入時快取功能區自訂中的影像。 如果您撰寫程式碼來快取這個事件處理常式中的功能區影像，可以獲得些許的效能提升。 如需詳細資訊，請參閱<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>。|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|當功能區實例關閉時引發。|

## <a name="RibbonControlClasses"></a>功能區控制項
 命名空間包含您在 [工具箱] 的 [ **Office 功能區控制項**] 群組中看到之每個控制項的類型。 <xref:Microsoft.Office.Tools.Ribbon>

 下表顯示每個`Ribbon`控制項的類型。 如需每個控制項的說明，請參閱[功能區總覽](../vsto/ribbon-overview.md)。

|控制項名稱|類別名稱|
|------------------|----------------|
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**DropDown**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**圖庫**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**群組**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Label**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Tab**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 命名空間會使用這些類型的「功能區」前置詞，以避免名稱與<xref:System.Windows.Forms>命名空間中的控制項類別名稱衝突。 <xref:Microsoft.Office.Tools.Ribbon>

 當您將控制項加入功能區設計工具時，功能區設計工具會將該控制項的類別宣告為功能區設計工具程式碼檔案中的欄位。

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>使用功能區控制項屬性的一般工作
 每`Ribbon`個控制項都包含屬性，可讓您用來執行各種工作，例如將標籤指派給控制項，或隱藏和顯示控制項。

 在某些情況下，屬性會在功能區載入之後，或在控制項加入至動態功能表之後變成隻讀狀態。 如需詳細資訊，請參閱[設定變成隻讀的屬性](#SettingReadOnlyProperties)。

 下表描述一些您可以使用`Ribbon`控制項屬性來執行的工作。

|這項工作：|請執行：|
|--------------------|--------------|
|隱藏或顯示控制項。|使用 Visible 屬性。|
|啟用或停用控制項。|使用 [已啟用] 屬性。|
|設定控制項的大小。|使用 ControlSize 屬性。|
|取得出現在控制項上的影像。|使用 Image 屬性。|
|變更控制項的標籤。|使用 [標籤] 屬性。|
|將使用者定義的資料加入至控制項。|使用 Tag 屬性。|
|取得<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>、 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>、或中的專案<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>ctrl.|使用 Items 屬性。|
|將專案加入至<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>、 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>或<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>控制項。|使用 Items 屬性。|
|將控制項加入至<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>。|使用 Items 屬性。<br /><br /> 若要在功能區<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>載入至 office 應用程式之後，將控制項加入至，您必須<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A>先將屬性設定為**true** ，才能將功能區載入至 office 應用程式。 如需相關資訊，請參閱[設定變成隻讀的屬性](#SettingReadOnlyProperties)。|
|取得選取的<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>專案，<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> 或 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|使用 SelectedItem 屬性。 若為<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> ，請使用屬性。 <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|取得上<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>的群組。|請使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> 屬性。|
|指定出現在中<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>的資料列和資料行數目。|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A>使用和<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>屬性。|

## <a name="SettingReadOnlyProperties"></a>設定變成隻讀的屬性
 有些屬性只能在功能區載入之前設定。 有三個地方可以設定這些屬性：

- 在 [Visual Studio**屬性**] 視窗中。

- 在**功能區**類別的函式中。

- 在專案的`ThisAddin`、 `ThisWorkbook`或`CreateRibbonExtensibilityObject` 類別`ThisDocument`的方法中。

  動態功能表提供一些例外狀況。 您可以建立新的控制項、設定其屬性，然後在執行時間將它們加入動態功能表，即使在載入包含功能表的功能區之後也一樣。

  您可以隨時設定加入至動態功能表的控制項屬性。

  如需詳細資訊，請參閱[變成隻讀的屬性](#ReadOnlyProperties)。

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>設定功能區的函式中的屬性
 您可以在**功能區**類別的`Ribbon`函式中設定控制項的屬性。 此程式碼必須在呼叫`InitializeComponent`方法之後出現。 下列範例會在目前時間為17:00 太平洋時間（UTC-8）或更新版本時，將新按鈕新增至群組。

 新增下列程式碼。

 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]

 在您C#從 Visual Studio 2008 升級的 Visual 專案中，此函式會出現在功能區程式碼檔案中。

 在 Visual Basic 專案中，或在C#您于中[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]建立的 Visual 專案中，此函式會出現在功能區設計工具程式碼檔中。 這個檔案的名稱是*YourRibbonItem*。Designer.cs 或*YourRibbonItem*。設計工具 .vb。 若要在 Visual Basic 專案中查看這個檔案，您必須先按一下方案總管中的 [**顯示所有**檔案] 按鈕。

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>在 CreateRibbonExtensibilityObject 方法中設定屬性
 當您在專案的`Ribbon` `ThisAddin` `CreateRibbonExtensibilityObject` 、 `ThisWorkbook`或類別中覆寫方法時，可以設定控制項的屬性。`ThisDocument` 如需`CreateRibbonExtensibilityObject`方法的詳細資訊，請參閱[功能區總覽](../vsto/ribbon-overview.md)。

 下列範例會在 Excel 活頁簿專案`CreateRibbonExtensibilityObject`之`ThisWorkbook`類別的方法中設定功能區屬性。

 新增下列程式碼。

 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]

### <a name="ReadOnlyProperties"></a>變成隻讀的屬性
 下表顯示只能在功能區載入之前設定的屬性。

> [!NOTE]
> 您可以隨時在動態功能表上設定控制項的屬性。 在此情況下，此資料表不適用。

|屬性|功能區控制項類別|
|--------------|--------------------------|
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**效果**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**部門**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**名稱**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|
|**移動**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**RowCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**索引標籤**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**標題**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>設定出現在 Outlook 偵測器中之功能區的屬性
 每次使用者開啟會在其中出現功能區的偵測器時，就會建立新的功能區實例。 不過，您只能在建立功能區的第一個實例之前，設定上清單格中所列的屬性。 在建立第一個實例之後，這些屬性會變成隻讀，因為第一個實例會定義 Outlook 用來載入功能區的 XML 檔案。

 如果您的條件式邏輯會在建立功能區的其他實例時，將任何這些屬性設定為不同的值，則此程式碼不會有任何作用。

> [!NOTE]
> 請確定已針對您新增至 Outlook 功能區的每個控制項，設定 [**名稱**] 屬性。 如果您在執行時間將控制項加入 Outlook 功能區，則必須在程式碼中設定這個屬性。 如果您在設計階段將控制項加入 Outlook 功能區，則會自動設定 [名稱] 屬性。

## <a name="ribbon-control-events"></a>功能區控制項事件
 每個控制項類別都包含一或多個事件。 下表描述這些事件。

|Event - 事件|描述|
|-----------|-----------------|
|按一下|發生于按一下控制項時。|
|TextChanged|發生于編輯方塊或下拉式方塊的文字變更時。|
|ItemsLoading|發生于 Office 要求控制項的 Items 集合時。 Office 會快取專案集合，直到您的程式碼變更控制項的屬性，或呼叫<xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A>方法為止。|
|ButtonClick|發生于按一下<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>或<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>中的按鈕時。|
|SelectionChanged|發生于<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>或<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>中的選取專案變更時。|
|DialogLauncherClick|發生于按一下群組右下角的對話方塊啟動器圖示時。|

 這些事件的事件處理常式有下列兩個參數。

|參數|描述|
|---------------|-----------------|
|*sender*|<xref:System.Object> ，表示引發事件的控制項。|
|*e*|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> 包含<xref:Microsoft.Office.Core.IRibbonControl>的。 使用此控制項來存取所提供[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]的功能區物件模型中未提供的任何屬性。|

## <a name="see-also"></a>另請參閱
- [在執行時間存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)
- [功能區總覽](../vsto/ribbon-overview.md)
- [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [功能區設計工具](../vsto/ribbon-designer.md)
- [逐步解說：使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [逐步解說：在執行時間更新功能區上的控制項](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [自訂 Outlook 的功能區](../vsto/customizing-a-ribbon-for-outlook.md)
- [如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)
- [如何：將控制項新增至 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [如何：從功能區設計工具將功能區匯出至功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [如何：顯示增益集使用者介面錯誤](../vsto/how-to-show-add-in-user-interface-errors.md)
