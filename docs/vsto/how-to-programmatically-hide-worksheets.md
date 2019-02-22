---
title: HOW TO：以程式設計方式隱藏工作表
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 188c7fbf16002086a4968b91c068cd67357292de
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870489"
---
# <a name="how-to-programmatically-hide-worksheets"></a>HOW TO：以程式設計方式隱藏工作表
  您可以顯示或隱藏活頁簿中的任何工作表。 若要隱藏工作表，請使用工作表主項目，或使用活頁簿的工作表集合存取工作表。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-the-worksheet-host-item"></a>使用工作表主項目  
 如果在文件層級自訂的設計階段即已加入工作表，請使用 <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> 屬性隱藏指定的工作表。  
  
### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>使用工作表主項目隱藏工作表  
  
1.  將 <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> 主項目的 `Sheet1` 屬性設定為 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> 列舉值。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]  
  
## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>使用 Excel 活頁簿的工作表集合  
 在下列情況中，透過 Microsoft Office Excel 的 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合存取工作表：  
  
-   您想要隱藏工作表中的 VSTO 增益集。  
  
-   您想要隱藏的工作表，是在文件層級自訂的執行階段建立的。  
  
### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>使用 Excel 活頁簿的工作表集合隱藏工作表  
  
1.  將工作表的 <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> 屬性設定為 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> 列舉值。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]  
  
## <a name="see-also"></a>另請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以程式設計方式從活頁簿中刪除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [如何：以程式設計方式移動工作表在活頁簿內](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [如何：以程式設計方式保護工作表](../vsto/how-to-programmatically-protect-worksheets.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)  
