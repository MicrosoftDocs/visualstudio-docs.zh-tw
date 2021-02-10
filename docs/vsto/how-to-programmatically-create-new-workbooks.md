---
title: 如何：以程式設計方式建立新的活頁簿
description: 瞭解如何使用 Visual Studio，以程式設計方式建立新的 Microsoft Excel 活頁簿。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 13acd34d9883cfdc7df201dff193d261252f8a9d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963987"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>如何：以程式設計方式建立新的活頁簿
  當您以程式設計方式建立活頁簿時，它就是原生的 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件，不是 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 您可以在 VSTO 增益集專案中，為 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件產生 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目。 如需詳細資訊，請參閱 [在 VSTO 增益集中，于執行時間擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。

## <a name="to-create-a-new-workbook"></a>建立新的活頁簿

1. 使用 <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> 集合的 <xref:Microsoft.Office.Interop.Excel.Workbooks> 方法。

     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]

    > [!NOTE]
    > 您可以根據預設範本以外的範本建立活頁簿：將要用的範本當成參數傳遞至 <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> 方法。

## <a name="see-also"></a>另請參閱
- [在 VSTO 增益集的執行時間中擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [在執行時間將控制項新增至 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [使用活頁簿](../vsto/working-with-workbooks.md)
- [如何：以程式設計方式開啟活頁簿](../vsto/how-to-programmatically-open-workbooks.md)
- [如何：以程式設計方式儲存活頁簿](../vsto/how-to-programmatically-save-workbooks.md)
- [如何：以程式設計方式關閉活頁簿](../vsto/how-to-programmatically-close-workbooks.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
