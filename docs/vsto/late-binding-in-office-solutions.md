---
title: 在 Office 方案中的晚期繫結
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c886305b3cfe63ef2d2821752d97099d93689891
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847252"
---
# <a name="late-binding-in-office-solutions"></a>在 Office 方案中的晚期繫結
  Office 應用程式的物件模型中的某些類型提供可透過晚期繫結功能的功能。 比方說，有些方法和屬性可以傳回不同類型的物件，根據 Office 應用程式的內容，而某些型別可以公開不同的方法或在不同的內容中的屬性。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Visual Basic 專案的位置**Option Strict**是關閉和視覺化C#目標的專案[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]可以直接使用運用這些晚期繫結功能的型別。  
  
## <a name="implicit-and-explicit-casting-of-object-return-values"></a>隱含和明確轉換物件的傳回值  
 許多方法和屬性中的 Microsoft Office 主要 interop 組件 (Pia) 傳回<xref:System.Object>值，因為它們可以傳回許多不同類型的物件。 例如，<xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A>屬性會傳回<xref:System.Object>因為其傳回值可以是<xref:Microsoft.Office.Interop.Excel.Worksheet>或<xref:Microsoft.Office.Interop.Excel.Chart>物件，根據使用中工作表。  
  
 當方法或屬性傳回<xref:System.Object>，您必須明確 （在 Visual Basic) 將物件轉換為正確的類型，在 Visual Basic 專案所在**Option Strict**上。 您沒有明確轉型<xref:System.Object>傳回值，在 Visual Basic 專案所在**Option Strict**已關閉。  
  
 在大部分情況下，參考文件會列出可能的傳回值類型的成員，傳回<xref:System.Object>。 轉換或轉型物件啟用物件在程式碼編輯器 IntelliSense。  
  
 如需在 Visual Basic 中的轉換資訊，請參閱 <<c0> [ 隱含和明確轉換&#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)並[CType 函式&#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function)。</c0>  
  
### <a name="examples"></a>範例  
 下列程式碼範例示範如何將物件轉換成特定類型在 Visual Basic 專案中何處**Option Strict**上。 在這種專案類型中，您必須明確轉型<xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A>屬性設<xref:Microsoft.Office.Interop.Excel.Range>。 這個範例需要名為工作表類別的文件層級 Excel 專案`Sheet1`。  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 下列程式碼範例示範如何以隱含方式轉換 Visual Basic 專案中的 為特定類型的物件所在**Option Strict**關閉或視覺效果中C#專案的目標[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]。 在這些類型的專案中，<xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A>屬性會隱含地轉換成<xref:Microsoft.Office.Interop.Excel.Range>。 這個範例需要名為工作表類別的文件層級 Excel 專案`Sheet1`。  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## <a name="access-members-that-are-available-only-through-late-binding"></a>存取成員，都只能透過晚期繫結  
 某些屬性和 Office Pia 中的方法都只能透過晚期繫結。 專案 Visual Basic 中的 where **Option Strict**已關閉，或在視覺效果C#目標的專案[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]，您可以在這些語言中使用晚期繫結功能來存取晚期繫結成員。 專案 Visual Basic 中的 where **Option Strict**已開啟，您必須使用反映來存取這些成員。  
  
### <a name="examples"></a>範例  
 下列程式碼範例示範如何存取 Visual Basic 專案中的晚期繫結成員所在**Option Strict**關閉或視覺效果中C#專案的目標[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]。 這個範例會存取晚期繫結**名稱**屬性**檔案開啟**在 Word 中的對話方塊。 若要使用此範例中，執行從`ThisDocument`或`ThisAddIn`Word 專案中的類別。  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 下列程式碼範例示範如何使用反映來完成相同的工作，在 Visual Basic 專案中何處**Option Strict**上。  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>另請參閱  
 [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)   
 [使用動態類型&#40;C&#35;程式設計指南&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict 陳述式](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [反映 (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [反映 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)  
