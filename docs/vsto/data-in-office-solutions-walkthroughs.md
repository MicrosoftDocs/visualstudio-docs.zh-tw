---
title: Office 方案中的資料逐步解說
description: 瞭解如何使用適用于 Microsoft Word 和 Microsoft Excel 的檔層級自訂和 VSTO 增益集中的資料。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], walkthroughs
- walkthroughs [Office development in Visual Studio], data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 25bf42015dcc60014012faf0254d4b6d02c30d56
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845579"
---
# <a name="data-in-office-solutions-walkthroughs"></a>Office 方案中的資料逐步解說
  下列逐步解說示範如何處理 Microsoft Office Word 和 Microsoft Office Excel 文件層級自訂和 VSTO 增益集中的資料。

## <a name="bind-controls-to-data"></a>將控制項系結至資料
- [逐步解說：檔層級專案中的簡單資料](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) 系結示範如何將 SQL Server 資料庫中的單一資料欄位系結至 <xref:Microsoft.Office.Tools.Excel.NamedRange> Excel 檔層級自訂中的。

- [逐步解說：檔層級專案中的複雜資料](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) 系結示範如何將 SQL Server 資料庫中的資料表，系結至 <xref:Microsoft.Office.Tools.Excel.ListObject> Excel 檔層級自訂中的。

- [逐步解說： VSTO 增益集專案中的簡單資料](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) 系結示範如何 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 在 Word 的 VSTO 增益集中，將 SQL Server 資料庫中的單一資料欄位系結至。

- [逐步解說： VSTO 增益集專案中的複雜資料](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) 系結示範如何 <xref:Microsoft.Office.Tools.Excel.ListObject> 在 Excel 的 VSTO 增益集中，將 SQL Server 資料庫中的資料表系結至。

- [逐步解說：將資料系結至 Excel 執行窗格上的控制項](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md) 示範如何將系結至資料來源的控制項加入 Excel 中的執行窗格。

- [逐步解說：將資料系結至 Word 執行窗格上的控制項](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md) 示範如何將執行窗格上的控制項系結至資料。 這些控制項會顯示 SQL Server 資料庫中資料表之間的主要/詳細資料關聯。

- [逐步解說：將內容控制項系結至自訂 XML 元件](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md) 示範如何將 Word 檔中的內容控制項系結至儲存在檔中的 XML 資料。

## <a name="cache-data-in-document-level-solutions"></a>快取檔層級方案中的資料
- [逐步解說：使用快取資料集建立主要詳細資料關聯](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md) 示範如何在工作表上建立主版/詳細資料關聯，並快取資料，讓方案可以離線使用。

- [逐步解說：在伺服器的活頁簿中插入資料](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md) 示範如何在不啟動 Excel 的情況下，將資料插入 Microsoft Office Excel 活頁簿中快取的資料集。

- [逐步解說：從伺服器上的活頁簿取出快取的資料](../vsto/walkthrough-retrieving-cached-data-from-a-workbook-on-a-server.md) 示範如何在不啟動 Excel 的情況下，從 Microsoft Office Excel 活頁簿中快取的資料集取得資料。

- [逐步解說：變更伺服器上活頁簿中的](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md) 快取資料示範如何在不啟動 Excel 的情況下，修改在 Microsoft Office Excel 活頁簿中快取的資料集。

## <a name="see-also"></a>另請參閱
- [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)
- [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)
- [Office UI 自訂逐步解說](../vsto/office-ui-customization-walkthroughs.md)
- [安全性和部署逐步解說](../vsto/security-and-deployment-walkthroughs.md)
- [Office 開發範例](../vsto/office-development-samples.md)
- [在 Visual Studio&#41;中開始 &#40;Office 開發 ](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office 程式設計中的一般工作](../vsto/common-tasks-in-office-programming.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
