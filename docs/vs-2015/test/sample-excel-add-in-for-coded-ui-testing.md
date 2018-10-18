---
title: 自動程式化 UI 測試的範例 Excel 增益集 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 18
ms.author: gewarren
manager: douge
ms.openlocfilehash: 564669d5af3ea526ad8822d3aea7310095151c6a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290676"
---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>自動程式化 UI 測試的範例 Excel 增益集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 的此範例增益集是特別設計來支援 Excel 工作表的自動程式碼 UI 測試，在 Visual Studio 企業版中記錄及執行 增益集是使用 Visual Studio Tools for Office 所建立的。  
  
 如需如何建立 Excel 增益集的詳細資訊，請參閱[逐步解說：建立 Excel 的第一個 VSTO 增益集](http://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)，或在 MSDN 中搜尋「Excel 增益集」。  
  
 雖然「Excel 增益集」不是適用於 Excel 的自動程式化 UI 測試延伸模組這份文件的主要主題，但是一些註解可能很有用。  
  
 此增益集的重要部分：  
  
-   `ThisAddIn` 類別 - 管理 `ExcelUICommunicator` 和 [Excel 的範例自動程式化 UI 測試延伸模組](../test/sample-coded-ui-test-extension-for-excel.md)之間的 .NET 遠端通道。  
  
-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx` - 用以測試增益集的安全性憑證。  
  
-   `ExcelUICommunicator` 類別 - 這個類別會實作 `IExcelUICommunication` 介面。  
  
## <a name="thisaddin-class"></a>ThisAddIn 類別  
 此類別大部分實際上是由 Visual Studio Tools for Office 在您建立您的 Excel 增益集專案時，在 `ThisAddIn.Designer.cs` 檔案中產生。  
  
 您必須實作的成員為事件處理常式：`ThisAddIn_Startup()` 和 `ThisAddIn_Shutdown()`。 其目的是要初始化或關閉 `ExcelUICommunicator` 所使用的.NET 遠端通道。  
  
## <a name="excelcodeduiaddinhelpertemporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey.pfx  
 此檔案包含暫存的安全性憑證，該憑證是由 Visual Studio Tools for Office 產生，並提供增益集封裝權限以在 Excel 處理序中運作來測試增益集和延伸模組。 您應該刪除此憑證，然後在專案 [屬性] 視窗的 [簽署] 索引標籤中建立一個新的憑證，或附加您自己的測試憑證。  
  
## <a name="exceluicommunicator-class"></a>ExcelUICommunicator 類別  
 這個類別會實作 `IExcelUITestCommunication` 介面，並且從 Excel 物件模型取得要求 UI 資訊。 如需詳細資訊，請參閱[範例 Excel Communicator 介面](../test/sample-excel-communicator-interface.md)。  
  
## <a name="see-also"></a>另請參閱  
 [擴充自動程式化 UI 測試和動作記錄以支援 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [逐步解說：建立 Excel 的第一個 VSTO 增益集](http://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)   
 [Office 和 SharePoint 開發](http://msdn.microsoft.com/library/2ddec047-263a-4901-a54c-a15fc8472329)



