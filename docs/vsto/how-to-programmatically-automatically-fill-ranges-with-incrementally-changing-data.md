---
title: 以程式設計的方式自動填滿變更資料範圍
description: 瞭解範圍物件的自動填滿方法如何讓您自動以值填滿工作表中的範圍。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 615331181b9402e0d2062142ad266bdd41dca4eb
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824935"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>如何：以程式設計方式自動以累加方式變更資料填滿範圍
  <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>物件的方法可 <xref:Microsoft.Office.Interop.Excel.Range> 讓您自動以值填滿工作表中的範圍。 最常見的 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 方法是在範圍內以累加方式儲存或減少值。 您可以藉由提供列舉中的選擇性常數來指定行為 <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> 。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 使用時，您必須指定兩個範圍 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> ：

- 呼叫方法的範圍 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> ，這個方法會指定填滿的起點並且包含初始值。

- 您要填滿的範圍，以參數形式傳遞給 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 方法。 這個目的範圍必須包含包含初始值的範圍。

    > [!NOTE]
    > 您無法傳遞 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項來取代 <xref:Microsoft.Office.Interop.Excel.Range> 。 如需詳細資訊，請參閱 [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。

## <a name="example"></a>範例
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet49":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet49":::

## <a name="compile-the-code"></a>編譯程式碼
 您要填滿之範圍的第一個資料格必須包含初始值。

 此範例會要求您填入三個區域：

- 資料行 B 是包含五個工作日。 針對初始值，在儲存格 B1 中輸入 **Monday** 。

- C 資料行是包含五個月。 在 [初始值] 中，輸入儲存格 C1 中的 **一月** 。

- 資料行 D 是包含一連串的數位，每個資料列遞增兩次。 針對初始值，在儲存格 D2 中輸入 **4** ，並在儲存格 D2 中輸入 **6** 。

## <a name="see-also"></a>另請參閱
- [使用範圍](../vsto/working-with-ranges.md)
- [如何：以程式設計方式在程式碼中參考工作表範圍](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [如何：以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [如何：以程式設計方式執行 Excel 計算](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
