---
title: Office 程式設計中的一般工作
description: 瞭解如何在檔層級自訂中針對資料進行程式設計，而不需要使用 Microsoft Office Word 或 Office Excel 的物件模型。
ms.custom: SEO-VS-2020SS
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 67b09d3881dcde1d404b7ff0c1096ced1ecb50ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910611"
---
# <a name="common-tasks-in-office-programming"></a>Office 程式設計中的一般工作
  本主題旨在協助您找出下列類別之使用 Visual Studio 進行 Office 方案程式設計的相關常見問題解答。

- [設定和一般](#projects)工作。

- [使用者介面自訂](#ui)工作。

- [Excel 自動化](#excel)工作。

- [Word 自動化](#word)工作。

- [資料](#data)工作。

- [伺服器端文件管理工作](#server)

- [安全性](#security)工作。

- [部署](#deployment)工作。

## <a name="setup-and-general-tasks"></a><a name="projects"></a> 設定和一般工作

- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

- [如何：升級 Office 方案](/previous-versions/4bez6837(v=vs.140))。

- [如何：安裝 Office 主要 interop 元件](../vsto/how-to-install-office-primary-interop-assemblies.md)。

- [如何：透過主要 interop 元件以 Office 應用程式為目標](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)。

- [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

- [如何：開啟 Office 方案而不執行程式碼](../vsto/how-to-open-office-solutions-without-running-code.md)。

- [如何：設定 Office 方案的設定資訊](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)。

- [如何：顯示功能區上的 [開發人員]](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)索引標籤。

- [如何：顯示增益集使用者介面錯誤](../vsto/how-to-show-add-in-user-interface-errors.md)。

## <a name="user-interface-customization-tasks"></a><a name="ui"></a> 使用者介面自訂工作

### <a name="controls-on-documents-and-worksheets"></a>檔和工作表上的控制項

- [如何：將 Windows Forms 控制項加入 Office 檔](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)。

- [如何：將 NamedRange 控制項加入至工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)。

- [如何：將 ListObject 控制項加入至工作表](../vsto/how-to-add-listobject-controls-to-worksheets.md)。

- [如何：將 Windows Forms 控制項加入 Office 檔](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)。

- [如何：將內容控制項新增至 Word 檔](../vsto/how-to-add-content-controls-to-word-documents.md)。

- [如何：將書簽控制項新增至 Word 檔](../vsto/how-to-add-bookmark-controls-to-word-documents.md)。

### <a name="task-panes-in-document-level-customizations"></a>檔層級自訂中的工作窗格

- [如何：將執行窗格加入 Word 檔或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)。

### <a name="task-panes-in-vsto-add-ins"></a>VSTO 增益集中的工作窗格

- [如何：將自訂工作窗格加入至應用程式](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)。

### <a name="ribbon-customizations"></a>功能區自訂

- [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。

- [如何：變更功能區上](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)的索引標籤位置。

- [如何：自訂內建](../vsto/how-to-customize-a-built-in-tab.md)索引標籤。

- [如何：將控制項加入至 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)。

- [如何：將功能區設計工具的功能區匯出至功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="outlook-form-regions"></a>Outlook 表單區域

- [如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。

- [如何：防止 Outlook 顯示表單區域](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)。

### <a name="custom-menus"></a>自訂功能表

- [如何：將命令新增至快捷方式功能表](../vsto/how-to-add-commands-to-shortcut-menus.md)。

## <a name="excel-automation-tasks"></a><a name="excel"></a> Excel 自動化工作

- [如何：以程式設計方式在工作表儲存格中顯示字串](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md)。

- [如何：以程式設計方式建立新](../vsto/how-to-programmatically-create-new-workbooks.md)的活頁簿。

- [如何：以程式設計方式開啟活頁簿](../vsto/how-to-programmatically-open-workbooks.md)。

- [如何：以程式設計方式儲存活頁簿](../vsto/how-to-programmatically-save-workbooks.md)。

- [如何：以程式設計方式關閉活頁簿](../vsto/how-to-programmatically-close-workbooks.md)。

- [如何：以程式設計方式在活頁簿中加入新的工作表](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)。

- [如何：以程式設計方式隱藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)。

- [如何：以程式設計方式在活頁簿內移動工作表](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)。

- [如何：以程式設計方式保護活頁簿](../vsto/how-to-programmatically-protect-workbooks.md)。

- [如何：以程式設計方式在程式碼中參考工作表範圍](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)。

- [如何：以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)。

- [如何：以程式設計方式變更包含選定儲存格的工作表資料列格式](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)。

- [如何：以程式設計方式在工作表範圍中搜尋文字](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)。

- [如何：以程式設計方式列印工作表](../vsto/how-to-programmatically-print-worksheets.md)。

- [如何：以程式設計方式執行 Excel 計算](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)。

- [如何：以程式設計方式排序工作表中的資料](../vsto/how-to-programmatically-sort-data-in-worksheets.md)。

## <a name="word-automation-tasks"></a><a name="word"></a> Word 自動化工作

- [如何：以程式設計方式建立新檔](../vsto/how-to-programmatically-create-new-documents.md)。

- [如何：以程式設計方式開啟現有的檔](../vsto/how-to-programmatically-open-existing-documents.md)。

- [如何：以程式設計方式儲存檔](../vsto/how-to-programmatically-save-documents.md)。

- [如何：以程式設計方式關閉檔](../vsto/how-to-programmatically-close-documents.md)。

- [如何：以程式設計方式在 Word 檔中插入文字](../vsto/how-to-programmatically-insert-text-into-word-documents.md)。

- [如何：以程式設計方式定義和選取檔中的範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)。

- [如何：以程式設計方式重設 Word 檔中的範圍](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)。

- [如何：以程式設計方式格式化檔中的文字](../vsto/how-to-programmatically-format-text-in-documents.md)。

- [如何：將 XMLNode 控制項新增至 Word 檔](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)。

- [如何：以程式設計方式更新書簽文字](../vsto/how-to-programmatically-update-bookmark-text.md)。

- [如何：以程式設計方式搜尋和取代檔中的文字](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)。

- [如何：以程式設計方式列印檔案](../vsto/how-to-programmatically-print-documents.md)。

- [如何：以程式設計方式建立 Word 資料表](../vsto/how-to-programmatically-create-word-tables.md)。

- [如何：以程式設計方式將資料列和資料行加入至 Word 資料表](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)。

- [如何：以程式設計方式計算檔中的字元數](../vsto/how-to-programmatically-count-characters-in-documents.md)。

## <a name="data-tasks"></a><a name="data"></a> 資料工作

### <a name="data-bound-controls"></a>資料繫結控制項

- [如何：使用資料庫中的資料填入工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)。

- [如何：將資料庫的資料填入檔](../vsto/how-to-populate-documents-with-data-from-a-database.md)。

- [如何：將服務的資料填入檔](../vsto/how-to-populate-documents-with-data-from-services.md)。

- [如何：將物件的資料填入檔](../vsto/how-to-populate-documents-with-data-from-objects.md)。

- [如何：將資料庫的資料填入檔](../vsto/how-to-populate-documents-with-data-from-a-database.md)。

- [如何：將服務的資料填入檔](../vsto/how-to-populate-documents-with-data-from-services.md)。

- [如何：使用主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)。

### <a name="cached-data-in-document-level-solutions"></a>檔層級方案中的快取資料

- [如何：快取資料供離線使用或在伺服器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。

- [如何：以程式設計方式快取 Office 檔中的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)。

- [如何：快取受密碼保護檔中的資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)。

### <a name="custom-xml-data"></a>自訂 XML 資料

- [如何：將自訂 XML 元件加入至檔層級自訂](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)。

- [如何：使用 VSTO 增益集將自訂 XML 元件加入至檔](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)。

## <a name="server-side-document-management-tasks"></a><a name="server"></a> 伺服器端檔管理工作

- [如何：從檔移除 managed 程式碼延伸](../vsto/how-to-remove-managed-code-extensions-from-documents.md)模組。

- [如何：將 managed 程式碼擴充附加至檔](../vsto/how-to-attach-managed-code-extensions-to-documents.md)。

## <a name="security-tasks"></a><a name="security"></a> 安全性工作

- [如何：簽署 Office 方案](../vsto/how-to-sign-office-solutions.md)。

## <a name="deployment-tasks"></a><a name="deployment"></a> 部署工作

- [如何：使用 ClickOnce 發行 Office 方案](/previous-versions/bb386095(v=vs.110))。

- [如何：使用 ClickOnce 將檔層級 Office 方案發行至 SharePoint 伺服器](/previous-versions/bb608595(v=vs.110))。

- [如何：安裝 ClickOnce Office 方案](/previous-versions/bb608592(v=vs.110))。

- [如何：在終端使用者電腦上安裝必要條件以執行 Office 解決方案](/previous-versions/bb608608(v=vs.110))。

- [如何：準備 IIS 以部署 Office 方案](/previous-versions/bb608629(v=vs.110))。

- [如何：更新已部署的 Office 方案](/previous-versions/bb157871(v=vs.110))。

- [如何：變更 Office 方案的安裝路徑](/previous-versions/bb608626(v=vs.110))。

## <a name="see-also"></a>另請參閱
- [在 Visual Studio&#41;中開始 &#40;Office 開發 ](../vsto/getting-started-office-development-in-visual-studio.md)
- [依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)
- [Office 開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)