---
title: HOW TO：以程式設計方式移除工作表的保護
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ccf7de70c3ef741119ec22f8fa9bc76868a47030
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084215"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>HOW TO：以程式設計方式移除工作表的保護
  您可以程式設計的方式，移除 Microsoft Office Excel 工作表保護。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 下例使用的變數 `getPasswordFromUser`，包含從使用者處取得的密碼。

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>取消文件層級自訂工作表的保護

1. 呼叫<xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A>的工作表並傳入密碼，如有必要的方法。 這個範例會假設您是使用名為 `Sheet1`的工作表。

     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>若要取消保護工作表中的 VSTO 增益集

1. 呼叫<xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A>現用工作表和傳入密碼，如有必要的方法。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]

## <a name="see-also"></a>另請參閱
- [使用工作表](../vsto/working-with-worksheets.md)
- [如何：以程式設計方式保護工作表](../vsto/how-to-programmatically-protect-worksheets.md)
- [如何：以程式設計方式保護活頁簿](../vsto/how-to-programmatically-protect-workbooks.md)
- [如何：以程式設計方式隱藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)
- [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)
