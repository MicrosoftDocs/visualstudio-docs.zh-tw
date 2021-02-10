---
title: Office UI 自訂逐步解說
description: 瞭解如何使用檔層級自訂和 VSTO 增益集來自訂 Microsoft Office 應用程式的使用者介面 (UI) 。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9ee5d6cbe372b0a7930b867a98136d132ddb0b2c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959879"
---
# <a name="office-ui-customization-walkthroughs"></a>Office UI 自訂逐步解說
  下列逐步解說示範使用文件層級自訂和 VSTO 增益集來自訂 Microsoft Office 應用程式使用者介面 (UI) 的方法。

## <a name="actions-pane-walkthroughs"></a>動作窗格逐步解說
- [逐步解說：從執行窗格將文字插入檔](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md) 示範如何在 Word 檔中建立執行窗格。 執行窗格包含會將使用者輸入傳送至文件的兩個控制項。

- [逐步解說：將資料系結至 Word 執行窗格上的控制項](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md) 示範如何將 Word 執行窗格上的控制項系結至資料。 這些控制項會顯示 SQL Server 資料庫中資料表之間的主要/詳細資料關聯。

- [逐步解說：將資料系結至 Excel 執行窗格上的控制項](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md) 描述如何將系結至資料來源的控制項加入 Excel 中的執行窗格。

## <a name="custom-task-pane-walkthroughs"></a>自訂工作窗格逐步解說
- [逐步解說：從自訂工作窗格自動化應用程式](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md) 示範如何建立自訂工作窗格，其中包含的控制項，可在使用者按一下控制項時自動化主應用程式。

- [逐步解說：使用功能區按鈕同步處理自訂工作窗格](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md) 示範如何建立使用者按一下功能區上的切換按鈕，即可隱藏或顯示的自訂工作窗格。

- [逐步解說：在 Outlook 中顯示含有電子郵件訊息的自訂工作窗格](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md) 示範如何使用在 Outlook 中建立或開啟的每一封電子郵件訊息，顯示自訂工作窗格的唯一實例。

## <a name="ribbon-walkthroughs"></a>功能區逐步解說
- [逐步解說：使用功能區設計工具建立自訂](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md) 索引標籤示範如何使用功能區設計工具建立自訂功能區索引標籤。 索引標籤包含可用來隱藏或顯示執行窗格的按鈕。

- [逐步解說：在執行時間更新功能區上的控制項](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md) 示範如何使用功能區物件模型，在功能區載入至 Office 應用程式之後，更新功能區上的控制項。

- [逐步解說：使用功能區 XML 建立自訂](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md) 索引標籤示範如何使用功能區 XML 來建立自訂功能區索引標籤，而不是使用功能區設計工具。

## <a name="controls-on-word-documents"></a>Word 檔上的控制項
- [逐步解說：在 VSTO 增益集中，于執行時間將控制項加入至檔](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md) 示範如何使用 VSTO 增益集將控制項加入檔。

- [逐步解說：使用 CheckBox 控制項變更檔案格式](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md) 示範如何在檔層級自訂中使用核取方塊來變更 Word 檔中的格式。

- [逐步解說：使用按鈕在檔的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md) 示範如何在 Word 檔上使用按鈕和文字方塊。

- [逐步解說：使用選項按鈕更新檔中的圖表](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md) 示範如何在檔層級自訂中使用選項按鈕，以變更 Word 檔中的圖表樣式。

## <a name="controls-on-excel-worksheets"></a>Excel 工作表上的控制項
- [逐步解說：在執行時間于 VSTO 增益集專案中，將控制項加入工作表](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) 示範如何使用 VSTO 增益集將控制項加入工作表。

- [逐步解說：使用 CheckBox 控制項變更工作表格式](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md) 示範在 Excel 工作表上使用核取方塊來變更格式的基本概念。

- [逐步解說：使用按鈕在工作表的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md) 示範在 Excel 工作表上使用按鈕和文字方塊的基本概念。

- [逐步解說：使用選項按鈕更新工作表中的圖表](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md) 顯示在 Excel 工作表上使用選項按鈕變更圖表樣式的基本概念。

## <a name="see-also"></a>另請參閱
- [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)
- [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)
- [Office 方案中的資料逐步解說](../vsto/data-in-office-solutions-walkthroughs.md)
- [安全性和部署逐步解說](../vsto/security-and-deployment-walkthroughs.md)
- [在 Visual Studio&#41;中開始 &#40;Office 開發 ](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office 程式設計中的一般工作](../vsto/common-tasks-in-office-programming.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
