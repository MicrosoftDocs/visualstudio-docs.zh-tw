---
title: 功能區物件模型概觀
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e8c0e18146361cfbe89433d79962afcb89de3061
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961305"
---
# <a name="ribbon-object-model-overview"></a>功能區物件模型概觀
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]會公開強類型的物件模型，您可以使用它來取得和設定在執行階段的功能區控制項的屬性。 例如，您可以動態填入功能表控制項，或顯示和隱藏控制項內容。 您也可以新增索引標籤、 群組和控制項的功能區中，但只在 Office 應用程式載入功能區之前。 如需資訊，請參閱[設定會變成唯讀的屬性](#SettingReadOnlyProperties)。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 此功能區物件模型包含主要[功能區類別](#RibbonClass)，[功能區事件](#RibbonEvents)，並[功能區控制項類別](#RibbonControlClasses)。  
  
##  <a name="RibbonClass"></a> 功能區類別  
 當您將加入新**功能區 （視覺化設計工具）** 項目加入專案，Visual Studio 會加入**功能區**類別，以您的專案。 **功能區**類別繼承自<xref:Microsoft.Office.Tools.Ribbon.RibbonBase>類別。  
  
 這個類別會顯示為功能區程式碼檔案和功能區設計工具程式碼檔案分割成部分類別。  
  
##  <a name="RibbonEvents"></a> 功能區事件  
 **功能區**類別包含下列三個事件：  
  
|Event - 事件|描述|  
|-----------|-----------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Office 應用程式載入功能區自訂時引發。 <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>事件處理常式會自動加入至功能區程式碼檔案。 功能區載入時執行自訂程式碼中使用這個事件處理常式。|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|可讓您快取映像，在功能區自訂功能區載入時。 如果您撰寫程式碼快取功能區中的映像這個事件處理常式，您可以取得輕微的效能提升。 如需詳細資訊，請參閱<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>。|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|當功能區執行個體關閉時引發。|  
  
##  <a name="RibbonControlClasses"></a> 功能區控制項  
 <xref:Microsoft.Office.Tools.Ribbon>命名空間包含您在中看到每個控制項的型別**Office 功能區控制項**群組**工具箱**。  
  
 下表顯示的類型，每個`Ribbon`控制項。 如需每個控制項的說明，請參閱 <<c0> [ 功能區概觀](../vsto/ribbon-overview.md)。  
  
|控制項名稱|類別名稱|  
|------------------|----------------|  
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**下拉式清單中**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**編輯方塊**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**圖庫**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**群組**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Label**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Tab**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 <xref:Microsoft.Office.Tools.Ribbon>命名空間以避免名稱衝突名稱的控制項類別中使用這些類型的 「 功能區 」 前置詞<xref:System.Windows.Forms>命名空間。  
  
 當您將控制項加入功能區設計工具時，功能區設計工具會將該控制項的類別宣告為功能區設計工具程式碼檔案中的欄位。  
  
### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>使用功能區控制項的屬性的一般工作  
 每個`Ribbon`控制項包含可用來執行各種工作，例如將標籤指派至控制項，或隱藏與顯示控制項的屬性。  
  
 在某些情況下，屬性會變成唯讀之後在功能區載入，或動態功能表中加入一個控制項之後。 如需詳細資訊，請參閱 <<c0> [ 設定會變成唯讀的屬性](#SettingReadOnlyProperties)。  
  
 下表描述一些您可以使用執行的工作`Ribbon`控制屬性。  
  
|這項工作：|請執行：|  
|--------------------|--------------|  
|隱藏或顯示控制項。|使用可見的屬性。|  
|啟用或停用的控制項。|使用 [啟用] 屬性。|  
|設定控制項的大小。|使用 ControlSize; 屬性。|  
|取得控制項顯示的影像。|使用 [影像] 屬性。|  
|變更控制項的標籤。|使用標籤屬性。|  
|將使用者定義的資料加入控制項。|使用 Tag 屬性。|  
|取得中的項目<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>， <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>， <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>，或<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> 控制項。|使用項目屬性。|  
|將項目加入<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>， <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>，或<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>控制項。|使用項目屬性。|  
|將控制項加入<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>。|使用項目屬性。<br /><br /> 若要將控制項加入<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>功能區載入至 Office 應用程式之後，您必須設定<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A>屬性設 **，則為 true**區載入至 Office 應用程式之前。 如需資訊，請參閱[設定會變成唯讀的屬性](#SettingReadOnlyProperties)。|  
|取得選取的項目<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>，<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> 或 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|使用 SelectedItem 屬性。 針對<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>，使用<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A>屬性。|  
|取得群組<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>。|請使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> 屬性。|  
|指定的資料列和資料行中出現數<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>。|使用<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A>和<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>屬性。|  
  
##  <a name="SettingReadOnlyProperties"></a> 設定會變成唯讀的屬性  
 功能區載入之前，只可以設定某些屬性。 有三個地方可以設定這些屬性：  
  
- 在 Visual Studio**屬性**視窗。  
  
- 中的建構函式**功能區**類別。  
  
- 在 `CreateRibbonExtensibilityObject`方法`ThisAddin`， `ThisWorkbook`，或`ThisDocument`您專案的類別。  
  
  動態功能表提供了一些例外狀況。 您可以建立新的控制項，設定其屬性，然後將它們新增至動態功能表在執行階段，即使在包含的功能表功能區載入。  
  
  您將新增至動態功能表的控制項的屬性可以設定在任何時間。  
  
  如需詳細資訊，請參閱 <<c0> [ 變成唯讀的屬性](#ReadOnlyProperties)。  
  
### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>在功能區的建構函式中設定屬性  
 您可以設定的屬性`Ribbon`建構函式中的控制項**功能區**類別。 此程式碼必須在呼叫之後出現`InitializeComponent`方法。 下列範例會新增到群組的新按鈕如果目前的時間為 17:00 太平洋時間 (UTC-8) 或更新版本。  
  
 新增下列程式碼。  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]  
  
 在視覺效果C#您從 Visual Studio 2008 升級的專案中，建構函式會出現在功能區程式碼檔案。  
  
 在 Visual Basic 專案，或在視覺效果C#中建立的專案[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]，建構函式會出現在功能區設計工具程式碼檔案。 此檔案名為*YourRibbonItem*。Designer.cs 或*YourRibbonItem*.Designer.vb。 若要查看這個檔案在 Visual Basic 專案中的，您必須先按一下**顯示所有檔案**方案總管 中的按鈕。  
  
### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>在 CreateRibbonExtensibilityObject 方法中設定屬性  
 您可以設定的屬性`Ribbon`控制當您覆寫`CreateRibbonExtensibilityObject`方法中的`ThisAddin`， `ThisWorkbook`，或`ThisDocument`您專案的類別。 如需詳細資訊`CreateRibbonExtensibilityObject`方法，請參閱 <<c2> [ 功能區概觀](../vsto/ribbon-overview.md)。  
  
 下列範例會將功能區屬性`CreateRibbonExtensibilityObject`方法的`ThisWorkbook`類別的 Excel 活頁簿專案。  
  
 新增下列程式碼。  
  
 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]  
  
###  <a name="ReadOnlyProperties"></a> 會變成唯讀的屬性  
 下表顯示只能在功能區載入之前設定的屬性。  
  
> [!NOTE]  
>  您可以隨時設定動態功能表上的控制項的屬性。 這個表格不適用於在此情況下。  
  
|屬性|功能區控制項類別|  
|--------------|--------------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**欄數**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**動態**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**群組**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**名稱**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**位置**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**資料列計數**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**索引標籤**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**標題**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>設定會出現在 Outlook 偵測器的功能區的屬性  
 功能區的新執行個體被建立每次使用者開啟功能區會顯示在偵測器。 不過，您可以設定只在功能區的第一個執行個體建立之前，在上表中列出的屬性。 第一個執行個體建立之後，這些屬性會變成唯讀，因為第一個執行個體定義的 Outlook 用來載入功能區 XML 檔案。  
  
 如果您有任何這些屬性設定為不同的值，建立功能區的其他執行個體時的條件式邏輯時，此程式碼會有任何作用。  
  
> [!NOTE]  
>  請確認**名稱**屬性設定為您的 Outlook 功能區中新增每個控制項。 如果您在 Outlook 功能區在執行階段加入控制項，您必須在程式碼中設定這個屬性。 如果您在設計階段將控制項新增至 Outlook 功能區，就會自動設定的 Name 屬性。  
  
## <a name="ribbon-control-events"></a>功能區控制項事件  
 每個控制項類別包含一或多個事件。 下表描述這些事件。  
  
|Event - 事件|描述|  
|-----------|-----------------|  
|按一下|發生於按下控制項時。|  
|TextChanged|編輯方塊或下拉式方塊的文字變更時，就會發生。|  
|ItemsLoading|發生於控制項的項目集合由 Office。 Office 在您的程式碼變更控制項的屬性，或您呼叫之前，會快取項目集合<xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A>方法。|  
|ButtonClick|中的按鈕時，就會發生<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>或<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>按下。|  
|SelectionChanged|發生時的選取範圍<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>或<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>變更。|  
|DialogLauncherClick|按一下群組右下角的對話方塊啟動器圖示時，就會發生。|  
  
 這些事件的事件處理常式有下列兩個參數。  
  
|參數|描述|  
|---------------|-----------------|  
|*寄件者*|<xref:System.Object>表示引發事件的控制項。|  
|*e*|A <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> ，其中包含<xref:Microsoft.Office.Core.IRibbonControl>。 使用這個控制項來存取所提供的功能區物件模型中沒有任何屬性[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。|  
  
## <a name="see-also"></a>另請參閱  
 [在執行階段功能區的存取](../vsto/accessing-the-ribbon-at-run-time.md)   
 [功能區概觀](../vsto/ribbon-overview.md)   
 [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [逐步解說：更新在執行階段的功能區上的控制項](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [適用於 Outlook 自訂功能區](../vsto/customizing-a-ribbon-for-outlook.md)   
 [如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)   
 [如何：將控制項加入至 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [如何：將功能區設計工具功能區匯出至功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [如何：顯示增益集使用者介面錯誤](../vsto/how-to-show-add-in-user-interface-errors.md)  
