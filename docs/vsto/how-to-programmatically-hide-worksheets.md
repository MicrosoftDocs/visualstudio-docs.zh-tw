---
title: "如何： 以程式設計方式隱藏工作表 |Microsoft 文件"
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
- hidden worksheets
- worksheets, hiding
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1ce83d6cec246a5a232026dff4e11f3dc1ed9e06
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-hide-worksheets"></a>如何：以程式設計方式隱藏工作表
  您可以顯示或隱藏活頁簿中的任何工作表。 若要隱藏工作表，請使用工作表主項目，或使用活頁簿的工作表集合存取工作表。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-the-worksheet-host-item"></a>使用工作表主項目  
 如果在文件層級自訂的設計階段即已加入工作表，請使用 <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> 屬性隱藏指定的工作表。  
  
#### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>使用工作表主項目隱藏工作表  
  
1.  將 <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> 主項目的 `Sheet1` 屬性設定為 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> 列舉值。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]  
  
## <a name="using-the-sheets-collection-of-the-excel-workbook"></a>使用 Excel 活頁簿的工作表集合  
 在下列情況中，透過 Microsoft Office Excel 的 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合存取工作表：  
  
-   您要隱藏 VSTO 增益集的工作表。  
  
-   您想要隱藏的工作表，是在文件層級自訂的執行階段建立的。  
  
#### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>使用 Excel 活頁簿的工作表集合隱藏工作表  
  
1.  將工作表的 <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> 屬性設定為 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> 列舉值。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]  
  
## <a name="see-also"></a>請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何： 以程式設計方式從活頁簿刪除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [如何： 以程式設計方式移動工作表中的活頁簿](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [如何： 以程式設計方式保護工作表](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)  
  