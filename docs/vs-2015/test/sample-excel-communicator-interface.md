---
title: 範例 Excel Communicator 介面 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 13
ms.author: gewarren
manager: douge
ms.openlocfilehash: a1f544734cd00361162c461cd2b1682204075e10
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488898"
---
# <a name="sample-excel-communicator-interface"></a>範例 Excel Communicator 介面
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[範例 Excel Communicator 介面](https://docs.microsoft.com/visualstudio/test/sample-excel-communicator-interface)。  
  
範例 `IExcelUICommunication` 介面會用於 `ExcelAddIn` 專案中的 `ExcelUICommunicator` 物件。  
  
## <a name="iexceluicommunication-interface"></a>IExcelUICommunication 介面  
 這個介面會定義 `CodedUIExtension` (在自動程式化 UI 測試處理序中執行) 與 `ExcelCodedUIAddIn` (在 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 處理序中執行) 之間的通訊點。  
  
 `ExcelCodedUIAddinHelper` 組件具有衍生自此介面的 `ExcelUICommunicator` 類別，並且使用 Excel 物件模型來處理這些方法。  
  
 某些方法會從 Excel 取得要求的資訊，然後建立並傳回其中一個資訊物件，例如 `CellInformation` 物件。  
  
 其他方法會使用提供的資訊物件，尋找 Excel 中的對應控制項，並且針對此控制項進行某些處理。 例如，`ScrollIntoView` 方法會捲動工作表，以便顯示指定的儲存格。  
  
## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>CodedUIExtensibilitySample 與 ExcelCodedUIAddinHelper 通訊  
 `ExcelCodedUIAddinHelper` 組件會在 Excel 處理序中執行，而且具有 `UICommunicator` 類別，這個類別會實作 `IExcelUITestCommunication` 介面並且直接從 Excel UI 取得或設定必要的資訊。  
  
 `CodedUIExtensibilitySample` 組件會在 Visual Studio 自動程式化 UI 測試處理序中執行。 這個組件具有開啟 .NET 遠端處理通道的 `Communicator` 類別，並且提供 `Instance` 屬性，這個屬性會使用 `IExcelUICommunication` 介面，透過 `ExcelCodedUIAddinHelper` 組件中的 `UICommunicator` 物件，在兩個組件之間來回傳遞要求和資訊物件 (例如 `CellInformation` 物件)。  
  
## <a name="see-also"></a>另請參閱  
 [擴充自動程式化 UI 測試和動作記錄以支援 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [自動程式化 UI 測試的範例 Excel 增益集](../test/sample-excel-add-in-for-coded-ui-testing.md)   
 [Excel 的範例自動程式化 UI 測試擴充功能](../test/sample-coded-ui-test-extension-for-excel.md)



