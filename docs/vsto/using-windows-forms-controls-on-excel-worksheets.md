---
title: 使用 Windows Form 控制項中的 Excel 工作表上 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d4c754c0fff7f7a0f5c3bf31293696e3ec57961f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="using-windows-forms-controls-on-excel-worksheets"></a>在 Excel 工作表中使用 Windows Form 控制項
  您可以加入 Windows Form 控制項 Microsoft Office Excel 活頁簿，您會將控制項加入 Windows Form 的方式相同。 如需有關文件上的控制項使用的一般資訊，請參閱[Windows Form 控制項，在 Office 文件概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>適用於 Excel 的控制項考量  
 有幾個考量專屬於 Excel。  
  
### <a name="matching-control-size-to-cell-size"></a>比對控制項大小的儲存格大小  
 您可以設定在父儲存格的大小變更時自動調整控制項的大小。 如需詳細資訊，請參閱[如何： 調整大小的控制項內工作表儲存格](../vsto/how-to-resize-controls-within-worksheet-cells.md)。  
  
### <a name="adding-components-that-are-shared-by-all-worksheets"></a>加入所有工作表共用的元件  
 您可以將想要在所有工作表之間共用的元件，例如 <xref:System.Data.DataSet>，加入活頁簿設計工具，而不是加入工作表。 元件會出現在元件匣中。  
  
### <a name="formula-for-embedding-controls"></a>內嵌控制項的公式  
 在 Excel 中選取控制項時，您會在 [資料編輯列]  看到 **=EMBED("WinForms.Control.Host","")**。 這個文字是必要的，不應該刪除。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 調整工作表儲存格內的控制項的大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [如何： 列印時隱藏工作表上的控制項](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [逐步解說： 變更工作表使用核取方塊控制項](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [逐步解說： 使用按鈕在工作表中的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [逐步解說：使用選項按鈕更新工作表中的圖表](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  