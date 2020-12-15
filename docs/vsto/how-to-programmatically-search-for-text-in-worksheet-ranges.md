---
title: 如何：以程式設計方式在工作表範圍中搜尋文字
description: 瞭解如何使用 Visual Studio，以程式設計方式在 Microsoft Excel 工作表範圍中搜尋文字。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 01ce01e76aa56a834f4f63cd2bd0f6f16c4ab03a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524557"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>如何：以程式設計方式在工作表範圍中搜尋文字
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>物件的方法可 <xref:Microsoft.Office.Interop.Excel.Range> 讓您搜尋範圍內的文字。 此文字也可以是可以出現在工作表儲存格中的任何錯誤字串，例如 `#NULL!` 或 `#VALUE!` 。 如需錯誤字串的詳細資訊，請參閱 [資料格誤差值](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values)。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 下列範例會搜尋名為的範圍 `Fruits` ，並修改包含 "蘋果" 這個字的儲存格字型。 此程式也會使用 <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> 方法，該方法會使用先前設定的搜尋設定來重複搜尋。 您可以指定要搜尋的資料格，而且 <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> 方法會處理其餘部分。

> [!NOTE]
> <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>方法的搜尋在到達範圍結尾之後，會換回搜尋範圍的開頭。 您的程式碼必須確保搜尋不會在無限迴圈中換行。 範例程式會顯示使用屬性來處理此情況的一種方法 <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> 。

## <a name="to-search-for-text-in-a-worksheet-range"></a>在工作表範圍中搜尋文字

1. 宣告變數以追蹤整個範圍、第一個找到的範圍，以及目前找到的範圍。

    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]

2. 搜尋第一個相符項，指定除了要搜尋的儲存格以外的所有參數。

    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]

3. 只要有相符專案，即可繼續搜尋。

    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]

4. 比較第一個找到的範圍 (`firstFind`) 為 **Nothing**。 如果 `firstFind` 未包含任何值，則程式碼會將找到的範圍儲存 (`currentFind`) 。

    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]

5. 如果找到的範圍位址符合第一個找到範圍的位址，請結束迴圈。

    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]

6. 設定找到範圍的外觀。

    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]

7. 執行其他搜尋。

    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]

   下列範例示範完整的方法：

## <a name="example"></a>範例
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]

## <a name="see-also"></a>另請參閱
- [使用範圍](../vsto/working-with-ranges.md)
- [如何：以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [如何：以程式設計方式在程式碼中參考工作表範圍](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
