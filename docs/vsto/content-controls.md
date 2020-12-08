---
title: 內容控制項
description: 學習內容控制項，以及內容控制項如何提供方法讓您設計檔和範本。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.DropDownListContentControl
- VST.Toolbox.RichTextContentControl
- VST.Toolbox.PlainTextContentControl
- VST.Toolbox.ComboBoxContentControl
- VST.Toolbox.CCBuildingBlockGalleryContentControl
- VST.Toolbox.DatePickerContentControl
- VST.Toolbox.PictureContentControl
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document building blocks [Office development in Visual Studio]
- restricted permissions [Office development in Visual Studio]
- ComboBoxContentControl class
- PictureContentControl class
- PlainTextContentControl class
- Office documents [Office development in Visual Studio], restricted permissions
- RichTextContentControl class
- content controls [Office development in Visual Studio]
- building block gallery [Office development in Visual Studio]
- controls [Office development in Visual Studio], content controls
- GroupContentControl class
- documents [Office development in Visual Studio], restricted permissions
- DropDownListContentControl class
- DatePickerContentControl class
- data binding [Office development in Visual Studio], content controls
- content controls [Office development in Visual Studio], about content controls
- custom XML parts, content controls
- templates [Office development in Visual Studio], content controls
- BuildingBlockGalleryContentControl class
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a34211c7fb1fa001719219b7d08baab65340bde5
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848036"
---
# <a name="content-controls"></a>內容控制項
  內容控制項提供一種設計文件和範本的方式，能讓它們具有下列功能：

- 像表單一樣具有受控制輸入的使用者介面 (UI)。

