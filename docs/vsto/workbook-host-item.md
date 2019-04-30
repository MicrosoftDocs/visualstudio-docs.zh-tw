---
title: Workbook 主項目
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel workbooks
- Workbook host items
- host items [Office development in Visual Studio], Workbook
- workbooks, Excel
- Workbook host items, events
- workbooks
- Excel [Office development in Visual Studio], workbooks
- workbooks, events
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e30ab9ce498134426caa35e0c3c9f9652f683535
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445527"
---
# <a name="workbook-host-item"></a>Workbook 主項目
  <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目是可從 Excel 的主要 Interop 組件擴充 <xref:Microsoft.Office.Interop.Excel.Workbook> 類型的一種類型。 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目除了提供與 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件相同的所有屬性、方法和事件之外，也會提供其他功能。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 文件層級專案中有代表專案中活頁簿的預設 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目。 在 VSTO 增益集專案中，您可以產生<xref:Microsoft.Office.Tools.Excel.Workbook>裝載在執行階段的項目。

## <a name="understand-the-workbook-host-item-in-document-level-projects"></a>了解文件層級專案中的 workbook 主項目
 若要存取專案中的活頁簿，請使用 `ThisWorkbook` 類別。 `ThisWorkbook` 類別可讓您存取 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目的成員，以在自訂中執行基本工作，例如在開啟或關閉活頁簿時執行程式碼。 如需詳細資訊，請參閱 <<c0> [ 程式的文件層級自訂](../vsto/programming-document-level-customizations.md)。

 `ThisWorkbook` 類別提供了一個位置，供您開始在專案中撰寫程式碼。 由於該類別會提供與 Excel 之主要 Interop 組件中的 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件相同的所有屬性、方法和事件，因此您也可以使用 `ThisWorkbook` 存取 Excel 的物件模型。 如需詳細資訊，請參閱 < [Excel 物件模型概觀](../vsto/excel-object-model-overview.md)。

 按兩下 [方案總管]  中的 [ThisWorkbook]  專案項目以顯示活頁簿設計工具，並在 [屬性]  視窗中檢視活頁簿的屬性和事件。

### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>限制的文件層級專案中的 workbook 主項目
 文件層級專案只能包含一個 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目 (也就是 `ThisWorkbook` 類別)。 您無法加入新<xref:Microsoft.Office.Tools.Excel.Workbook>在設計階段，主機項目至您的專案，並在您無法建立新<xref:Microsoft.Office.Tools.Excel.Workbook>裝載在執行階段從 文件層級自訂的項目。

 如果您在執行階段建立新的 Excel 活頁簿，其將會是型別<xref:Microsoft.Office.Interop.Excel.Workbook>。 由於這不是主項目，因此無法包含任何主控制項或 Windows Forms 控制項。 如需在執行階段建立活頁簿的詳細資訊，請參閱[How to:以程式設計方式建立新的活頁簿](../vsto/how-to-programmatically-create-new-workbooks.md)。

 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目不能做為主控制項的容器。 因此，您無法將任何可見的控制項加入活頁簿，但您可以加入 <xref:System.Data.DataSet>等元件，讓所有工作表都能共用這些元件。 在文件層級專案中，您可以在 [工具箱]  的 [元件]  索引標籤、[資料]  索引標籤和 [所有 Windows Forms] 索引標籤上，找到活頁簿可用的元件。

> [!NOTE]
> Visual Studio 中的 Office 開發工具不支援共用活頁簿。

## <a name="understand-workbook-host-items-in-vsto-add-in-projects"></a>了解 VSTO 增益集專案中的 workbook 主項目
 在 VSTO 增益集專案中，您可以產生<xref:Microsoft.Office.Tools.Excel.Workbook>在執行階段是在 Excel 中開啟任何活頁簿的主項目。 若要產生 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目，請使用 `GetVstoObject` 方法。 如需詳細資訊，請參閱 <<c0> [ 擴充 Word 文件和 VSTO 增益集在執行階段中的 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。

## <a name="see-also"></a>另請參閱
- [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)
- [擴充 Word 文件和 Excel 活頁簿，VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)
- [工作表主項目](../vsto/worksheet-host-item.md)
- [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
