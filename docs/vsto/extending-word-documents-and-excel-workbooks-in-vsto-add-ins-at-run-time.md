---
title: 擴充 Word 文件和 Excel 活頁簿，在 VSTO 增益集在執行階段
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- GetVstoObject method
- application-level add-ins [Office development in Visual Studio], adding controls to documents
- host items [Office development in Visual Studio], creating at run time in add-ins
- application-level add-ins [Office development in Visual Studio], extending Word documents
- application-level add-ins [Office development in Visual Studio], extending Excel workbooks
- controls [Office development in Visual Studio], adding at run time
- HasVstoObject method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7b7461ba184850ba53099327fdad44e3103dcd87
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548618"
---
# <a name="extend-word-documents-and-excel-workbooks-in-vsto-add-ins-at-runtime"></a>擴充 Word 文件和 Excel 活頁簿，在 VSTO 增益集在執行階段
  您可以使用 VSTO 增益集，以下列方式自訂 Word 文件和 Excel 活頁簿：  
  
-   將 Managed 控制項加入任何開啟的文件或工作表。  
  
-   將 Excel 工作表上的現有清單物件轉換成擴充的 <xref:Microsoft.Office.Tools.Excel.ListObject> ，這個物件會公開事件，而且可以透過 Windows Form 資料繫結模型繫結至資料。  
  
-   存取 Word 和 Excel 為特定文件、活頁簿和工作表公開的應用程式層級事件。  
  
 若要使用這項功能，您可以產生在擴充的文件或活頁簿的執行階段物件。  
  
 **適用於：** 本文章中的資訊適用於 VSTO 增益集專案中下列應用程式： Excel 和 Word。 如需詳細資訊，請參閱[依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)。  
  
