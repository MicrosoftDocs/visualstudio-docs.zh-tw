---
title: 在 Excel 工作表上使用 Windows Forms 控制項
description: 瞭解如何以將控制項新增至 Windows Forms 的相同方式，將 Windows Forms 控制項新增至 Microsoft Excel 活頁簿。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f8c79e487e116741c393cef5a6f65b30cc4a8cfb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838213"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>在 Excel 工作表上使用 Windows Forms 控制項
  您可以用將控制項新增至 Windows Forms 的相同方式，將 Windows Forms 控制項加入 Microsoft Office Excel 活頁簿中。 如需在檔上使用控制項的一般資訊，請參閱 [Office 檔的 Windows Forms 控制項總覽](../vsto/windows-forms-controls-on-office-documents-overview.md)。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="control-considerations-for-excel"></a>Excel 的控制項考慮
 Excel 有一些特定的考慮。

### <a name="match-control-size-to-cell-size"></a>將控制項大小符合資料格大小
 您可以設定在父儲存格的大小變更時自動調整控制項的大小。 如需詳細資訊，請參閱 [如何：在工作表儲存格中調整控制項的大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)。

### <a name="add-components-that-are-shared-by-all-worksheets"></a>新增所有工作表共用的元件
 您可以將想要在所有工作表之間共用的元件，例如 <xref:System.Data.DataSet>，加入活頁簿設計工具，而不是加入工作表。 元件會出現在元件匣中。

### <a name="formula-for-embedding-controls"></a>內嵌控制項的公式
 在 Excel 中選取控制項時，您會在 [資料編輯列]  看到 **=EMBED("WinForms.Control.Host","")**。 這個文字是必要的，不應該刪除。

## <a name="see-also"></a>另請參閱
- [如何：調整工作表儲存格內的控制項大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [如何：列印時隱藏工作表上的控制項](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [逐步解說：使用 CheckBox 控制項變更工作表格式](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [逐步解說：使用按鈕在工作表的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [逐步解說：使用選項按鈕更新工作表中的圖表](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
