---
title: 如何：以程式設計方式檢查工作表中的拼寫
description: 瞭解如何以程式設計方式檢查 Microsoft Excel 工作表中的單字拼寫。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1bf35e225def686ae2424a89b7e5d6b77207ccee
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826053"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>如何：以程式設計方式檢查工作表中的拼寫
  您可以用程式設計方式檢查工作表中的拼字。 如果工作表中有任何拼寫不正確的字，[拼字檢查]  對話方塊就會自動出現。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>在文件層級自訂中檢查工作表的拼字

1. 呼叫工作表的 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> 方法。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet45":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet45":::

## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>若要在 VSTO 增益集中檢查工作表中的拼寫

1. 呼叫使用中工作表的 <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> 方法。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet22":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet22":::

## <a name="see-also"></a>另請參閱
- [使用工作表](../vsto/working-with-worksheets.md)
- [如何：以程式設計方式執行 Excel 計算](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
