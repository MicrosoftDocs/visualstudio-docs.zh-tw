---
title: 如何：以程式設計方式關閉活頁簿
description: 瞭解如何關閉使用中的活頁簿，或指定要以程式設計方式關閉的活頁簿。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 13b487054e4e8a12c2479ddfc167ca0b8e90285a
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846054"
---
# <a name="how-to-programmatically-close-workbooks"></a>如何：以程式設計方式關閉活頁簿
  您可以關閉現用活頁簿，或是指定要關閉的活頁簿。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="close-the-active-workbook"></a>關閉現用活頁簿
 有兩種程序可以關閉現用活頁簿：一個適用於文件層級自訂，而另一個適用於 VSTO 增益集。

### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>若要透過文件層級自訂關閉現用活頁簿

1. 呼叫 <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> 方法，關閉與該自訂相關聯的活頁簿。 若要使用下列程式碼範例，請在 Excel 文件層級專案的 `Sheet1` 類別中執行程式碼。

     [!code-csharp[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#3)]

### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>若要透過 VSTO 增益集關閉現用活頁簿

1. 呼叫 <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> 方法，關閉使用中的活頁簿。 若要使用下列程式碼範例，請在 Excel VSTO 增益集專案的 `ThisAddIn` 類別中執行程式碼。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#1)]

## <a name="close-a-workbook-that-you-specify-by-name"></a>關閉您依名稱指定的活頁簿
 對 VSTO 增益集和文件層級自訂而言，依指定名稱關閉活頁簿的方式都是相同的。

### <a name="to-close-a-workbook-that-you-specify-by-name"></a>若要依指定名稱關閉活頁簿

1. 將活頁簿名稱指定為 <xref:Microsoft.Office.Interop.Excel.Workbooks> 集合的引數。 下列程式碼範例假設在 Excel 中開啟了名為 **NewWorkbook** 的活頁簿。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#2)]

## <a name="see-also"></a>另請參閱
- [使用活頁簿](../vsto/working-with-workbooks.md)
- [如何：以程式設計方式儲存活頁簿](../vsto/how-to-programmatically-save-workbooks.md)
- [如何：以程式設計方式開啟活頁簿](../vsto/how-to-programmatically-open-workbooks.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
