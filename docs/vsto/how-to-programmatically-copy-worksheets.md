---
title: HOW TO：以程式設計方式複製工作表
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 305f24204c1be7186b2d2d49fa61a0c32c52c8cb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104391"
---
# <a name="how-to-programmatically-copy-worksheets"></a>HOW TO：以程式設計方式複製工作表
  您可以建立一份工作表，並將其插入活頁簿中現有工作表的前面或後面。 如不指定工作表的插入位置，Excel 會建立新的活頁簿以收納新的工作表。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

> [!NOTE]
>  無論您是以程式設計的方式複製工作表，或是使用者手動複製工作表，新的工作表背後都沒有程式碼，而新工作表上的控制項也不會作用。 這是因為新複製的工作表是 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件，不是 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。 Windows Form 控制項和主控制項只能加入主項目。 如需詳細資訊，請參閱 <<c0> [ 主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>在文件層級自訂的活頁簿中加入複製的工作表

1. 使用 <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> 方法複製目前活頁簿中的第一張工作表，並將複本放在第三張工作表之後。

     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>將複製的工作表加入 VSTO 增益集活頁簿

1. 使用 <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> 方法複製目前活頁簿中的第一張工作表，並將複本放在第三張工作表之後。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]

## <a name="see-also"></a>另請參閱
- [使用工作表](../vsto/working-with-worksheets.md)
- [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)
- [如何：以程式設計方式在活頁簿中加入新的工作表](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [如何：以程式設計方式從活頁簿中刪除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [如何：以程式設計方式選取工作表](../vsto/how-to-programmatically-select-worksheets.md)
- [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)
- [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
