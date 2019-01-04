---
title: ListObject 控制項
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.List
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- lists, events
- ListObject control
- ListObject control, events
- ListObject control, data binding
- ListObject control, improving performance when bound to data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0c488cafabcdffc3bfa56ee59ea4ca163c9d9dd0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945180"
---
# <a name="listobject-control"></a>ListObject 控制項
  <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項是可公開事件及繫結至資料的清單。 當您將清單加入工作表時，Visual Studio 會建立 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項，以便您直接對這個控制項進行程式設計，而不必周遊 Microsoft Office Excel 物件模型。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="create-the-control"></a>建立控制項  
 在文件層級專案中，您可以於設計階段或執行階段，將 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項加入工作表。 在 VSTO 增益集專案中，您可以新增<xref:Microsoft.Office.Tools.Excel.ListObject>控制項加入工作表，只能在執行階段。 如需詳細資訊，請參閱[＜How to：將 ListObject 控制項加入工作表](../vsto/how-to-add-listobject-controls-to-worksheets.md)。  
  
> [!NOTE]  
>  根據預設，當工作表關閉時，動態建立的清單物件不會保存為工作表中的主控制項。 如需詳細資訊，請參閱 <<c0> [ 將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
## <a name="bind-data-to-the-control"></a>將資料繫結至控制項  
 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項支援簡單和複雜資料繫結。 <xref:Microsoft.Office.Tools.Excel.ListObject>可以使用資料來源控制項繫結<xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A>並<xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A>在設計階段屬性或<xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A>方法在執行階段。  
  
> [!NOTE]  
>  如果將 <xref:Microsoft.Office.Tools.Excel.ListObject> 繫結至資料變更時會引發事件的資料來源 (例如 <xref:System.Data.DataTable>)，它會自動進行更新。 如果將 <xref:Microsoft.Office.Tools.Excel.ListObject> 繫結至資料變更時不會引發事件的資料來源，則必須呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> 或 <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> 方法以更新 <xref:Microsoft.Office.Tools.Excel.ListObject>。  
  
 當您將重複的結構描述項目對應至工作表儲存格，藉此將 <xref:Microsoft.Office.Tools.Excel.ListObject> 加入該儲存格時，Visual Studio 會自動將 <xref:Microsoft.Office.Tools.Excel.ListObject> 對應至產生的資料集。 不過， <xref:Microsoft.Office.Tools.Excel.ListObject> 不會自動繫結至資料。 您可以採取步驟來繫結<xref:Microsoft.Office.Tools.Excel.ListObject>來在設計階段或在執行階段在文件層級專案中的資料集。 您可以透過程式設計方式繫結<xref:Microsoft.Office.Tools.Excel.ListObject>至在執行階段在 VSTO 增益集中的資料集。  
  
 由於資料與 <xref:Microsoft.Office.Tools.Excel.ListObject>分離，因此您應該透過所繫結的資料集加入及移除資料，而不是直接透過 <xref:Microsoft.Office.Tools.Excel.ListObject>進行。 如果透過任何機制更新所繫結之資料集中的資料， <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項會自動反映這些變更。 如需詳細資訊，請參閱 <<c0> [ 將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
 您可以將 <xref:Microsoft.Office.Tools.Excel.ListObject> 繫結至資料來源，以快速填入 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。 如果您在繫結至資料的 <xref:Microsoft.Office.Tools.Excel.ListObject>中編輯資料，資料來源中也會自動進行這些變更。 如果您想要填入 <xref:Microsoft.Office.Tools.Excel.ListObject> ，再讓使用者變更 <xref:Microsoft.Office.Tools.Excel.ListObject> 中的資料，卻又不想要修改資料來源，則可以使用 <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> 方法將 <xref:Microsoft.Office.Tools.Excel.ListObject> 與資料來源中斷連結。 如需詳細資訊，請參閱[＜How to：使用資料填入 ListObject 控制項](../vsto/how-to-fill-listobject-controls-with-data.md)。  
  
> [!NOTE]  
>  重疊的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項不支援資料繫結。  
  
### <a name="improve-performance-in-listobject-controls"></a>提升 ListObject 控制項中的效能  
 如果先繫結控制項，再呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject> 填入資料集，通常會使 XML 檔案讀入繫結至資料之 <xref:System.Data.DataSet.ReadXml%2A> 控制項的速度變慢。 若要提升效能，請先呼叫 <xref:System.Data.DataSet.ReadXml%2A> 再繫結控制項。  
  
### <a name="disconnect-listobject-controls-from-the-data-source"></a>從資料來源中斷連接 ListObject 控制項  
 將 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項繫結至資料來源並以此資料填入控制項之後，您可以中斷與資料來源的連接，如此一來對清單物件中資料所做的修改，就不會影響資料來源。 如需詳細資訊，請參閱[＜How to：使用資料填入 ListObject 控制項](../vsto/how-to-fill-listobject-controls-with-data.md)。  
  
### <a name="restore-column-and-row-order"></a>還原欄和列順序  
 當您將資料繫結至在設計階段加入文件的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項時，Visual Studio 會在每次儲存活頁簿時，記錄欄和列順序。 如果使用者移<xref:Microsoft.Office.Tools.Excel.ListObject>資料行或資料列，在執行階段，的下次開啟活頁簿會保留新的順序和<xref:Microsoft.Office.Tools.Excel.ListObject>控制項繫結至資料來源一次。  
  
 如果您想要將 <xref:Microsoft.Office.Tools.Excel.ListObject> 還原成其原始欄和列順序，可以呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> 方法。 這個方法會移除與指定 <xref:Microsoft.Office.Tools.Excel.ListObject>之欄和列順序相關的自訂文件屬性。 如果不想保留 <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> 的欄和列順序，請從活頁簿的 <xref:Microsoft.Office.Tools.Excel.ListObject>事件呼叫這個方法。  
  
## <a name="format"></a>格式  
 可套用至 <xref:Microsoft.Office.Interop.Excel.ListObject> 的格式，也可套用至 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。 這包括框線、字型、數字格式和樣式。 使用者可以重新排列資料行中資料繫結<xref:Microsoft.Office.Tools.Excel.ListObject>，以及這些變更會保存提供的文件<xref:Microsoft.Office.Tools.Excel.ListObject>已在設計階段新增至文件。 下次開啟文件時，清單物件會繫結至相同的資料來源，但欄順序則會反映使用者的變更。  
  
## <a name="add-and-remove-columns-at-runtime"></a>新增和移除資料行，在執行階段  
 您無法手動新增或移除資料行在資料繫結<xref:Microsoft.Office.Tools.Excel.ListObject>控制項在執行階段。 如果使用者嘗試刪除資料行時，會立即還原，將會移除任何加入的資料行。 因此，請務必撰寫程式碼，向使用者說明為何無法在繫結至資料的 <xref:Microsoft.Office.Tools.Excel.ListObject> 上執行這些動作。 Visual Studio 在與資料繫結相關的 <xref:Microsoft.Office.Tools.Excel.ListObject> 上，提供數個事件。 例如，您可以使用 <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> 事件，在使用者嘗試刪除資料時，警告使用者該資料無法刪除並已還原。  
  
## <a name="add-and-remove-rows-at-runtime"></a>新增和移除資料列，在執行階段  
 只要資料來源允許新增列且不是唯讀，您便可以在繫結至資料的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項中手動加入及移除列。 您可以對 <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> 等事件撰寫程式碼，以驗證資料。 如需詳細資訊，請參閱[＜How to：新的資料列加入 ListObject 控制項時驗證資料](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)。  
  
 有時清單物件與資料來源的關聯性會造成常式錯誤。 例如，您可以對應要在 <xref:Microsoft.Office.Tools.Excel.ListObject>中出現的欄；在這種情況下，如果遺漏具有限制的欄 (例如不可接受 null 值的欄位)，則每次建立列都會引發錯誤。 您可以撰寫程式碼，在 <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> 事件的事件處理常式中加入遺漏的值。  
  
## <a name="rename-listobject-controls-in-excel"></a>重新命名 ListObject 控制項，在 Excel 中  
 Excel 可讓使用者藉由變更 Excel 表格，在執行階段的名稱**設計** 索引標籤。不過， <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項不支援這項功能。 如果使用者嘗試重新命名對應至 <xref:Microsoft.Office.Tools.Excel.ListObject>的 Excel 表格，該 Excel 表格的名稱會自動還原成儲存活頁簿時所使用的原始名稱。  
  
## <a name="events"></a>事件  
 下列事件適用於 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項：  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>  
  
## <a name="see-also"></a>另請參閱  
 [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [如何：將 ListObject 控制項加入工作表](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [如何：調整 ListObject 控制項的大小](../vsto/how-to-resize-listobject-controls.md)   
 [如何：新的資料列加入 ListObject 控制項時驗證資料](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [如何：將 ListObject 欄對應到資料](../vsto/how-to-map-listobject-columns-to-data.md)   
 [如何：使用資料填入 ListObject 控制項](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)   
 [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [擴充 Word 文件和 Excel 活頁簿，VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [如何：從資料庫的資料填入工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
