---
title: Office 方案中的晚期繫結
description: 瞭解 Microsoft Office 應用程式內物件模型中的某些類型如何提供可透過晚期繫結功能取得的功能。
ms.custom: SEO-VS-2020
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e618dcd0cc699b4626f825890cf0fc8bd7ddd853
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823882"
---
# <a name="late-binding-in-office-solutions"></a>Office 方案中的晚期繫結
  Office 應用程式物件模型中的某些類型會提供透過晚期繫結功能提供的功能。 例如，某些方法和屬性可以根據 Office 應用程式的內容傳回不同類型的物件，而某些類型可能會在不同的內容中公開不同的方法或屬性。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 如果 **Option Strict** 為 off，而以或為目標的 Visual c # 專案，則 Visual Basic 專案 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 可以直接搭配採用這些晚期繫結功能的型別使用。

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>物件傳回值的隱含和明確轉換
 Microsoft Office 主要 interop 元件中的許多方法和屬性 (Pia) 傳回 <xref:System.Object> 值，因為它們可以傳回數種不同類型的物件。 例如，屬性會傳回， <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> <xref:System.Object> 因為它的傳回值可以是 <xref:Microsoft.Office.Interop.Excel.Worksheet> 或 <xref:Microsoft.Office.Interop.Excel.Chart> 物件，這取決於使用中的工作表。

 當方法或屬性傳回時 <xref:System.Object> ，您必須明確地將 Visual Basic) 物件 (轉換為 Visual Basic 專案中， **Option Strict** 為 on 的正確類型。 在 <xref:System.Object> **Option Strict** 為 off 的 Visual Basic 專案中，您不需要明確地轉換傳回值。

 在大部分的情況下，參考檔會列出傳回之成員的傳回值可能類型 <xref:System.Object> 。 轉換或轉換物件可在程式碼編輯器中啟用物件的 IntelliSense。

 如需 Visual Basic 轉換的詳細資訊，請參閱 [隱含和明確轉換 &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) 和 [CType 函數 &#40;](/dotnet/visual-basic/language-reference/functions/ctype-function)Visual Basic&#41;。

### <a name="examples"></a>範例
 下列程式碼範例示範如何在 **Option Strict** 為 on 的 Visual Basic 專案中，將物件轉型為特定的類型。 在這種類型的專案中，您必須明確地將 <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> 屬性轉換為 <xref:Microsoft.Office.Interop.Excel.Range> 。 此範例需要檔層級 Excel 專案，其中包含名為的工作表類別 `Sheet1` 。

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet9":::

 下列程式碼範例示範如何將物件隱含轉換成 Visual Basic 專案中的特定型別，其中 **Option Strict** 為 off，或在以為目標的 Visual c # 專案中 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 。 在這些類型的專案中， <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> 屬性會隱含地轉換成 <xref:Microsoft.Office.Interop.Excel.Range> 。 此範例需要檔層級 Excel 專案，其中包含名為的工作表類別 `Sheet1` 。

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet10":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="access-members-that-are-available-only-through-late-binding"></a>存取只能透過晚期繫結使用的成員
 Office Pia 中的部分屬性和方法只能透過晚期繫結來使用。 在 Visual Basic 專案中， **Option Strict** 為 off 或在以或為目標的 Visual c # 專案中 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ，您可以使用這些語言中的晚期繫結功能來存取晚期繫結成員。 在 **Option Strict** 為 on Visual Basic 專案中，您必須使用反映來存取這些成員。

### <a name="examples"></a>範例
 下列程式碼範例示範如何存取 Visual Basic 專案中的晚期繫結成員，其中 **Option Strict** 為 off，或在以為目標的 Visual c # 專案中 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 。 這個範例會存取 Word 中 [**開啟** 檔案] 對話方塊的 [晚期繫結 **名稱**] 屬性。 若要使用此範例，請從 `ThisDocument` `ThisAddIn` Word 專案的或類別中執行它。

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet122":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet122":::

 下列程式碼範例示範如何在 **Option Strict** 為 on 的 Visual Basic 專案中，使用反映來完成相同的工作。

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet102":::

## <a name="see-also"></a>另請參閱
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
- [使用類型 dynamic &#40;C&#35; 程式設計手冊&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Option Strict 語句](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [反映 (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [反映 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
