---
title: Office UI 自訂逐步解說
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes, walkthroughs
- smart documents, walkthroughs
- walkthroughs [Office development in Visual Studio], smart tags
- walkthroughs [Office development in Visual Studio], action panes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e961479fc500e53133c62337478368878bf26893
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254134"
---
# <a name="office-ui-customization-walkthroughs"></a>Office UI 自訂逐步解說
  下列逐步解說示範使用文件層級自訂和 VSTO 增益集來自訂 Microsoft Office 應用程式使用者介面 (UI) 的方法。

## <a name="actions-pane-walkthroughs"></a>動作窗格逐步解說
- [逐步解說：從執行窗格](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)將文字插入檔中，會示範如何在 Word 檔中建立執行窗格。 執行窗格包含會將使用者輸入傳送至文件的兩個控制項。

- [逐步解說：將資料系結至 word 執行窗格](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)上的控制項示範如何將 word 中 [動作] 窗格上的控制項系結至資料。 這些控制項會顯示 SQL Server 資料庫中資料表之間的主要/詳細資料關聯。

- [逐步解說：將資料系結至 excel 執行窗格](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)上的控制項說明如何將系結至資料來源的控制項加入 excel 的 [動作] 窗格。

## <a name="custom-task-pane-walkthroughs"></a>自訂工作窗格逐步解說
- [逐步解說：從自訂工作窗格](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)自動化應用程式示範如何建立自訂工作窗格，其中包含可在使用者按一下控制項時自動執行主應用程式的控制項。

- [逐步解說：使用功能區按鈕](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)同步處理自訂工作窗格示範如何建立自訂工作窗格，讓使用者按一下功能區上的切換按鈕來隱藏或顯示。

- [逐步解說：在 outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)中使用電子郵件訊息顯示自訂工作窗格示範如何顯示自訂工作窗格的唯一實例，以及每個在 Outlook 中建立或開啟的電子郵件訊息。

## <a name="ribbon-walkthroughs"></a>功能區逐步解說
- [逐步解說：使用功能區設計](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)工具建立自訂索引標籤示範如何使用功能區設計工具建立自訂功能區索引標籤。 索引標籤包含可用來隱藏或顯示執行窗格的按鈕。

- [逐步解說：在執行時間](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)更新功能區上的控制項示範如何使用功能區物件模型，在功能區載入至 Office 應用程式之後，更新功能區上的控制項。

- [逐步解說：使用功能區 xml](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)建立自訂索引標籤示範如何使用功能區 xml 建立自訂功能區索引標籤，而不是使用功能區設計工具。

## <a name="controls-on-word-documents"></a>Word 檔上的控制項
- [逐步解說：在 vsto 增益集](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)的執行時間中將控制項加入檔中示範如何使用 vsto 增益集，將控制項加入檔中。

- [逐步解說：使用核取方塊控制項](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)變更檔案格式示範如何在檔層級自訂中使用核取方塊來變更 Word 檔中的格式。

- [逐步解說：使用按鈕](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)在檔的文字方塊中顯示文字，示範如何在 Word 檔上使用按鈕和文字方塊。

- [逐步解說：使用選項按鈕](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)更新檔中的圖表示範如何在檔層級自訂中使用選項按鈕來變更 Word 檔中的圖表樣式。

## <a name="controls-on-excel-worksheets"></a>Excel 工作表上的控制項
- [逐步解說：在執行時間于 vsto 增益集專案](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)中將控制項加入工作表示範如何使用 vsto 增益集，將控制項加入工作表。

- [逐步解說：使用 CheckBox 控制項](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)來變更工作表格式示範在 Excel 工作表上使用核取方塊來變更格式的基本概念。

- [逐步解說：使用按鈕](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)在工作表的文字方塊中顯示文字，會示範在 Excel 工作表上使用按鈕和文字方塊的基本概念。

- [逐步解說：使用選項按鈕](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)更新工作表中的圖表顯示在 Excel 工作表上使用選項按鈕變更圖表樣式的基本概念。

## <a name="see-also"></a>另請參閱
- [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)
- [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)
- [Office 方案中的資料逐步解說](../vsto/data-in-office-solutions-walkthroughs.md)
- [安全性和部署逐步解說](../vsto/security-and-deployment-walkthroughs.md)
- [開始&#40;在 Visual Studio 中進行 Office 開發&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office 程式設計的一般工作](../vsto/common-tasks-in-office-programming.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
