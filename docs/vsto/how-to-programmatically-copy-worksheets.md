---
title: 如何：以程式設計方式複製工作表
description: 瞭解如何建立工作表的複本，並將該工作表插入活頁簿中現有的工作表之前或之後。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: d4b2f16cfc8855f2adff3a4614c38eb70fbe7db5
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524793"
---
# <a name="how-to-programmatically-copy-worksheets"></a>如何：以程式設計方式複製工作表
  您可以建立一份工作表，並將其插入活頁簿中現有工作表的前面或後面。 如不指定工作表的插入位置，Excel 會建立新的活頁簿以收納新的工作表。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

> [!NOTE]
> 無論您是以程式設計的方式複製工作表，或是使用者手動複製工作表，新的工作表背後都沒有程式碼，而新工作表上的控制項也不會作用。 這是因為新複製的工作表是 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件，不是 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。 Windows Form 控制項和主控制項只能加入主項目。 如需詳細資訊，請參閱 [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。

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
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [如何：以程式設計方式在活頁簿中加入新的工作表](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [如何：以程式設計方式從活頁簿中刪除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [如何：以程式設計方式選取工作表](../vsto/how-to-programmatically-select-worksheets.md)
- [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
