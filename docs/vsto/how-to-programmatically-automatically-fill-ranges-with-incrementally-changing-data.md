---
title: 以累加方式以程式設計方式變更資料範圍的自動填滿
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a514f83d12cd00c4a7792ae0bf2483fdd916897a
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177694"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>作法：使用累加式變更資料，以程式設計的方式自動填滿範圍
  <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>方法的<xref:Microsoft.Office.Interop.Excel.Range>物件可讓您將會自動填入值的工作表中的範圍。 大多數情況下，<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>方法用來儲存以累加方式增加或減少的範圍內的值。 您可以藉由提供選擇性的常數，從指定的行為<xref:Microsoft.Office.Interop.Excel.XlAutoFillType>列舉型別。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 使用時，您必須指定兩個範圍<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:

- 呼叫的範圍<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>方法，它指定填滿的起點，並包含初始值。

- 您想要填滿時，範圍當做參數傳遞給<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>方法。 此目的範圍必須包括包含的起始值的範圍。

    > [!NOTE]
    > 您不能傳遞<xref:Microsoft.Office.Tools.Excel.NamedRange>控制的位置<xref:Microsoft.Office.Interop.Excel.Range>。 如需詳細資訊，請參閱 <<c0> [ 主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。

## <a name="example"></a>範例
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]

## <a name="compile-the-code"></a>編譯程式碼
 第一個資料格，您想要填入的範圍必須包含一個初始值。

 這個範例需要您填入三個區域：

- 資料行 B 是包含五個工作天。 初始的值輸入**星期一**儲存格 B1 中。

- C 資料行是加入第五個月。 初始的值輸入**年 1 月**儲存格 C1 中。

- 資料行 D 是包含一系列數字，每個資料列的兩個遞增。 初始的值中，輸入**4**儲存格 D1 並**6**在儲存格 D2。

## <a name="see-also"></a>另請參閱
- [使用範圍](../vsto/working-with-ranges.md)
- [如何：以程式設計方式參考程式碼中的工作表範圍](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [如何：以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [如何：以程式設計方式執行 Excel 計算](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
