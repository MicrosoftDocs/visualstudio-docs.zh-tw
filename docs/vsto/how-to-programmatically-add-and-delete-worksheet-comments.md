---
title: 如何：以程式設計方式新增及刪除工作表批註
description: 瞭解如何以程式設計方式加入和刪除 Microsoft Office Excel 工作表中的批註。 您只能將批註加入至單一資料格，而不是多儲存格範圍。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ec70c03dfdce05c7445762e2cfd452f3fdf90775
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904494"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>如何：以程式設計方式新增及刪除工作表批註
  您可以透過程式設計方式，加入及刪除 Microsoft Office Excel 工作表中的註解。 註解只能加入單一儲存格，而不能加入多個儲存格範圍。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>在檔層級專案中加入及刪除批註
 下列範例假設名為 <xref:Microsoft.Office.Tools.Excel.NamedRange> 的工作表上有名為 `dateComment` 的單一儲存格 `Sheet1`。

### <a name="to-add-a-new-comment-to-a-named-range"></a>將新註解加入具名範圍

1. 呼叫 <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> 控制項的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 方法，並提供註解文字。 這段程式碼必須放在 `Sheet1` 類別中。

     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]

#### <a name="to-delete-a-comment-from-a-named-range"></a>從具名範圍中刪除註解

1. 確認範圍中有註解，再加以刪除。 這段程式碼必須放在 `Sheet1` 類別中。

     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]

## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>在 VSTO 增益集專案中加入及刪除批註
 下列範例假設使用中工作表上有名為 <xref:Microsoft.Office.Interop.Excel.Range> 的單一儲存格 `dateComment` 。

### <a name="to-add-a-new-comment-to-an-excel-range"></a>將新註解加入 Excel 範圍

1. 呼叫 <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> 的 <xref:Microsoft.Office.Interop.Excel.Range> 方法，並提供註解文字。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]

### <a name="to-delete-a-comment-from-an-excel-range"></a>從 Excel 範圍中刪除註解

1. 確認範圍中有註解，再加以刪除。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]

## <a name="see-also"></a>另請參閱
- [使用工作表](../vsto/working-with-worksheets.md)
- [如何：以程式設計方式顯示工作表批註](../vsto/how-to-programmatically-display-worksheet-comments.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
