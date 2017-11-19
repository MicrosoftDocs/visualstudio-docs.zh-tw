---
title: "Office 程式設計的一般工作 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
ms.assetid: 7afc9bad-1d31-486e-beea-91e6d308cd67
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4271669f7e40363e17375f9ee233e3f9c0b55b95
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="common-tasks-in-office-programming"></a>Office 程式設計的一般工作
  本主題旨在協助您找出下列類別之使用 Visual Studio 進行 Office 方案程式設計的相關常見問題解答。  
  
-   [安裝和一般工作](#projects)  
  
-   [使用者介面自訂工作](#ui)  
  
-   [Excel 自動化工作](#excel)。  
  
-   [Word 自動化工作](#word)  
  
-   [資料工作](#data)  
  
-   [伺服器端文件管理工作](#server)  
  
-   [安全性工作](#security)  
  
-   [部署工作](#deployment)  
  
##  <a name="projects"></a> Setup and General Tasks  
  
-   [如何： 在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
-   [如何：升級 Office 方案](http://msdn.microsoft.com/en-us/a269e539-b717-4680-a568-2152b070347e)。  
  
-   [How to: Install Office Primary Interop Assemblies](../vsto/how-to-install-office-primary-interop-assemblies.md).  
  
-   [How to: Target Office Applications Through Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
-   [如何： 在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
-   [How to: Open Office Solutions without Running Code](../vsto/how-to-open-office-solutions-without-running-code.md).  
  
-   [How to: Set Up Configuration Information for an Office Solution](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).  
  
-   [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
-   [How to: Show Add-in User Interface Errors](../vsto/how-to-show-add-in-user-interface-errors.md).  
  
##  <a name="ui"></a> User Interface Customization Tasks  
  
### <a name="controls-on-documents-and-worksheets"></a>文件和工作表上的控制項  
  
-   [How to: Add Windows Forms Controls to Office Documents](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
-   [How to: Add NamedRange Controls to Worksheets](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
-   [How to: Add ListObject Controls to Worksheets](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
-   [How to: Add Windows Forms Controls to Office Documents](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
-   [How to: Add Content Controls to Word Documents](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
-   [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
### <a name="task-panes-in-document-level-customizations"></a>文件層級自訂的工作窗格  
  
-   [如何： 執行窗格加入 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)。  
  
### <a name="task-panes-in-vsto-add-ins"></a>VSTO 增益集的工作窗格  
  
-   [How to: Add a Custom Task Pane to an Application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
### <a name="ribbon-customizations"></a>功能區自訂  
  
-   [How to: Get Started Customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
-   [如何： 變更功能區上的索引標籤的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)。  
  
-   [How to: Customize a Built-in Tab](../vsto/how-to-customize-a-built-in-tab.md).  
  
-   [如何： 將控制項加入 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)。  
  
-   [How to: Export a Ribbon from the Ribbon Designer to Ribbon XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### <a name="outlook-form-regions"></a>Outlook 表單區域  
  
-   [How to: Add a Form Region to an Outlook Add-in Project](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
-   [How to: Prevent Outlook from Displaying a Form Region](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).  
  
### <a name="custom-menus"></a>自訂功能表  
  
-   [如何： 將命令加入至快顯功能表](../vsto/how-to-add-commands-to-shortcut-menus.md)。  
  
##  <a name="excel"></a> Excel Automation Tasks  
  
-   [如何： 以程式設計方式在工作表儲存格中顯示字串](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md)。  
  
-   [如何： 以程式設計方式建立新的活頁簿](../vsto/how-to-programmatically-create-new-workbooks.md)。  
  
-   [如何： 以程式設計方式開啟活頁簿](../vsto/how-to-programmatically-open-workbooks.md)。  
  
-   [如何： 以程式設計方式儲存活頁簿](../vsto/how-to-programmatically-save-workbooks.md)。  
  
-   [如何： 以程式設計方式關閉活頁簿](../vsto/how-to-programmatically-close-workbooks.md)。  
  
-   [如何： 以程式設計方式在活頁簿中加入新的工作表](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)。  
  
-   [如何： 以程式設計方式隱藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)。  
  
-   [如何： 以程式設計方式移動工作表在活頁簿內](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)。  
  
-   [如何： 以程式設計方式保護活頁簿](../vsto/how-to-programmatically-protect-workbooks.md)。  
  
-   [如何： 以程式設計方式在程式碼中的工作表範圍參考](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)。  
  
-   [如何： 以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)。  
  
-   [如何： 以程式設計方式變更工作表包含選取儲存格的資料列中的格式化](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)。  
  
-   [如何： 以程式設計方式搜尋工作表範圍中的文字](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)。  
  
-   [如何： 以程式設計方式列印工作表](../vsto/how-to-programmatically-print-worksheets.md)。  
  
-   [如何： 以程式設計方式執行 Excel 計算](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)。  
  
-   [如何： 以程式設計的方式排序工作表中的資料](../vsto/how-to-programmatically-sort-data-in-worksheets.md)。  
  
##  <a name="word"></a> Word Automation Tasks  
  
-   [如何： 以程式設計方式建立新文件](../vsto/how-to-programmatically-create-new-documents.md)。  
  
-   [如何： 以程式設計方式開啟現有文件](../vsto/how-to-programmatically-open-existing-documents.md)。  
  
-   [如何： 以程式設計方式儲存文件](../vsto/how-to-programmatically-save-documents.md)。  
  
-   [如何： 以程式設計方式關閉文件](../vsto/how-to-programmatically-close-documents.md)。  
  
-   [如何： 以程式設計方式將文字插入 Word 文件](../vsto/how-to-programmatically-insert-text-into-word-documents.md)。  
  
-   [如何： 以程式設計方式定義及選取範圍中的文件](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)。  
  
-   [如何： 以程式設計方式在 Word 中重設範圍的文件](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)。  
  
-   [如何： 以程式設計的方式格式化文件中的文字](../vsto/how-to-programmatically-format-text-in-documents.md)。  
  
-   [How to: Add XMLNode Controls to Word Documents](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
-   [如何： 以程式設計方式更新書籤文字](../vsto/how-to-programmatically-update-bookmark-text.md)。  
  
-   [如何： 以程式設計方式搜尋和取代文件中的文字](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)。  
  
-   [如何： 以程式設計方式列印文件](../vsto/how-to-programmatically-print-documents.md)。  
  
-   [如何： 以程式設計方式建立 Word 表格](../vsto/how-to-programmatically-create-word-tables.md)。  
  
-   [如何： 以程式設計方式將資料列和資料行加入至 Word 表格](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)。  
  
-   [如何： 以程式設計方式在文件中的字元計數](../vsto/how-to-programmatically-count-characters-in-documents.md)。  
  
##  <a name="data"></a> Data Tasks  
  
### <a name="data-bound-controls"></a>資料繫結控制項  
  
-   [How to: Populate Worksheets with Data from a Database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md).  
  
-   [How to: Populate Documents with Data from a Database](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
-   [How to: Populate Documents with Data from Services](../vsto/how-to-populate-documents-with-data-from-services.md).  
  
-   [How to: Populate Documents with Data from Objects](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
-   [How to: Populate Documents with Data from a Database](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
-   [How to: Populate Documents with Data from Services](../vsto/how-to-populate-documents-with-data-from-services.md).  
  
-   [How to: Update a Data Source with Data from a Host Control](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
### <a name="cached-data-in-document-level-solutions"></a>文件層級自訂中的快取資料  
  
-   [How to: Cache Data for Use Offline or on a Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   [How to: Programmatically Cache a Data Source in an Office Document](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
-   [How to: Cache Data in a Password-Protected Document](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
### <a name="custom-xml-data"></a>自訂 XML 資料  
  
-   [How to: Add Custom XML Parts to Document-Level Customizations](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).  
  
-   [How to: Add Custom XML Parts to Documents by Using VSTO Add-Ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)。  
  
##  <a name="server"></a> Server-side Document Management Tasks  
  
-   [如何： 從文件移除 Managed 程式碼擴充](../vsto/how-to-remove-managed-code-extensions-from-documents.md)。  
  
-   [如何： 將 Managed 程式碼擴充附加至文件](../vsto/how-to-attach-managed-code-extensions-to-documents.md)。  
  
##  <a name="security"></a> Security Tasks  
  
-   [如何： 簽署 Office 方案](../vsto/how-to-sign-office-solutions.md)。  
  
##  <a name="deployment"></a> Deployment Tasks  
  
-   [如何：使用 ClickOnce 發行 Office 方案](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)。  
  
-   [如何：使用 ClickOnce 將文件層級的 Office 方案發行至 SharePoint Server](http://msdn.microsoft.com/en-us/2408e809-fb78-42a1-9152-00afa1522e58)。  
  
-   [如何：安裝 ClickOnce Office 方案](http://msdn.microsoft.com/en-us/14702f48-9161-4190-994c-78211fe18065)。  
  
-   [如何：在使用者電腦上安裝必要條件來執行 Office 方案](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)。  
  
-   [如何：準備 IIS 來部署 Office 方案](http://msdn.microsoft.com/en-us/f62bce70-81d4-4f8b-86e6-2f2afec5d9b4)。  
  
-   [如何：更新已部署的 Office 方案](http://msdn.microsoft.com/en-us/be96db53-b6ea-46ab-b8d9-b76b098b3b13)。  
  
-   [如何：變更 Office 方案的安裝路徑](http://msdn.microsoft.com/en-us/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)。  
  
## <a name="see-also"></a>另請參閱  
 [開始使用 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/getting-started-office-development-in-visual-studio.md)   
 [依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)   
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)  
  
  