---
title: HOW TO：以程式設計方式在工作表範圍中的文字搜尋
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dba0ce5928b61b1ec6b5777e1922cc68f8ed57ee
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826123"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>HOW TO：以程式設計方式在工作表範圍中搜尋的文字
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>方法的<xref:Microsoft.Office.Interop.Excel.Range>物件可讓您搜尋的範圍內的文字。 這段文字也可以是任何錯誤字串，例如可以出現在工作表儲存格中`#NULL!`或`#VALUE!`。 如需詳細的錯誤字串的詳細資訊，請參閱[儲存格的錯誤值](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values)。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 下列範例會搜尋範圍，名為`Fruits`並修改包含單字"apples"的資料格的字型。 此程序也會使用<xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>方法，它會使用先前設定搜尋設定，以重複搜尋。 指定要搜尋，請在之後的資料格和<xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>方法會處理其餘部分。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>它達到範圍的結尾後方法的搜尋會繞回搜尋範圍的開頭。 您的程式碼必須確定，搜尋不會環繞在無限迴圈。 此範例程序示範一種方式處理這種使用<xref:Microsoft.Office.Interop.Excel.Range.Address%2A>屬性。  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範，請參閱[How do i:Excel 增益集中使用 Find 方法嗎？](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
## <a name="to-search-for-text-in-a-worksheet-range"></a>若要在工作表範圍中搜尋文字  
  
1. 宣告變數，用於追蹤的整個範圍，第一個找到的範圍，並找到目前的範圍。  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2. 搜尋第一個相符的項目，指定要搜尋的儲存格以外的所有參數。  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3. 繼續搜尋，只要有相符項目。  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4. 比較的第一個找到的範圍 (`firstFind`) 來**Nothing**。 如果`firstFind`找到的範圍不包含任何的值，離開程式碼存放區 (`currentFind`)。  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5. 如果找到的範圍的位址符合第一個找到的範圍的位址，請結束迴圈。  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6. 設定的外觀，找到的範圍。  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7. 執行另一個搜尋。  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
   下列範例示範完整的方法：  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>另請參閱  
 [使用範圍](../vsto/working-with-ranges.md)   
 [如何：以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何：以程式設計方式參考程式碼中的工作表範圍](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