## <a name="generate-extended-objects-in-vsto-add-ins"></a>在 VSTO 增益集產生擴充的物件  
 *「擴充物件」* (Extended Object) 是 Visual Studio Tools for Office Runtime 所提供的類型執行個體，可為原本存在於 Word 或 Excel 物件模型中的物件 (稱為 *「原生 Office 物件」*(Native Office Object)) 新增功能。 若要產生 Word 或 Excel 物件的擴充物件，請使用 `GetVstoObject` 方法。 第一次呼叫`GetVstoObject`方法指定的 Word 或 Excel 物件，它會傳回可擴充指定的物件的新物件。 每次呼叫方法並指定相同的 Word 或 Excel 物件時，都會傳回相同的擴充物件。  
  
 擴充物件的類型具有與原生 Office 物件類型相同的名稱，但是該類型是在 <xref:Microsoft.Office.Tools.Excel> 或 <xref:Microsoft.Office.Tools.Word> 命名空間中定義的。 例如，如果您呼叫 `GetVstoObject` 方法以擴充 <xref:Microsoft.Office.Interop.Word.Document> 物件，該方法會傳回 <xref:Microsoft.Office.Tools.Word.Document> 物件。  
  
 `GetVstoObject`方法原本主要用於 VSTO 增益集專案中。 您也可以在文件層級專案中使用這些方法，但運作方式會不同，而且用途較少。  
  
 若要判斷是否已為特定原生 Office 物件產生擴充物件，請使用 `HasVstoObject` 方法。 如需詳細資訊，請參閱[判斷是否已擴充 Office 物件](#HasVstoObject)。  
  
### <a name="generate-host-items"></a>產生主項目  
 當您使用`GetVstoObject`擴充文件層級物件 (也就是<xref:Microsoft.Office.Interop.Excel.Workbook>， <xref:Microsoft.Office.Interop.Excel.Worksheet>，或<xref:Microsoft.Office.Interop.Word.Document>)，傳回的物件稱為*主項目*。 主項目是可包含其他物件 (包括其他擴充物件和控制項) 的類型。 它類似 Word 或 Excel 主要 Interop 組件中的對應類型，但具有額外的功能。 如需主項目的詳細資訊，請參閱[主項目和裝載控制項概觀](../vsto/host-items-and-host-controls-overview.md)。  
  
 在您產生主項目之後，即可用來將 Managed 控制項加入文件、活頁簿或工作表。 如需詳細資訊，請參閱[加入 managed 控制項加入文件和工作表](#AddControls)。  
  
#### <a name="to-generate-a-host-item-for-a-word-document"></a>產生 Word 文件的主項目  
  
-   下列程式碼範例示範如何產生現用文件的主項目。  
  
     [!code-vb[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#8)]
     [!code-csharp[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#8)]  
  
#### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>產生 Excel 活頁簿的主項目  
  
-   下列程式碼範例示範如何產生現用活頁簿的主項目。  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#2)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#2)]  
  
#### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>產生 Excel 工作表的主項目  
  
-   下列程式碼範例示範如何產生專案中現用工作表的主項目。  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#1)]  
  
### <a name="generate-listobject-host-controls"></a>產生 ListObject 主控制項  
 當您使用 `GetVstoObject` 方法擴充 <xref:Microsoft.Office.Interop.Excel.ListObject> 時，該方法會傳回 <xref:Microsoft.Office.Tools.Excel.ListObject>。 <xref:Microsoft.Office.Tools.Excel.ListObject>包含所有的原始功能<xref:Microsoft.Office.Interop.Excel.ListObject>。 它也具有其他功能，並可以使用 Windows Form 資料繫結模型繫結至資料。 如需詳細資訊，請參閱[ListObject 控制項](../vsto/listobject-control.md)。  
  
#### <a name="to-generate-a-host-control-for-a-listobject"></a>產生 ListObject 的主控制項  
  
-   下列程式碼範例示範如何為專案之現用工作表中的第一個 <xref:Microsoft.Office.Tools.Excel.ListObject> 產生 <xref:Microsoft.Office.Interop.Excel.ListObject> 。  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#3)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#3)]  
  
###  <a name="AddControls"></a> 將 managed 的控制項加入文件和工作表  
 在您產生 <xref:Microsoft.Office.Tools.Word.Document> 或 <xref:Microsoft.Office.Tools.Excel.Worksheet>之後，即可將控制項加入這些擴充物件所代表的文件或工作表。 若要加入控制項，請使用`Controls`屬性<xref:Microsoft.Office.Tools.Word.Document>或<xref:Microsoft.Office.Tools.Excel.Worksheet>。 如需詳細資訊，請參閱[將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
 您可以加入 Windows Form 控制項或 *「主控制項」*(Host Control)。 主控制項是 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 所提供的控制項，可包裝 Word 或 Excel 主要 Interop 組件中的對應控制項。 主控制項不僅會公開所有基礎原生 Office 物件的行為。 它也會引發事件，並可以使用 Windows Form 資料繫結模型繫結至資料。 如需詳細資訊，請參閱[主項目和裝載控制項概觀](../vsto/host-items-and-host-controls-overview.md)。  
  
> [!NOTE]  
>  您無法使用 VSTO 增益集將 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項加入工作表，或者將 <xref:Microsoft.Office.Tools.Word.XMLNode> 或 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項加入文件。 這些主控制項無法以程式設計方式加入。 如需詳細資訊，請參閱[主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。  
  
### <a name="persist-and-remove-controls"></a>保存和移除控制項  
 將 Managed 控制項加入文件或工作表並在儲存與關閉文件時，將無法保存這些控制項。 所有主控制項都會被移除，只留下基礎原生 Office 物件。 例如， <xref:Microsoft.Office.Tools.Excel.ListObject> 會變成 <xref:Microsoft.Office.Interop.Excel.ListObject>。 所有 Windows Form 控制項也會被移除，但控制項的 ActiveX 包裝函式會留在文件中。 您必須在 VSTO 增益集中包含程式碼，以清除控制項，或在下次開啟文件時重新建立控制項。 如需詳細資訊，請參閱[保存動態控制項中的 Office 文件](../vsto/persisting-dynamic-controls-in-office-documents.md)。  
  
## <a name="access-application-level-events-on-documents-and-workbooks"></a>存取文件和活頁簿上的應用程式層級事件  
 原生 Word 和 Excel 物件模型中的某些文件、活頁簿和工作表事件只會在應用程式層級上引發。 例如，在 Word 中開啟文件時會引發 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 事件，但這個事件是在 <xref:Microsoft.Office.Interop.Word.Application> 類別 (而不是 <xref:Microsoft.Office.Interop.Word.Document> 類別) 中定義的。  
  
 如果您只在 VSTO 增益集中使用原生 Office 物件，則必須處理這些應用程式層級事件，然後再撰寫額外的程式碼，以判斷引發該事件的文件是否為您已自訂的文件。 主項目會在文件層級提供這些事件，如此就比較容易處理特定文件的事件。 您可以產生主項目，然後再處理這個主項目的事件。  
  
### <a name="example-that-uses-native-word-objects"></a>使用原生 Word 物件範例  
 下列程式碼範例示範如何處理 Word 文件的應用程式層級事件。 `CreateDocument` 方法會建立新文件，然後定義防止儲存這份文件的 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 事件處理常式。 是，就會引發應用程式層級事件<xref:Microsoft.Office.Interop.Word.Application>物件和事件處理常式必須比較`Doc`參數`document1`物件來判斷如果`document1`代表儲存的文件。  
  
 [!code-vb[Trin_WordAddInDynamicControls #12](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#12)]
 [!code-csharp[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#12)]  
  
### <a name="examples-that-use-a-host-item"></a>主項目的使用的範例  
 下列程式碼範例透過處理 <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> 主項目的 <xref:Microsoft.Office.Tools.Word.Document> 事件，來簡化這個程序。 `CreateDocument2`方法在這些範例會產生<xref:Microsoft.Office.Tools.Word.Document>延伸`document2`物件，然後定義<xref:Microsoft.Office.Tools.Word.Document.BeforeSave>防止儲存文件的事件處理常式。 此事件處理常式時才會呼叫`document2`儲存，並可以直接取消儲存動作，而不執行任何額外的工作來確認已儲存的文件。  
  
 下列程式碼範例示範這項工作。  
  
 [!code-vb[Trin_WordAddInDynamicControls #13](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#13)]
 [!code-csharp[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#13)]  
  
##  <a name="HasVstoObject"></a> 判斷是否已擴充 Office 物件  
 若要判斷是否已為特定原生 Office 物件產生擴充物件，請使用 `HasVstoObject` 方法。 這個方法會傳回**true**如果已產生擴充的物件。  
  
 請使用 `Globals.Factory.HasVstoMethod` 方法。 傳入您要針對擴充物件測試的原生 Word 或 Excel 物件，例如 <xref:Microsoft.Office.Interop.Word.Document> 或 <xref:Microsoft.Office.Interop.Excel.Worksheet>。  
  
 如果您只想在指定的 Office 物件具有擴充物件時才執行程式碼，`HasVstoObject` 方法會很有用。 例如，如果您有 Word VSTO 增益集處理<xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>從文件移除 managed 的控制項，它會在儲存之前，請使用事件`HasVstoObject`方法，以判斷是否已擴充該文件。 如果文件尚未擴充，它不能有 managed 控制項，並可傳回事件處理常式，而不嘗試清除文件的控制項。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫 VSTO 增益集](../vsto/programming-vsto-add-ins.md)   
 [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)  
  
  