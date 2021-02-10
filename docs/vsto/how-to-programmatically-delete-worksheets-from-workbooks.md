---
title: 如何：以程式設計方式從活頁簿中刪除工作表
description: 您可以使用工作表主專案，瞭解如何以程式設計的方式刪除 Microsoft Excel 活頁簿中的任何工作表。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2289309932dcd1d946fc775de60a0e07892be222
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963884"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>如何：以程式設計方式從活頁簿中刪除工作表
  您可以刪除活頁簿中的任何工作表。 若要刪除工作表，請使用工作表主項目，或使用活頁簿的工作表集合存取工作表。

 [!INCLUDE[appliesto_xlalldocapp](includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>使用工作表主專案
 如果在文件層級自訂的執行階段即已加入工作表，請使用 <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> 方法刪除指定的工作表。 下列程式碼會直接參考工作表主項目，從活頁簿中刪除工作表。

> [!IMPORTANT]
> 只有在使用下列任何專案範本建立的專案中，才能執行此程式碼：
>
> - Excel 2013 活頁簿
> - Excel 2013 範本
> - Excel 2010 活頁簿
> - Excel 2010 範本
>
>   如果您想要在任何其他類型的專案中執行這項工作，您必須將參考加入至 node.js 元件，然後必須使用該元件 **中的類別** 開啟活頁簿，並刪除工作表。 如需詳細資訊，請參閱 [如何：透過主要 interop 元件以 Office 應用程式為目標](how-to-target-office-applications-through-primary-interop-assemblies.md) 和 [Excel 2010 主要 interop 元件參考](office-primary-interop-assemblies.md)。

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>使用工作表主項目刪除工作表

1. 呼叫 <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> 的 `Sheet1`方法。

     [!code-csharp[Trin_VstcoreExcelAutomation#17](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>使用 Excel 活頁簿的工作表集合
 在下列情況中，透過 Microsoft Office Excel 的 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合存取工作表：

- 您要刪除 VSTO 增益集的工作表。

- 您想要刪除的工作表，是在文件層級自訂的執行階段建立的。

  下列程式碼會 **透過工作表集合的** 索引編號參考工作表，從活頁簿刪除工作表。 這個程式碼會假設新的工作表是以程式設計方式建立的。

> [!IMPORTANT]
> 如果您想要在任何其他類型的專案中執行這項工作，您必須將參考加入至 node.js 元件，然後必須使用該元件 **中的類別** 開啟活頁簿，並刪除工作表。 如需詳細資訊，請參閱 [如何：透過主要 interop 元件以 Office 應用程式為目標](how-to-target-office-applications-through-primary-interop-assemblies.md) 和 [Excel 2010 主要 interop 元件參考](office-primary-interop-assemblies.md)。

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>使用 Excel 活頁簿的工作表集合刪除工作表

1. 呼叫 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合的 <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> 方法。

     [!code-csharp[Trin_VstcoreExcelAutomation#18](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]

## <a name="see-also"></a>另請參閱
- [使用工作表](working-with-worksheets.md)
- [如何：以程式設計方式隱藏工作表](how-to-programmatically-hide-worksheets.md)
- [如何：以程式設計方式在活頁簿內移動工作表](how-to-programmatically-move-worksheets-within-workbooks.md)
- [如何：以程式設計方式選取工作表](how-to-programmatically-select-worksheets.md)
- [如何：以程式設計方式在活頁簿中加入新的工作表](how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [工作表主專案](worksheet-host-item.md)
- [全域存取 Office 專案中的物件](global-access-to-objects-in-office-projects.md)
- [主專案和主控制項的程式設計限制](programmatic-limitations-of-host-items-and-host-controls.md)
