---
title: "工作表主項目 |Microsoft 文件"
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
- host items [Office development in Visual Studio], Worksheet
- Excel [Office development in Visual Studio], worksheets
- Worksheet host items
- worksheets, events
- Worksheet host items, events
- Excel worksheets
- worksheets, Excel
- worksheets
- events [Office development in Visual Studio]
ms.assetid: b4f7c501-81f5-409e-aa1b-748f010798b9
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ce07e378d13f12300f9b3a207f7e31de9d5b9936
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="worksheet-host-item"></a>Worksheet 主項目
  <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目是可從 Excel 的主要 Interop 組件擴充 <xref:Microsoft.Office.Interop.Excel.Worksheet> 類型的一種類型。 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目除了提供與 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件相同的所有屬性、方法和事件之外，也會公開其他事件，並做為主控制項和 Windows Form 控制項的容器。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 在文件層級專案中，您可以在設計階段將 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目加入專案。 在 VSTO 增益集專案中，您可以在執行階段產生 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。  
  
## <a name="understanding-worksheet-host-items-in-document-level-projects"></a>了解文件層級專案中的 Worksheet 主項目  
 當您建立 Excel 的文件層級專案時，Visual Studio 會自動在專案中建立三個 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。 這些工作表的預設名稱為 `Sheet1`、 `Sheet2`和 `Sheet3`。 如果您根據現有的活頁簿建立專案，主項目的數目取決於活頁簿中的工作表數目。  
  
 這些工作表類別可讓您存取 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目的成員，以便在自訂中執行基本工作，例如修改工作表的內容。 您也可以使用這些類別將控制項加入工作表。 藉由結合不同組的控制項並撰寫程式碼，您可以將控制項繫結至資料、從使用者收集資訊，以及回應使用者動作。 如需詳細資訊，請參閱 [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)。  
  
 工作表類別提供了一個位置，供您開始在專案中撰寫程式碼。 由於該類別會提供與 Excel 之主要 Interop 組件中的 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件相同的所有屬性、方法和事件，因此您也可以使用這些類別存取 Excel 的物件模型。 如需詳細資訊，請參閱 [Excel Object Model Overview](../vsto/excel-object-model-overview.md)。  
  
 在文件層級專案中，您可以在設計階段將其他 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目加入專案，方法是在設計工具中將新的工作表加入活頁簿。  
  
### <a name="renaming-worksheets"></a>重新命名工作表  
 在文件層級專案中，您可以於 Visual Studio 設計工具中為工作表重新命名，但這樣做只會變更工作表的顯示名稱。 程式設計名稱仍是工作表的預設名稱。 如果您在 [屬性]  視窗中為工作表重新命名，則只會變更程式設計名稱。  
  
### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>文件層級專案中 Worksheet 主項目的限制  
 您無法在文件層級專案的執行階段建立新的 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。 如果您在執行階段建立新的 Excel 工作表，該工作表會是 <xref:Microsoft.Office.Interop.Excel.Worksheet>類型。 由於這不是主項目，因此無法包含任何主控制項或 Windows Form 控制項。 如需有關如何在執行階段建立文件的詳細資訊，請參閱[How to： 以程式設計方式加入新的工作表為活頁簿](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)。  
  
## <a name="understanding-worksheet-host-items-in-vsto-add-in-projects"></a>了解 VSTO 增益集專案中的 Worksheet 主項目  
 在應用程式層級專案中，您可以在執行階段為使用 Excel 開啟的任何工作表產生 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。 您可以使用 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目將控制項加入相關聯的工作表，或處理 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件上沒有的事件。  
  
 若要產生<xref:Microsoft.Office.Tools.Excel.Worksheet>主項目，請使用 GetVstoObject 方法。 如需詳細資訊，請參閱 [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)   
 [在執行階段擴充 Word 文件和 Excel 活頁簿，在 VSTO 增益集](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [在執行階段將控制項加入 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Workbook 主項目](../vsto/workbook-host-item.md)   
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  