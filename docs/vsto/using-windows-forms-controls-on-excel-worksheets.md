---
title: 使用 Excel 工作表上的 Windows Form 控制項
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 032ee551ff04590ccdb8744c1274b137dec0b756
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599502"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>使用 Excel 工作表上的 Windows Form 控制項
  您可以加入 Windows Form 控制項您的 Microsoft Office Excel 活頁簿將控制項新增至 Windows Forms 的方式相同。 如需有關使用文件上控制項的一般資訊，請參閱[Windows Forms 控制項上 Office 文件概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="control-considerations-for-excel"></a>適用於 Excel 的控制考量
 有幾個專用於 Excel 的考量。

### <a name="match-control-size-to-cell-size"></a>儲存格大小的相符項目控制項大小
 您可以設定在父儲存格的大小變更時自動調整控制項的大小。 如需詳細資訊，請參閱[如何：調整工作表儲存格內的控制項大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)。

### <a name="add-components-that-are-shared-by-all-worksheets"></a>新增共用的所有工作表的元件
 您可以將想要在所有工作表之間共用的元件，例如 <xref:System.Data.DataSet>，加入活頁簿設計工具，而不是加入工作表。 元件會出現在元件匣中。

### <a name="formula-for-embedding-controls"></a>內嵌控制項的公式
 在 Excel 中選取控制項時，您會在 [資料編輯列]  看到 **=EMBED("WinForms.Control.Host","")**。 這個文字是必要的，不應該刪除。

## <a name="see-also"></a>另請參閱
- [如何：調整工作表儲存格內的控制項的大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [如何：列印時隱藏工作表的控制項](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [逐步解說：變更工作表的格式使用核取方塊控制項](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [逐步解說：在文字方塊中，使用按鈕在工作表中的顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [逐步解說：更新使用選項按鈕在工作表中的圖表](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
