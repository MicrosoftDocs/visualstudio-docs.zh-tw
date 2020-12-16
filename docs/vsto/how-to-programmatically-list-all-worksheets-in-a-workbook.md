---
title: 如何：以程式設計方式列出活頁簿中的所有工作表
description: 瞭解如何使用 Visual Studio，以程式設計方式列出 Microsoft Excel 活頁簿中的所有工作表。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing worksheets
- worksheets, listing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 74ff02d6458e643e9a143a8132ad16f10899ec74
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525664"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>如何：以程式設計方式列出活頁簿中的所有工作表
  <xref:Microsoft.Office.Interop.Excel.Workbook> 類別會提供 <xref:Microsoft.Office.Interop.Excel.Worksheets> 物件。 這個物件在活頁簿中含有所有 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件的集合。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>若要在文件層級自訂中列出活頁簿的全部現有工作表

1. 在 <xref:Microsoft.Office.Interop.Excel.Worksheets> 集合中逐一查看每個工作表的名稱，並將名稱傳送到從 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項位移 (Offset) 的儲存格。

     [!code-csharp[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#21)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>若要在 VSTO 增益集中列出活頁簿的全部現有工作表

1. 在 <xref:Microsoft.Office.Interop.Excel.Worksheets> 集合中逐一查看每個工作表的名稱，並將名稱傳送到與 <xref:Microsoft.Office.Interop.Excel.Range> 物件相距某位移的儲存格。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#13)]

## <a name="see-also"></a>另請參閱
- [使用工作表](../vsto/working-with-worksheets.md)
- [如何：以程式設計方式在活頁簿中加入新的工作表](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [如何：以程式設計方式在活頁簿內移動工作表](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)
