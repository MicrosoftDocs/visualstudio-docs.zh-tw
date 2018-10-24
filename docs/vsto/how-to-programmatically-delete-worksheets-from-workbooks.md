---
title: 如何： 以程式設計方式從活頁簿中刪除工作表
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 73c501d545f76012b63bde291001b38c214c3eb6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950221"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>如何： 以程式設計方式從活頁簿中刪除工作表
  您可以刪除活頁簿中的任何工作表。 若要刪除工作表，請使用工作表主項目，或使用活頁簿的工作表集合存取工作表。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-the-worksheet-host-item"></a>使用工作表主項目  
 如果在文件層級自訂的設計階段即已加入工作表，請使用 <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> 方法刪除指定的工作表。 下列程式碼會直接參考工作表主項目，從活頁簿中刪除工作表。  
  
> [!IMPORTANT]
>  只有在使用下列任一專案範本建立的專案中，才能執行此程式碼：  
> 
> - Excel 2013 活頁簿  
> - Excel 2013 範本  
> - Excel 2010 活頁簿  
> - Excel 2010 範本  
> 
>   如果您想要執行這項工作中任何其他類型的專案，您必須加入參考**Microsoft.Office.Interop.Excel**組件，然後您必須使用該組件中的類別來開啟活頁簿和刪除工作表。 如需詳細資訊，請參閱 <<c0> [ 如何： 透過主要 interop 組件的目標 Office 應用程式](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)並[Excel 2010 主要 interop 組件參考](http://go.microsoft.com/fwlink/?LinkId=189585)。  
  
### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>使用工作表主項目刪除工作表  
  
1.  呼叫 <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> 的 `Sheet1`方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]  
  
## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>使用 Excel 活頁簿的工作表集合  
 在下列情況中，透過 Microsoft Office Excel 的 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合存取工作表：  
  
- 您要刪除 VSTO 增益集的工作表。  
  
- 您想要刪除的工作表，是在文件層級自訂的執行階段建立的。  
  
  下列程式碼從活頁簿刪除工作表，藉由參考至索引數目的工作表**試算表**集合。 這個程式碼會假設新的工作表是以程式設計方式建立的。  
  
> [!IMPORTANT]  
>  如果您想要執行這項工作中任何其他類型的專案，您必須加入參考**Microsoft.Office.Interop.Excel**組件，然後您必須使用該組件中的類別來開啟活頁簿和刪除工作表。 如需詳細資訊，請參閱 <<c0> [ 如何： 透過主要 interop 組件的目標 Office 應用程式](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)並[Excel 2010 主要 interop 組件參考](http://go.microsoft.com/fwlink/?LinkId=189585)。  
  
### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>使用 Excel 活頁簿的工作表集合刪除工作表  
  
1.  呼叫 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合的 <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]  
  
## <a name="see-also"></a>另請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何： 以程式設計方式隱藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)   
 [如何： 以程式設計方式移動工作表在活頁簿內](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [如何： 以程式設計方式選取工作表](../vsto/how-to-programmatically-select-worksheets.md)   
 [如何： 以程式設計方式在活頁簿中加入新的工作表](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [工作表主項目](../vsto/worksheet-host-item.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  