---
title: HOW TO：以程式設計方式保護活頁簿
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5333504ed534373b6bb65902edb2566953de7a59
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863678"
---
# <a name="how-to-programmatically-protect-workbooks"></a>HOW TO：以程式設計方式保護活頁簿
  您可以保護 Microsoft Office Excel 活頁簿，以便讓使用者無法加入或刪除工作表，並也以程式設計方式取消保護活頁簿。 或者，您可以指定密碼，指出您是否要保護 （讓使用者無法移動工作表），這個結構，以及表示是否要讓受保護的活頁簿的視窗。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 保護活頁簿並不會防止使用者編輯儲存格。 若要保護的資料，您必須保護工作表。 如需詳細資訊，請參閱[＜How to：以程式設計方式保護工作表](../vsto/how-to-programmatically-protect-worksheets.md)。  
  
 下列程式碼範例會使用變數來包含取自於使用者的密碼。  
  
## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>保護文件層級自訂一部分的活頁簿  
  
### <a name="to-protect-a-workbook"></a>若要保護的活頁簿  
  
1.  呼叫<xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A>活頁簿的方法，並包含密碼。 若要使用下列程式碼範例，在中執行`ThisWorkbook`類別，不會在工作表類別。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]  
  
### <a name="to-unprotect-a-workbook"></a>若要取消保護活頁簿  
  
1.  呼叫<xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A>方法，傳遞所需的密碼。 若要使用下列程式碼範例，在中執行`ThisWorkbook`類別，不會在工作表類別。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]  
  
## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>使用應用程式層級增益集來保護活頁簿  
  
### <a name="to-protect-a-workbook"></a>若要保護的活頁簿  
  
1.  呼叫<xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A>活頁簿的方法，並包含密碼。 此程式碼範例會使用目前的活頁簿。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]  
  
### <a name="to-unprotect-a-workbook"></a>若要取消保護活頁簿  
  
1.  呼叫<xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A>通過的密碼，如有必要，然後將活頁簿的方法。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>另請參閱  
 [使用活頁簿](../vsto/working-with-workbooks.md)   
 [如何：以程式設計方式保護工作表](../vsto/how-to-programmatically-protect-worksheets.md)   
 [如何：以程式設計方式隱藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
