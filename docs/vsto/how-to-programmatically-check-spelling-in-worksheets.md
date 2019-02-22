---
title: HOW TO：以程式設計方式檢查工作表拼字
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- spellchecking
- spelling checker, worksheets
- worksheets, checking spelling
- spelling, checking in worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93a9377579e9b299fd2a3b0a34e8e90a1f7f2bb6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633261"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>HOW TO：以程式設計方式檢查工作表拼字
  您可以用程式設計方式檢查工作表中的拼字。 如果工作表中有任何拼寫不正確的字，[拼字檢查]  對話方塊就會自動出現。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>在文件層級自訂中檢查工作表的拼字

1.  呼叫工作表的 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> 方法。

     [!code-csharp[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#45)]
     [!code-vb[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#45)]

## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>若要在 VSTO 增益集的工作表中檢查拼字

1.  呼叫使用中工作表的 <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> 方法。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#22)]

## <a name="see-also"></a>另請參閱
- [使用工作表](../vsto/working-with-worksheets.md)
- [如何：以程式設計方式執行 Excel 計算](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
