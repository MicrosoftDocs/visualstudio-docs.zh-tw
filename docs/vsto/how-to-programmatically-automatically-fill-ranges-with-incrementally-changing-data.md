---
title: "如何： 以程式設計的方式自動填滿範圍與以累加方式變更資料 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
ms.assetid: 27639d55-8ab5-483c-8907-2ea50dfd2188
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4fad536f7e9f0891f7630cd86d31cea279d5706f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>如何：以程式設計方式用遞增 (減) 變化的資料自動填滿範圍
  <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>方法<xref:Microsoft.Office.Interop.Excel.Range>物件可讓您自動填入工作表中的範圍值。 通常，<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>方法用來儲存以累加方式增加或減少值的範圍內。 您可以藉由提供從選擇性常數指定行為<xref:Microsoft.Office.Interop.Excel.XlAutoFillType>列舉型別。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 使用時，您必須指定兩個範圍<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:  
  
-   呼叫的範圍<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>指定填滿的起點，並且包含初始值的方法。  
  
-   您想要填滿時，範圍傳遞為參數，以<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>方法。 此目的範圍必須包括包含的起始值的範圍。  
  
    > [!NOTE]  
    >  您無法將傳遞<xref:Microsoft.Office.Tools.Excel.NamedRange>取代控制<xref:Microsoft.Office.Interop.Excel.Range>。 如需詳細資訊，請參閱 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 您要填滿範圍的第一個資料格必須包含一個初始值。  
  
 這個範例需要您填入三個區域：  
  
-   資料行 B 是包含五個工作天。 初始值輸入**星期一**儲存格 B1 中。  
  
-   C 資料行是包含五個月。 初始值輸入**年 1 月**C1 資料格中。  
  
-   資料行 D 是包含一系列的數字遞增每個資料列的兩個。 做為初始值輸入**4**儲存格 D1 和**6**在儲存格 D2。  
  
## <a name="see-also"></a>另請參閱  
 [使用範圍](../vsto/working-with-ranges.md)   
 [如何： 以程式設計方式參考程式碼中的工作表範圍](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [如何： 以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何： 以程式設計方式執行 Excel 計算](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  