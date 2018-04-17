---
title: 如何： 以程式設計方式複製資料和格式跨工作表 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 10a710af8120ab789ec3a9c3ccb2b7e4398e82f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>如何：以程式設計方式跨工作表複製資料和格式
  您可以從上一個工作表範圍複製資料，所有其他工作表在活頁簿中，使用<xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A>方法。 指定範圍，以及您是否要複製資料、 格式設定，或兩者。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要名為範圍`rangeData`工作表中。  
  
## <a name="see-also"></a>另請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何： 以程式設計方式在活頁簿中加入新的工作表](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [如何： 以程式設計方式變更工作表包含選取儲存格的資料列中的格式](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  