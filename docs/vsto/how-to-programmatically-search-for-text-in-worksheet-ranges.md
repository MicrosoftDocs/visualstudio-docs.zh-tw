---
title: 如何： 以程式設計方式搜尋工作表範圍中的文字 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 2749834f459085b8d182b58f12a4c372f7493cba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>如何：以程式設計方式在工作表範圍中搜尋文字
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>方法<xref:Microsoft.Office.Interop.Excel.Range>物件可讓您搜尋的範圍內的文字。 此文字也可以是任何錯誤字串，例如可以出現在工作表儲存格`#NULL!`或`#VALUE!`。 如需錯誤字串的詳細資訊，請參閱[儲存格錯誤值](http://msdn.microsoft.com/library/office/ff839168.aspx)。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 下列範例會搜尋範圍，名為`Fruits`並修改包含 「 蘋果 」 一詞的資料格的字型。 此程序也會使用<xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>方法，會使用先前設定搜尋設定，以重複的搜尋。 指定要搜尋，請在後面的資料格和<xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>方法會處理其餘部分。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>方法的搜尋會繞回搜尋範圍的開頭，它已達到範圍的結尾之後。 您的程式碼必須確保搜尋不會無限迴圈環繞。 此範例程序示範一種方式處理這種使用<xref:Microsoft.Office.Interop.Excel.Range.Address%2A>屬性。  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")相關的影片示範，請參閱[如何： 使用 Find 方法中的 Excel 增益集？](http://go.microsoft.com/fwlink/?LinkID=130294)。  
  
### <a name="to-search-for-text-in-a-worksheet-range"></a>若要在工作表範圍中搜尋文字  
  
1.  宣告變數，用於追蹤的整個範圍、 第一個找到的範圍，以及目前找到的範圍。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2.  搜尋第一個符合的項目，指定要搜尋的資料格以外的所有參數。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3.  繼續搜尋，只要相符的項目。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4.  比較的第一個找到的範圍 (`firstFind`) 至**Nothing**。 如果`firstFind`找到的範圍不包含任何值，離開程式碼儲存區 (`currentFind`)。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5.  如果找到的範圍的位址符合找到的第一個範圍的位址，請結束迴圈。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6.  設定找到範圍的外觀。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7.  執行另一個搜尋。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
 下列範例示範完整的方法：  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>另請參閱  
 [使用範圍](../vsto/working-with-ranges.md)   
 [如何： 以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何： 以程式設計方式參考程式碼中的工作表範圍](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  