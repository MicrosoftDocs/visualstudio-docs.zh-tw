---
title: 如何：以程式設計方式保護活頁簿
description: 瞭解如何保護 Microsoft Excel 活頁簿，讓使用者無法新增或刪除工作表，也可以程式設計方式取消保護活頁簿。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9f0b479c56be6da7b14f87263c8c01d66910ac20
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827103"
---
# <a name="how-to-programmatically-protect-workbooks"></a>如何：以程式設計方式保護活頁簿
  您可以保護 Microsoft Office Excel 活頁簿，讓使用者無法新增或刪除工作表，也可以程式設計的方式取消保護活頁簿。 您可以選擇性地指定密碼、指出您是否想要 (結構，讓使用者無法將工作表移至) ，並指出您是否要保護活頁簿的 windows。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 保護活頁簿不會阻止使用者編輯儲存格。 若要保護資料，您必須保護工作表。 如需詳細資訊，請參閱 [如何：以程式設計方式保護工作表](../vsto/how-to-programmatically-protect-worksheets.md)。

 下列程式碼範例會使用變數來包含從使用者取得的密碼。

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>保護屬於檔層級自訂一部分的活頁簿

### <a name="to-protect-a-workbook"></a>保護活頁簿

1. 呼叫活頁 <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> 簿的方法，並包含密碼。 若要使用下列程式碼範例，請在類別中執行， `ThisWorkbook` 而不是在工作表類別中執行。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet10":::

### <a name="to-unprotect-a-workbook"></a>取消保護活頁簿

1. 呼叫 <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> 方法，並傳遞密碼（如果需要的話）。 若要使用下列程式碼範例，請在類別中執行， `ThisWorkbook` 而不是在工作表類別中執行。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet11":::

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>使用應用層級增益集保護活頁簿

### <a name="to-protect-a-workbook"></a>保護活頁簿

1. 呼叫活頁 <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> 簿的方法，並包含密碼。 這個程式碼範例會使用活動活頁簿。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet6":::

### <a name="to-unprotect-a-workbook"></a>取消保護活頁簿

1. 呼叫使用 <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> 中活頁簿的方法，並傳遞密碼（如果需要的話）。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet7":::

## <a name="see-also"></a>另請參閱
- [使用活頁簿](../vsto/working-with-workbooks.md)
- [如何：以程式設計方式保護工作表](../vsto/how-to-programmatically-protect-worksheets.md)
- [如何：以程式設計方式隱藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
