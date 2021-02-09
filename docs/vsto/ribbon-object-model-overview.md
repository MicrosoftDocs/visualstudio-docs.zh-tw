---
title: 功能區物件模型總覽
description: 瞭解 Visual Studio Tools for Office 執行時間如何公開強型別物件模型，您可以在執行時間用來取得和設定功能區控制項的屬性。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6306b13cc40d8b93de734168fe1e6df92c256d21
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888689"
---
# <a name="ribbon-object-model-overview"></a>功能區物件模型總覽
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]會公開強型別物件模型，您可以在執行時間用來取得和設定功能區控制項的屬性。 例如，您可以動態填入功能表控制項，或顯示和隱藏內容控制項。 您也可以將索引標籤、群組和控制項加入至功能區，但只有在 Office 應用程式載入功能區之前。 如需詳細資訊，請參閱 [設定變成隻讀的屬性](#SettingReadOnlyProperties)。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 這個功能區物件模型主要是由 [功能區類別](#RibbonClass)、 [功能區事件](#RibbonEvents)和 [功能區控制項類別](#RibbonControlClasses)所組成。

## <a name="ribbon-class"></a><a name="RibbonClass"></a> 功能區類別
 當您將新的 **功能區 (視覺化設計工具)** 專案加入至專案時，Visual Studio 會將 **功能區** 類別加入至專案。 **功能區** 類別繼承自 <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> 類別。

 這個類別會以部分類別的形式出現在功能區程式碼檔和功能區設計工具程式碼檔案中。

## <a name="ribbon-events"></a><a name="RibbonEvents"></a> 功能區事件
 **功能區** 類別包含下列三個事件：

|事件|描述|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|在 Office 應用程式載入功能區自訂時引發。 <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>事件處理常式會自動加入至功能區程式碼檔案。 您可以使用這個事件處理常式，在功能區載入時執行自訂程式碼。|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|可讓您在功能區載入時，快取功能區自訂中的影像。 如果您撰寫程式碼來快取此事件處理常式中的功能區影像，您可能會獲得輕微的效能提升。 如需詳細資訊，請參閱<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>。|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|在功能區實例關閉時引發。|

## <a name="ribbon-controls"></a><a name="RibbonControlClasses"></a> 功能區控制項
 <xref:Microsoft.Office.Tools.Ribbon>命名空間包含您在 [**工具箱**] 的 [ **Office 功能區控制項**] 群組中看到之每個控制項的類型。

 下表顯示每個控制項的類型 `Ribbon` 。 如需每個控制項的描述，請參閱 [功能區總覽](../vsto/ribbon-overview.md)。

|控制項名稱|類別名稱|
|------------------|----------------|
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**按鈕**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**拉**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**編輯方塊**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**主機庫**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**群組**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**標籤**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**功能表**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Tab**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 <xref:Microsoft.Office.Tools.Ribbon>命名空間會針對這些類型使用 "功能區" 前置詞，以避免名稱與命名空間中的控制項類別名稱衝突 <xref:System.Windows.Forms> 。

 當您將控制項加入至功能區設計工具時，功能區設計工具會將該控制項的類別宣告為功能區設計工具程式碼檔案中的欄位。

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>使用功能區控制項屬性的一般工作
 每個 `Ribbon` 控制項都包含屬性，可讓您用來執行各種工作，例如將標籤指派給控制項，或隱藏和顯示控制項。

 在某些情況下，屬性會在功能區載入之後，或在控制項加入至動態功能表之後變成隻讀。 如需詳細資訊，請參閱 [設定變成隻讀的屬性](#SettingReadOnlyProperties)。

 下表描述您可以使用控制項屬性執行的一些工作 `Ribbon` 。

|這項工作：|執行此動作：|
|--------------------|--------------|
|隱藏或顯示控制項。|使用 Visible 屬性。|
|啟用或停用控制項。|使用 Enabled 屬性。|
|設定控制項的大小。|使用 ControlSize 屬性。|
|取得顯示在控制項上的影像。|使用 Image 屬性。|
|變更控制項的標籤。|使用標籤屬性。|
|將使用者自訂資料新增至控制項。|使用 Tag 屬性。|
|取得 <xref:Microsoft.Office.Tools.Ribbon.RibbonBox> 、 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> 、 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 或中的專案<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> 控制。|使用 Items 屬性。|
|將專案加入至 <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> 、 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> 或 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 控制項。|使用 Items 屬性。|
|將控制項加入至 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> 。|使用 Items 屬性。<br /><br /> 若要在 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> 功能區載入至 office 應用程式之後將控制項加入至，您必須 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> 先將屬性設定為 **true** ，才能將功能區載入至 office 應用程式。 如需詳細資訊，請參閱 [設定變成隻讀的屬性](#SettingReadOnlyProperties)。|
|取得選取的專案 <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> ，<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>、或 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 。|使用 SelectedItem 屬性。 若為 <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> ，請使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> 屬性。|
|取得上的群組 <xref:Microsoft.Office.Tools.Ribbon.RibbonTab> 。|請使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> 屬性。|
|指定出現在中的資料列和資料行數目 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 。|使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> 和 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> 屬性。|

## <a name="set-properties-that-become-read-only"></a><a name="SettingReadOnlyProperties"></a> 設定變成隻讀的屬性
 某些屬性只能在功能區載入之前設定。 有三個地方可以設定這些屬性：

- 在 [Visual Studio **屬性** ] 視窗中。

- 在 **功能區** 類別的函式中。

- 在 `CreateRibbonExtensibilityObject` `ThisAddin` 專案的、 `ThisWorkbook` 或類別的方法中 `ThisDocument` 。

  動態功能表提供一些例外狀況。 您可以建立新的控制項、設定其屬性，然後在執行時間將它們加入至動態功能表，即使在載入包含功能表的功能區之後也是如此。

  您可以隨時設定新增至動態功能表的控制項屬性。

  如需詳細資訊，請參閱 [變成隻讀的屬性](#ReadOnlyProperties)。

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>在功能區的函式中設定屬性
 您可以 `Ribbon` 在 **功能區** 類別的函式中，設定控制項的屬性。 這個程式碼必須出現在呼叫方法之後 `InitializeComponent` 。 下列範例會將新按鈕新增至群組，如果目前時間是17:00 太平洋時間 (UTC-8) 或更新版本。

 加入下列程式碼。

 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]

 在您從 Visual Studio 2008 升級的 Visual c # 專案中，此函式會出現在功能區程式碼檔案中。

 在 Visual Basic 專案或您在中建立的 Visual c # 專案中 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] ，此函式會出現在功能區設計工具程式碼檔案中。 這個檔案的名稱是 *yourribbonitem.designer.vb*。Designer.cs 或 *yourribbonitem.designer.vb*。設計工具 .vb。 若要在 Visual Basic 專案中查看此檔案，您必須先按一下方案總管中的 [ **顯示所有** 檔案] 按鈕。

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>在 CreateRibbonExtensibilityObject 方法中設定屬性
 `Ribbon`當您在 `CreateRibbonExtensibilityObject` 專案的 `ThisAddin` 、 `ThisWorkbook` 或類別中覆寫方法時，您可以設定控制項的屬性 `ThisDocument` 。 如需此方法的詳細資訊 `CreateRibbonExtensibilityObject` ，請參閱 [功能區總覽](../vsto/ribbon-overview.md)。

 下列範例會在 `CreateRibbonExtensibilityObject` Excel 活頁簿專案類別的方法中設定功能區屬性 `ThisWorkbook` 。

 加入下列程式碼。

 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]

### <a name="properties-that-become-read-only"></a><a name="ReadOnlyProperties"></a> 變成隻讀的屬性
 下表顯示只能在功能區載入之前設定的屬性。

> [!NOTE]
> 您可以隨時在動態功能表上設定控制項的屬性。 在該情況下，此資料表並不適用。

|屬性|功能區控制項類別|
|--------------|--------------------------|
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**動態**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**全球**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**群組**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**名稱**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|
|**位置**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**計數**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**索引標籤**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**標題**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>設定出現在 Outlook 檢查器中的功能區屬性
 每次使用者開啟顯示功能區的偵測器時，就會建立新的功能區實例。 不過，您只能在建立功能區的第一個實例之前，設定上表中列出的屬性。 第一個實例建立之後，這些屬性會變成隻讀，因為第一個實例定義了 Outlook 用來載入功能區的 XML 檔案。

 如果您有條件式邏輯，可在建立功能區的其他實例時，將這些屬性設定為不同的值，則此程式碼將不會有任何作用。

> [!NOTE]
> 確定您加入至 Outlook 功能區的每個控制項都已設定 [ **名稱** ] 屬性。 如果您在執行時間將控制項加入 Outlook 功能區，則必須在程式碼中設定這個屬性。 如果您在設計階段將控制項加入 Outlook 功能區，則會自動設定 [名稱] 屬性。

## <a name="ribbon-control-events"></a>功能區控制項事件
 每個控制項類別都包含一或多個事件。 下表將說明這些事件。

|事件|描述|
|-----------|-----------------|
|按一下|發生于按一下控制項時。|
|TextChanged|發生于編輯方塊或下拉式方塊的文字變更時。|
|ItemsLoading|當 Office 要求控制項的專案集合時發生。 Office 會快取專案集合，直到您的程式碼變更控制項的屬性，或呼叫 <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> 方法。|
|>buttonclick|當按一下或中的按鈕 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 時發生 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> 。|
|SelectionChanged|在或中的選取範圍 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 變更時發生。|
|DialogLauncherClick|發生于按一下群組右下角的對話啟動器圖示時。|

 這些事件的事件處理常式有下列兩個參數。

|參數|Description|
|---------------|-----------------|
|*發送*|<xref:System.Object>，表示引發事件的控制項。|
|*pci-e*|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs>，其包含 <xref:Microsoft.Office.Core.IRibbonControl>。 您可以使用這個控制項來存取所提供的功能區物件模型中無法使用的任何屬性 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 。|

## <a name="see-also"></a>另請參閱
- [在執行時間存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)
- [功能區總覽](../vsto/ribbon-overview.md)
- [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [功能區設計工具](../vsto/ribbon-designer.md)
- [逐步解說：使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [逐步解說：在執行時間更新功能區上的控制項](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [自訂 Outlook 的功能區](../vsto/customizing-a-ribbon-for-outlook.md)
- [如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)
- [如何：將控制項加入至 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [如何：將功能區設計工具的功能區匯出至功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [如何：顯示增益集使用者介面錯誤](../vsto/how-to-show-add-in-user-interface-errors.md)
