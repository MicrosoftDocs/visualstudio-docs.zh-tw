---
title: 在 Office 方案中的晚期繫結
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 5616ce958747f90c8015df858f657299ba52852b
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572546"
---
# <a name="late-binding-in-office-solutions"></a>在 Office 方案中的晚期繫結
  Office 應用程式的物件模型中的某些類型提供功能，可透過晚期繫結功能。 例如，一些方法和屬性可以傳回不同類型的物件，視 Office 應用程式的內容而定，而某些型別可以公開不同的方法或在不同內容中的屬性。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Visual Basic 專案 where **Option Strict**已關閉，因此 Visual C# 目標的專案[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]可直接與採用這些晚期繫結功能的類型。  
  
## <a name="implicit-and-explicit-casting-of-object-return-values"></a>隱含和明確轉換物件的傳回值  
 許多方法和屬性中的 Microsoft Office 主要 interop 組件 (Pia) 傳回<xref:System.Object>值，因為它們可以傳回許多不同類型的物件。 例如，<xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A>屬性會傳回<xref:System.Object>因為其傳回值可以是<xref:Microsoft.Office.Interop.Excel.Worksheet>或<xref:Microsoft.Office.Interop.Excel.Chart>根據使用中工作表的是物件。  
  
 方法或屬性傳回<xref:System.Object>，您必須明確地 （在 Visual Basic) 將物件轉換成正確的類型，在 Visual Basic 專案位置**Option Strict**上。 您沒有明確轉換<xref:System.Object>傳回值，在 Visual Basic 專案位置**Option Strict**已關閉。  
  
 在大部分情況下，參考文件會列出可能的傳回值類型成員會傳回<xref:System.Object>。 轉換或轉型物件可讓 IntelliSense 程式碼編輯器中的物件。  
  
 如需在 Visual Basic 中的轉換資訊，請參閱[隱含和明確轉換&#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)和[CType 函式&#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function)。  
  
### <a name="examples"></a>範例  
 下列程式碼範例示範如何在 Visual Basic 專案轉換為特定類型的物件位置**Option Strict**上。 在這種專案類型中，您必須明確轉換<xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A>屬性<xref:Microsoft.Office.Interop.Excel.Range>。 這個範例需要名為工作表類別的文件層級 Excel 專案`Sheet1`。  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 下列程式碼範例示範如何以隱含方式轉換為特定類型的物件在 Visual Basic 專案中其中**Option Strict**已關閉或處於為目標的 Visual C# 專案[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]。 在這些類型的專案，<xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A>屬性隱含轉換成<xref:Microsoft.Office.Interop.Excel.Range>。 這個範例需要名為工作表類別的文件層級 Excel 專案`Sheet1`。  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## <a name="access-members-that-are-available-only-through-late-binding"></a>只能透過晚期繫結的存取成員  
 某些屬性和方法 Office Pia 中的都可以只透過晚期繫結。 專案 Visual Basic 中的 where **Option Strict**已關閉，或在 Visual C# 專案中目標[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]，您可以這些語言中使用晚期繫結功能，來存取晚期繫結成員。 專案 Visual Basic 中的 where **Option Strict**已開啟，您必須使用反映來存取這些成員。  
  
### <a name="examples"></a>範例  
 下列程式碼範例示範如何存取 Visual Basic 專案中的晚期繫結成員其中**Option Strict**已關閉或處於為目標的 Visual C# 專案[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]。 這個範例會存取晚期繫結**名稱**屬性**開啟舊檔**在 Word 中的對話方塊。 若要使用此範例中，執行從`ThisDocument`或`ThisAddIn`Word 專案中的類別。  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 下列程式碼範例示範如何使用反映來完成相同的工作，在 Visual Basic 專案中其中**Option Strict**上。  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>另請參閱  
 [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)   
 [使用動態類型&#40;C&#35;程式設計指南&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict 陳述式](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [反映 (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [反映 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)  
  
  