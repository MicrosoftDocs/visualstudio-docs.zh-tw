---
title: 如何：以程式設計方式移除工作表的保護
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 72448f9d1e5c24c917459b8c2c59e317190e0a11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85519869"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>如何：以程式設計方式移除工作表的保護
  您可以程式設計的方式，移除 Microsoft Office Excel 工作表保護。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 下例使用的變數 `getPasswordFromUser`，包含從使用者處取得的密碼。

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>取消文件層級自訂工作表的保護

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A>如有需要，請呼叫工作表的方法並傳入密碼。 這個範例會假設您是使用名為 `Sheet1`的工作表。

     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>若要取消保護 VSTO 增益集中的工作表

1. <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A>如有需要，請呼叫活動工作表的方法並傳入密碼。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]

## <a name="see-also"></a>另請參閱
- [使用工作表](../vsto/working-with-worksheets.md)
- [如何：以程式設計方式保護工作表](../vsto/how-to-programmatically-protect-worksheets.md)
- [如何：以程式設計方式保護活頁簿](../vsto/how-to-programmatically-protect-workbooks.md)
- [如何：以程式設計方式隱藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)
- [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)