- 防止使用者編輯文件或範本受保護區段的限制。 如需詳細資訊，請參閱 [使用內容控制項保護檔的元件](#Protection)。

- 繫結至資料來源的資料。 如需詳細資訊，請參閱 [將資料系結至內容控制項](#DataBinding)。

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  ![影片連結](../vsto/media/playvideo.gif "視訊的連結") 如需相關的影片示範，請參閱 [使用 Office system 的 Visual Studio Tools 將資料系結至 Word 2007 內容控制項 (3.0) ](/previous-versions/office/developer/office-2007/bb967663(v=office.12))。

## <a name="overview-of-content-controls"></a>內容控制項總覽
 內容控制項能為使用者的輸入和列印提供最佳化的 UI。 當您在文件中加入內容控制項時，可以指示使用者的框線、標題和暫存文字就會識別控制項。 文件的列印版本中不會出現控制項的框線和標題。

 例如，如果您想讓使用者在文件區段中輸入日期，您可以在文件中加入日期選擇器內容控制項。 當使用者按一下控制項時，標準的日期選擇器 UI 就會出現。 您也可以設定控制項屬性，設定出現的地區行事曆及指定日期格式。 使用者選擇日期之後，控制項的 UI 會隱藏，只有使用者列印文件時才顯示日期。

 內容控制項也會協助您執行下列作業：

- 防止使用者編輯或刪除文件組件。 如果文件或範本中有使用者應可讀取但無法編輯的資訊，或如果您希望使用者能夠編輯但不能刪除內容控制項，這非常有用。

- 將文件或範本的組件繫結至資料。 您可以將內容控制項繫結至資料庫欄位、[!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] 中的 Managed 物件、儲存在文件的 XML 元素，及其他資料來源。

  在文件層級的專案中，您可以於設計階段或執行階段，將內容控制項加入文件。 在 VSTO 增益集專案中，您可以在執行階段將內容控制項加入任何開啟的文件。 如需詳細資訊，請參閱 [如何：將內容控制項加入 Word 檔](../vsto/how-to-add-content-controls-to-word-documents.md)。

> [!NOTE]
> 您只能在以 Open XML 格式儲存的檔中使用內容控制項。 您無法在檔中使用儲存在 Word 97-2003 檔 (*.doc*) 格式的內容控制項。

## <a name="types-of-content-controls"></a>內容控制項的類型
 有九種不同型別的內容控制項可以加入文件。 大部分的內容控制項在 <xref:Microsoft.Office.Tools.Word> 命名空間中有對應的型別。 您也可以使用泛型的 <xref:Microsoft.Office.Tools.Word.ContentControl>，它可以代表任何可用的內容控制項。 如需示範如何使用每個可用內容控制項的逐步解說，請參閱 [逐步解說：使用內容控制項建立範本](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)。

### <a name="build-block-gallery"></a>組建區塊資源庫
 建立區塊庫可讓使用者從 *檔建立區塊* 清單中選取，以插入檔中。 文件建置組塊是一段可以多次使用的內容，例如通用的封面頁、格式化的資料表或頁首。 如需詳細資訊，請參閱 <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> 型別。 如需建立區塊的詳細資訊，請參閱 [Word 2007 中適用于開發人員的新功能](/previous-versions/office/developer/office-2007/bb266218(v=office.12))。

### <a name="check-box"></a>核取方塊
 核取方塊提供的 UI，代表二進位狀態：選取或清除。

 不同於其他型別的內容控制項，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 不提供表示核取方塊內容控制項的特定型別。 換句話說，沒有 `CheckBoxContentControl` 型別。 不過，以程式設計的方式在文件中加入泛型 <xref:Microsoft.Office.Tools.Word.ContentControl>您仍然可以建立核取方塊內容控制項。 如需詳細資訊，請參閱 [Word 專案中的核取方塊內容控制項](#checkbox)。

### <a name="combo-box"></a>下拉式方塊
 下拉式方塊會顯示使用者可以選取的項目清單。 不同於下拉式清單，下拉式方塊可讓使用者加入自己的項目。 如需詳細資訊，請參閱 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> 型別。

### <a name="date-picker"></a>日期選擇器
 日期選擇器提供選取日期的行事曆 UI。 當終端使用者按一下控制項的下拉箭號，就會出現日曆。 您可以使用地區行事曆和不同的日期格式。 如需詳細資訊，請參閱 <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> 型別。

### <a name="drop-down-list"></a>下拉式清單
 下拉式清單會顯示使用者可以選取的項目清單。 不同於下拉式方塊，下拉式清單不會讓使用者加入或編輯項目。 如需詳細資訊，請參閱 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 型別。

### <a name="group"></a>群組
 群組控制項定義的文件受保護區域，使用者不能予以編輯或刪除。 群組控制項可以包含任何文件項目，例如文字、表格、圖形及其他內容控制項。 如需詳細資訊，請參閱 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 型別。

### <a name="picture"></a>Picture
 圖片控制項會顯示映像。 您可以在設計階段或執行階段指定映像，或者使用者可以按一下這個控制項選取要插入文件中的映像。 如需詳細資訊，請參閱 <xref:Microsoft.Office.Tools.Word.PictureContentControl> 型別。

### <a name="rich-text"></a>Rich text
 RTF 文字控制項包含文字或其他項目，例如資料表、圖片或其他內容控制項。 如需詳細資訊，請參閱 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 型別。

### <a name="plain-text"></a>純文字
 純文字控制項包含文字。 純文字控制項不能包含其他項目，例如表格、圖片或其他內容控制項。 此外，純文字控制項中的所有文字都具有相同的格式。 例如，如果您斜體化純文字控制項中某個句子的某個字，則控制項內所有的文字都會變成斜體。 如需詳細資訊，請參閱 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> 型別。

### <a name="generic-content-control"></a>一般內容控制項
 泛型內容控制項是 <xref:Microsoft.Office.Tools.Word.ContentControl> 物件，可以代表內容控制項的任何可用型別。 使用 <xref:Microsoft.Office.Tools.Word.ContentControl.Type%2A> 屬性，您可以把 <xref:Microsoft.Office.Tools.Word.ContentControl> 物件的行為變得像不同型別的內容控制項。 例如，如果您建立代表純文字控制項的 <xref:Microsoft.Office.Tools.Word.ContentControl> 物件，您可以在執行階段變更它，讓它的行為類似下拉式方塊。

 您只能在執行階段建立 <xref:Microsoft.Office.Tools.Word.ContentControl> 物件，不能在設計階段建立。 如需詳細資訊，請參閱 [如何：將內容控制項加入 Word 檔](../vsto/how-to-add-content-controls-to-word-documents.md)。

## <a name="common-features-of-content-controls"></a>內容控制項的一般功能
 大部分內容控制項會共用一組可用以執行一般工作的成員。 下表描述使用這些成員可以執行的一些工作。

|這項工作：|執行此動作：|
|--------------------|--------------|
|取得或設定控制項中要顯示的文字。|使用 **Text** 屬性。 **注意：** <xref:Microsoft.Office.Tools.Word.PictureContentControl> 和 <xref:Microsoft.Office.Tools.Word.ContentControl> 類型沒有這個屬性。|
|取得或設定控制項顯示的暫存文字，直到使用者編輯控制項為止，以資料來源的資料填入控制項，不然控制項的內容會被刪除。|使用 **PlaceholderText** 屬性。 **注意：**  型別沒有 <xref:Microsoft.Office.Tools.Word.PictureContentControl> 這個屬性。|
|當使用者按一下它時，取得或設定內容控制項框線中顯示的標題。|使用 **Title** 屬性。|
|在使用者編輯控制項之後，自動移除文件的控制項。 (控制項中的文字保留在文件中。)|使用 **暫存** 屬性。|
|當使用者在控制項中按一下，或以程式設計方式將游標移至內容控制項時，執行程式碼。|處理控制項的 <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> 事件。|
|當使用者在內容控制項外部按一下，或以程式設計方式將游標移出內容控制項時，執行程式碼。|處理控制項的 <xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting> 事件。|
|因為取消復原或復原作業而文件中加入內容控制項之後，執行程式碼。|處理控制項的 <xref:Microsoft.Office.Tools.Word.ContentControlBase.Added> 事件。|
|就在刪除文件中的內容控制項之前，執行程式碼。|處理控制項的 <xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting> 事件。|

## <a name="protect-parts-of-documents-by-using-content-controls"></a><a name="Protection"></a> 使用內容控制項保護檔的元件
 當您保護文件的某個部分時，使用者即無法變更或刪除該部分文件的內容。 使用內容控制項有多種方法可以保護文件的組件。

 如果要保護的區域在內容控制項內，您可以使用內容控制項的屬性，防止使用者編輯或刪除控制項：

- **LockContents** 屬性可防止使用者編輯內容。

- **LockContentControl** 屬性可防止使用者刪除該控制項。

  如果要保護的區域不在內容控制項內，或者要保護的區域包含內容控制項和其他類型的內容，您可以將整個區域放入 <xref:Microsoft.Office.Tools.Word.GroupContentControl>。 不像其他內容的控制項，<xref:Microsoft.Office.Tools.Word.GroupContentControl> 不提供向使用者顯示的 UI。 它唯一的用途是定義使用者無法編輯的區域。

> [!NOTE]
> 如果建立的 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 包含內嵌內容控制項，則不會自動保護這些內嵌內容控制項。 您必須使用每個內嵌控制項的 **LockContents** 屬性，以防止使用者編輯其內容。

 如需如何使用內容控制項保護檔元件的詳細資訊，請參閱 [如何：使用內容控制項保護檔的元件](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)。

## <a name="bind-data-to-content-controls"></a><a name="DataBinding"></a> 將資料系結至內容控制項
 將內容控制項繫結至資料來源，即可在文件中顯示資料。 當資料來源更新時，內容控制項就會反映變更。 您也可以將變更儲存回資料來源。

 內容控制項提供下列資料繫結選項：

- 您可以使用與 Windows Form 相同的資料繫結模型，將內容控制項繫結到資料庫欄位或 Managed 物件。

- 您可以將內容控制項系結至 XML (中的元素，也就是內嵌于檔中的 *自訂 xml 元件*) 。

  如需在 Office 方案中將主控制項系結至資料的總覽，請參閱將資料系結 [至 office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。

### <a name="use-the-windows-forms-data-binding-model"></a>使用 Windows Forms 資料系結模型
 大部分的內容控制項支援 Windows Form 使用的簡易資料繫結模型。 簡易資料繫結表示控制項是繫結至單一資料元素，例如資料表中資料行的值。 如需詳細資訊，請參閱資料系結 [和 Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)。

 在檔層級專案中，您可以使用中的 [ **資料來源** ] 視窗，將資料系結至內容控制項 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 如需如何將資料系結內容控制項新增至檔的詳細資訊，請參閱 [如何：使用資料庫的資料填入檔](../vsto/how-to-populate-documents-with-data-from-a-database.md) 和 [如何：將物件的資料填入檔](../vsto/how-to-populate-documents-with-data-from-objects.md)。

 下表列出您可以在 [ **資料來源** ] 視窗中系結至每個資料類型的內容控制項。

|資料類型|預設內容控制項|可以繫結到這個資料類型的其他內容控制項|
|---------------|-----------------------------|----------------------------------------------------------------|
|<xref:System.Boolean><br /><br /> <xref:System.Byte><br /><br /> <xref:System.Char><br /><br /> <xref:System.Double><br /><br /> <xref:System.Enum><br /><br /> <xref:System.Guid><br /><br /> <xref:System.Int16><br /><br /> <xref:System.Int32><br /><br /> <xref:System.Int64><br /><br /> <xref:System.SByte><br /><br /> <xref:System.Single><br /><br /> <xref:System.String><br /><br /> <xref:System.TimeSpan><br /><br /> <xref:System.UInt16><br /><br /> <xref:System.UInt32><br /><br /> <xref:System.UInt64>|<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|
|<xref:System.DateTime>|<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|
|<xref:System.Drawing.Image><br /><br /> <xref:System.Byte> 陣列|<xref:Microsoft.Office.Tools.Word.PictureContentControl>|無|

 在文件層級和 VSTO 增益集專案中，您可以使用控制項的 <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> 屬性的 <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> 方法，以程式設計方式將內容控制項繫結至資料來源。 如果您這樣做，請將字串 **文字** 傳遞至方法的 *propertyName* 參數 <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> 。 **Text** 屬性是內容控制項的預設資料系結屬性。

 內容控制項也支援雙向的資料繫結，讓控制項中的變更更新回資料來源。 如需詳細資訊，請參閱 [如何：使用主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)。

> [!NOTE]
> 內容控制項不支援複雜的資料繫結。 如果使用 Windows Form 資料模型將 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 或 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> 繫結到資料來源，當使用者按一下控制項就只會看到單一值。 如果您想要將這些控制項繫結至一組使用者可以從中選擇的資料值，您可以將這些控制項繫結至自訂 XML 組件中的元素。

### <a name="bind-content-controls-to-custom-xml-parts"></a>將內容控制項系結至自訂 XML 元件
 您可以將一些內容控制項繫結至內嵌於文件的自訂 XML 組件的元素。 如需自訂 XML 元件的詳細資訊，請參閱 [自訂 xml 元件總覽](../vsto/custom-xml-parts-overview.md)。

 若要將內容控制項系結至自訂 XML 元件中的元素，請使用控制項的 **XMLMapping** 屬性。 下列程式碼範例示範如何將 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> 繫結至已加入文件之自訂 XML 組件的 `Product` 節點下的 `Price` 元素。

```vb
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price")
```

```csharp
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price", String.Empty, null);
```

 如需示範如何更詳細地將內容控制項系結至自訂 XML 元件的逐步解說，請參閱 [逐步解說：將內容控制項系結至自訂 xml 元件](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)。

 當您將內容控制項繫結至自訂 XML 組件時，會自動啟用雙向資料繫結。 如果使用者編輯控制項中的文字，對應的 XML 元素就會自動更新。 同樣地，如果自訂 XML 組件中的元素值變更，繫結至該 XML 元素的內容控制項就會顯示新的資料。

 您可以將下列型別的內容控制項繫結至自訂 XML 組件：

- <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>

- <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>

- <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>

- <xref:Microsoft.Office.Tools.Word.PictureContentControl>

- <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>

### <a name="data-bind-events-for-content-controls"></a>內容控制項的資料系結事件
 所有的內容控制項都會提供一組事件，您可以控制它們來執行與資料相關的工作，例如先驗證控制項中的文字是否符合特定準則，再更新資料來源。 下表列出與資料繫結相關的內容控制項事件。

|Task|事件|
|----------|-----------|
|就在 Word 自動更新繫結至自訂 XML 組件的內容控制項文字之前，執行程式碼。|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|
|就在 Word 自動更新繫結至內容控制項的自訂 XML 組件資料之前 (也就是內容控制項中的文字變更之後)，執行程式碼。|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|
|執行您自己的程式碼，根據自訂準則驗證控制項的內容。|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validating>|
|成功驗證控制項的內容之後，執行程式碼。|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validated>|

## <a name="limitations-of-content-controls"></a>內容控制項的限制
 當您在 Office 專案中使用內容控制項時，請注意下列限制。

### <a name="behavior-differences-between-design-time-and-runtime"></a>設計階段與執行時間之間的行為差異
 Microsoft Office Word 在執行階段加諸於內容控制項的許多限制，不會在設計階段強制施行。 當您在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中設計文件層級解決方案的 UI 時，請務必以執行階段支援的方式修改內容控制項。

 如果以執行階段控制項不支援的方式，在設計階段修改內容控制項，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 設計工具不會警示有不受支援的變更。 不過，當偵錯或執行專案，或儲存後再重新開啟專案時，Word 會顯示錯誤訊息，並要求權限修復文件。 當您修復文件時，Word 會移除控制項中所有不受支援的內容和格式。

 例如，Word 不會阻止您在設計階段將資料表加入 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>。 但因為 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> 物件在執行階段不能包含資料表，所以 Word 會在文件開啟時顯示錯誤訊息。

 另請注意，許多定義內容控制項行為的屬性，在設計階段不起任何作用。 例如，如果您在設計階段將內容控制項的 **LockContents** 屬性設定為 **True** ，您仍然可以在設計工具中編輯控制項中的文字 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 這個屬性只會防止使用者在執行階段編輯控制項。

### <a name="event-limitations"></a>事件限制
 內容控制項不提供使用者變更文字或其他控制項項目時所引發的事件。 例如，當使用者在 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 或 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> 中選取不同的項目時，不會引發任何事件。

 若要判斷使用者何時編輯內容控制項的內容，您可以將控制項繫結至自訂 XML 組件，接著處理 <xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating> 事件。 在使用者變更繫結至自訂 XML 組件控制項的內容時，會引發這個事件。 如需示範如何將內容控制項系結至自訂 XML 元件的逐步解說，請參閱 [逐步解說：將內容控制項系結至自訂 xml 元件](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)。

### <a name="check-box-content-controls-in-word-projects"></a><a name="checkbox"></a> Word 專案中的核取方塊內容控制項
 Word 2010 導入了表示核取方塊的新型別內容控制項。 但是，不 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會提供您要在 Office 專案中使用的對應 CheckBoxContentControl 類型。 若要在 [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 Word 2010 專案中建立核取方塊內容控制項，請使用 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddContentControl%2A> 方法建立 <xref:Microsoft.Office.Tools.Word.ContentControl> 物件，並將 <xref:Microsoft.Office.Interop.Word.WdContentControlType.wdContentControlCheckBox> 值傳遞給方法，以指定核取方塊內容控制項。 下列程式碼範例會示範如何執行這項操作。

 [!code-vb[Trin_ContentControlReference#800](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/checkbox.vb#800)]
 [!code-csharp[Trin_ContentControlReference#800](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/checkbox.cs#800)]

## <a name="see-also"></a>另請參閱
- [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)
- [如何：將內容控制項新增至 Word 檔](../vsto/how-to-add-content-controls-to-word-documents.md)
- [逐步解說：使用內容控制項建立範本](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)
- [Office 方案中的資料](../vsto/data-in-office-solutions.md)
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
