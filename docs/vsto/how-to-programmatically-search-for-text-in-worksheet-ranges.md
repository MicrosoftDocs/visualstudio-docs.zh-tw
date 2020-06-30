---
title: 如何：以程式設計方式在工作表範圍中搜尋文字
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
ms.openlocfilehash: 4d35d24f9132a9b279316b53fbb13e3bfa094994
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547026"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>如何：以程式設計方式在工作表範圍中搜尋文字
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>物件的方法可 <xref:Microsoft.Office.Interop.Excel.Range> 讓您搜尋範圍內的文字。 此文字也可以是任何可能出現在工作表資料格中的錯誤字串，例如 `#NULL!` 或 `#VALUE!` 。 如需錯誤字串的詳細資訊，請參閱[資料格錯誤值](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values)。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 下列範例會搜尋名為的範圍 `Fruits` ，並修改包含「蘋果」這個字的儲存格字型。 此程式也會使用 <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> 方法，其使用先前設定的搜尋設定來重複搜尋。 您可以指定要在其後搜尋的資料格，而方法則會 <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> 處理其餘部分。

> [!NOTE]
> <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>方法的搜尋會在到達範圍結尾之後，換回搜尋範圍的開頭。 您的程式碼必須確定搜尋不會在無限迴圈中環繞。 範例程式會示範使用屬性來處理這項操作的方法 <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> 。

## <a name="to-search-for-text-in-a-worksheet-range"></a>若要搜尋工作表範圍中的文字

1. 宣告用來追蹤整個範圍的變數、第一個找到的範圍，以及目前找到的範圍。

    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]

2. 搜尋第一個相符項，並指定除了要搜尋的資料格以外的所有參數。

    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]

3. 只要有相符專案，即可繼續搜尋。

    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]

4. 比較第一個找到的範圍（ `firstFind` ）為 [**無**]。 如果 `firstFind` 未包含任何值，則程式碼會將所找到的範圍（）儲存在外 `currentFind` 。

    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]

5. 如果找到的範圍位址符合第一個找到範圍的位址，則結束迴圈。

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
