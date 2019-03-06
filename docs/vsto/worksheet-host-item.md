---
title: 工作表主項目
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e4a5287648d515d1aca340ab55d5f21b494610b5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56612474"
---
# <a name="worksheet-host-item"></a>工作表主項目
  <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目是可從 Excel 的主要 Interop 組件擴充 <xref:Microsoft.Office.Interop.Excel.Worksheet> 類型的一種類型。 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目除了提供與 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件相同的所有屬性、方法和事件之外，也會公開其他事件，並做為主控制項和 Windows Form 控制項的容器。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 在文件層級專案中，您可以在設計階段將 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目加入專案。 在 VSTO 增益集專案中，您可以產生<xref:Microsoft.Office.Tools.Excel.Worksheet>裝載在執行階段的項目。

## <a name="understand-worksheet-host-items-in-document-level-projects"></a>了解文件層級專案中的 worksheet 主項目
 當您建立 Excel 的文件層級專案時，Visual Studio 會自動在專案中建立三個 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。 這些工作表的預設名稱為 `Sheet1`、 `Sheet2`和 `Sheet3`。 如果您根據現有的活頁簿建立專案，主項目的數目取決於活頁簿中的工作表數目。

 這些工作表類別可讓您存取 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目的成員，以便在自訂中執行基本工作，例如修改工作表的內容。 您也可以使用這些類別將控制項加入工作表。 藉由結合不同組的控制項並撰寫程式碼，您可以將控制項繫結至資料、從使用者收集資訊，以及回應使用者動作。 如需詳細資訊，請參閱 <<c0> [ 程式的文件層級自訂](../vsto/programming-document-level-customizations.md)。

 工作表類別提供了一個位置，供您開始在專案中撰寫程式碼。 由於該類別會提供與 Excel 之主要 Interop 組件中的 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件相同的所有屬性、方法和事件，因此您也可以使用這些類別存取 Excel 的物件模型。 如需詳細資訊，請參閱 < [Excel 物件模型概觀](../vsto/excel-object-model-overview.md)。

 在文件層級專案中，您可以在設計階段將其他 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目加入專案，方法是在設計工具中將新的工作表加入活頁簿。

### <a name="rename-worksheets"></a>重新命名工作表
 在文件層級專案中，您可以於 Visual Studio 設計工具中為工作表重新命名，但這樣做只會變更工作表的顯示名稱。 程式設計名稱仍是工作表的預設名稱。 如果您在 [屬性]  視窗中為工作表重新命名，則只會變更程式設計名稱。

### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>限制的文件層級專案中工作表主項目
 您無法建立新<xref:Microsoft.Office.Tools.Excel.Worksheet>裝載在執行階段在文件層級專案中的項目。 如果您在執行階段建立新的 Excel 工作表，其將會是型別<xref:Microsoft.Office.Interop.Excel.Worksheet>。 由於這不是主項目，因此無法包含任何主控制項或 Windows Forms 控制項。 如需在執行階段建立文件的詳細資訊，請參閱[How to:以程式設計方式在活頁簿中加入新的工作表](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)。

## <a name="understand-worksheet-host-items-in-vsto-add-in-projects"></a>了解 VSTO 增益集專案中的 worksheet 主項目
 在應用程式層級專案中，您可以在執行階段為使用 Excel 開啟的任何工作表產生 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。 您可以使用 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目將控制項加入相關聯的工作表，或處理 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件上沒有的事件。

 若要產生 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目，請使用 `GetVstoObject` 方法。 如需詳細資訊，請參閱 <<c0> [ 擴充 Word 文件和 VSTO 增益集在執行階段中的 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。

## <a name="see-also"></a>另請參閱
- [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)
- [擴充 Word 文件和 Excel 活頁簿，VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office 文件上的控制項](../vsto/controls-on-office-documents.md)
- [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)
- [Workbook 主項目](../vsto/workbook-host-item.md)
- [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
