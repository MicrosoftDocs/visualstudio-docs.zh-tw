---
title: "在執行階段擴充 Word 文件和 Excel 活頁簿，在 VSTO 增益集中 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: c1607314-4cf8-439c-b4c5-709db8b71cff
caps.latest.revision: "61"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93010f03384e3cb3930911115ee92b3bb9205b9e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time"></a>在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿
  您可以使用 VSTO 增益集，以下列方式自訂 Word 文件和 Excel 活頁簿：  
  
-   將 Managed 控制項加入任何開啟的文件或工作表。  
  
-   將 Excel 工作表上的現有清單物件轉換成擴充的 <xref:Microsoft.Office.Tools.Excel.ListObject> ，這個物件會公開事件，而且可以透過 Windows Form 資料繫結模型繫結至資料。  
  
-   存取 Word 和 Excel 為特定文件、活頁簿和工作表公開的應用程式層級事件。  
  
 若要使用這項功能，請在執行階段產生可擴充文件或活頁簿的物件。  
  
 **適用對象：** 本主題資訊適用於 Excel 和 Word 等應用程式的 VSTO 增益集專案。 如需詳細資訊，請參閱 [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md)。  
  
## <a name="generating-extended-objects-in-vsto-add-ins"></a>使用 VSTO 增益集產生擴充物件  
 *「擴充物件」* (Extended Object) 是 Visual Studio Tools for Office Runtime 所提供的類型執行個體，可為原本存在於 Word 或 Excel 物件模型中的物件 (稱為 *「原生 Office 物件」*(Native Office Object)) 新增功能。 若要產生 Word 或 Excel 物件的擴充的物件，使用 GetVstoObject 方法。 第一次您呼叫 GetVstoObject 方法為指定 Word 或 Excel 物件，它會傳回可擴充指定的物件的新物件。 每次呼叫方法並指定相同的 Word 或 Excel 物件時，都會傳回相同的擴充物件。  
  
 擴充物件的類型具有與原生 Office 物件類型相同的名稱，但是該類型是在 <xref:Microsoft.Office.Tools.Excel> 或 <xref:Microsoft.Office.Tools.Word> 命名空間中定義的。 例如，如果您呼叫 GetVstoObject 方法，以擴充<xref:Microsoft.Office.Interop.Word.Document>物件，該方法會傳回<xref:Microsoft.Office.Tools.Word.Document>物件。  
  
 GetVstoObject 方法的目的是要主要用於 VSTO 增益集專案中。 您也可以在文件層級專案中使用這些方法，但運作方式會不同，而且用途較少。  
  
 若要判斷擴充的物件是否已產生特定的原生 Office 物件，請使用 HasVstoObject 方法。 如需詳細資訊，請參閱 [判斷是否已擴充 Office 物件](#HasVstoObject)。  
  
### <a name="generating-host-items"></a>產生主項目  
 當您使用 GetVstoObject 擴充文件層級物件 (也就是<xref:Microsoft.Office.Interop.Excel.Workbook>， <xref:Microsoft.Office.Interop.Excel.Worksheet>，或<xref:Microsoft.Office.Interop.Word.Document>)，傳回的物件稱為*主項目*。 主項目是可包含其他物件 (包括其他擴充物件和控制項) 的類型。 它類似 Word 或 Excel 主要 Interop 組件中的對應類型，但具有額外的功能。 如需主項目的詳細資訊，請參閱 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)。  
  
 在您產生主項目之後，即可用來將 Managed 控制項加入文件、活頁簿或工作表。 如需詳細資訊，請參閱 [將 Managed 控制項加入文件和工作表](#AddControls)。  
  
##### <a name="to-generate-a-host-item-for-a-word-document"></a>產生 Word 文件的主項目  
  
-   下列程式碼範例示範如何產生現用文件的主項目。  
  
     [!code-vb[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#8)]
     [!code-csharp[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#8)]  
  
##### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>產生 Excel 活頁簿的主項目  
  
-   下列程式碼範例示範如何產生現用活頁簿的主項目。  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#2)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#2)]  
  
##### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>產生 Excel 工作表的主項目  
  
-   下列程式碼範例示範如何產生專案中現用工作表的主項目。  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#1)]  
  
### <a name="generating-listobject-host-controls"></a>產生 ListObject 主控制項  
 當您使用 GetVstoObject 方法來擴充<xref:Microsoft.Office.Interop.Excel.ListObject>，方法會傳回<xref:Microsoft.Office.Tools.Excel.ListObject>。 <xref:Microsoft.Office.Tools.Excel.ListObject> 不僅具有原始 <xref:Microsoft.Office.Interop.Excel.ListObject>的所有功能，還具有其他功能，例如可以透過 Windows Form 資料繫結模型繫結至資料。 如需詳細資訊，請參閱 [ListObject Control](../vsto/listobject-control.md)。  
  
##### <a name="to-generate-a-host-control-for-a-listobject"></a>產生 ListObject 的主控制項  
  
-   下列程式碼範例示範如何為專案之現用工作表中的第一個 <xref:Microsoft.Office.Tools.Excel.ListObject> 產生 <xref:Microsoft.Office.Interop.Excel.ListObject> 。  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#3)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#3)]  
  
##  <a name="AddControls"></a> 將 Managed 控制項加入文件和工作表  
 在您產生 <xref:Microsoft.Office.Tools.Word.Document> 或 <xref:Microsoft.Office.Tools.Excel.Worksheet>之後，即可將控制項加入這些擴充物件所代表的文件或工作表。 若要這樣做，請使用控制項內容的<xref:Microsoft.Office.Tools.Word.Document>或<xref:Microsoft.Office.Tools.Excel.Worksheet>。 如需詳細資訊，請參閱 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
 您可以加入 Windows Form 控制項或 *「主控制項」*(Host Control)。 主控制項是 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 所提供的控制項，可包裝 Word 或 Excel 主要 Interop 組件中的對應控制項。 主控制項不僅會公開基礎原生 Office 物件的所有行為，還會引發事件，並可透過 Windows Form 資料繫結模型繫結至資料。 如需詳細資訊，請參閱 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)。  
  
> [!NOTE]  
>  您無法使用 VSTO 增益集將 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項加入工作表，或者將 <xref:Microsoft.Office.Tools.Word.XMLNode> 或 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項加入文件。 這些主控制項無法以程式設計方式加入。 如需詳細資訊，請參閱 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。  
  
### <a name="persisting-and-removing-controls"></a>保存和移除控制項  
 將 Managed 控制項加入文件或工作表並在儲存與關閉文件時，將無法保存這些控制項。 所有主控制項都會被移除，只留下基礎原生 Office 物件。 例如， <xref:Microsoft.Office.Tools.Excel.ListObject> 會變成 <xref:Microsoft.Office.Interop.Excel.ListObject>。 所有 Windows Form 控制項也會被移除，但控制項的 ActiveX 包裝函式會留在文件中。 您必須在 VSTO 增益集中包含程式碼，以清除控制項，或在下次開啟文件時重新建立控制項。 如需詳細資訊，請參閱 [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md)。  
  
## <a name="accessing-application-level-events-on-documents-and-workbooks"></a>存取文件和活頁簿上的應用程式層級事件  
 原生 Word 和 Excel 物件模型中的某些文件、活頁簿和工作表事件只會在應用程式層級上引發。 例如，在 Word 中開啟文件時會引發 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 事件，但這個事件是在 <xref:Microsoft.Office.Interop.Word.Application> 類別 (而不是 <xref:Microsoft.Office.Interop.Word.Document> 類別) 中定義的。  
  
 如果您只在 VSTO 增益集中使用原生 Office 物件，則必須處理這些應用程式層級事件，然後再撰寫額外的程式碼，以判斷引發該事件的文件是否為您已自訂的文件。 主項目會在文件層級提供這些事件，如此就比較容易處理特定文件的事件。 您可以產生主項目，然後再處理這個主項目的事件。  
  
### <a name="example-that-uses-native-word-objects"></a>使用原生 Word 物件的範例  
 下列程式碼範例示範如何處理 Word 文件的應用程式層級事件。 `CreateDocument` 方法會建立新文件，然後定義防止儲存這份文件的 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 事件處理常式。 因為這是針對 <xref:Microsoft.Office.Interop.Word.Application> 物件引發的應用程式層級事件，所以事件處理常式必須將 `Doc` 參數與 `document1` 物件進行比較，以判斷 `document1` 是否代表儲存的文件。  
  
 [!code-vb[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#12)]
 [!code-csharp[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#12)]  
  
### <a name="examples-that-use-a-host-item"></a>主項目的使用範例  
 下列程式碼範例透過處理 <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> 主項目的 <xref:Microsoft.Office.Tools.Word.Document> 事件，來簡化這個程序。 這些範例中的 `CreateDocument2` 方法會產生可擴充 <xref:Microsoft.Office.Tools.Word.Document> 物件的 `document2` ，然後定義防止儲存這份文件的 <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> 事件處理常式。 因為只有在儲存 `document2` 時才會呼叫這個事件處理常式，所以事件處理常式可以直接取消儲存動作，而不需要執行任何額外的工作來確認已儲存哪個文件。  
  
 下列程式碼範例示範這項工作。  
  
 [!code-vb[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#13)]
 [!code-csharp[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#13)]  
  
##  <a name="HasVstoObject"></a> 判斷是否已擴充 Office 物件  
 若要判斷擴充的物件是否已產生特定的原生 Office 物件，請使用 HasVstoObject 方法。 如果已產生擴充物件，這個方法會傳回 **true** ，否則會傳回 **false**。  
  
 使用 Globals.Factory.HasVstoMethod 方法。 傳入您要針對擴充物件測試的原生 Word 或 Excel 物件，例如 <xref:Microsoft.Office.Interop.Word.Document> 或 <xref:Microsoft.Office.Interop.Excel.Worksheet>。  
  
 HasVstoObject 方法時，您想要在指定的 Office 物件具有擴充的物件時，才執行程式碼。 例如，如果您有 Word VSTO 增益集處理<xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>儲存事件從之前的文件移除 managed 的控制項，您可用來判斷是否已擴充該文件 HasVstoObject 方法。 如果文件尚未擴充，便無法包含 Managed 控制項，因此事件處理常式可能會直接傳回，而不嘗試清除文件上的控制項。  
  
## <a name="see-also"></a>另請參閱  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [在執行階段將控制項加入 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)  
  
  