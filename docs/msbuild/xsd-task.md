---
title: "XSD 工作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
caps.latest.revision: "13"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e45350598a50709a411da270e3607197a36ee20b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xsd-task"></a>XSD 工作
包裝 XML 結構描述定義工具 (xsd.exe)，其會從來源產生結構描述或類別檔案。  
  
## <a name="parameters"></a>參數  
 下表說明 **XSD** 工作的參數。  
  
-   **AdditionalOptions**  
  
     選擇性的 **String** 參數。  
  
     選項的清單，如命令列上所指定。 例如 "*/option1 /option2 /option#*"。 使用這個參數來指定任何其他 **XSD** 工作參數未表示的選項。  
  
-   **GenerateFromSchema**  
  
     選擇性的 **String** 參數。  
  
     指定從指定的結構描述產生的類型。  
  
     指定下列其中一個值，每個值會分別對應至一個 XSD 選項。  
  
    -   **classes** - **/classes**  
  
    -   **dataset** - **/dataset**  
  
-   **Language**  
  
     選擇性的 **String** 參數。  
  
     指定產生的程式碼要使用的程式語言。  
  
     可以選擇 **CS** (C#，此為預設值)、**VB** (Visual Basic) 或 **JS** (JScript)。 您可以對實作 `System.CodeDom.Compiler.CodeDomProvider Class` 的類別指定完整名稱。  
  
-   **Namespace**  
  
     選擇性的 **String** 參數。  
  
     指定產生的型別的執行階段命名空間。  
  
-   **Sources**  
  
     必要的 `ITaskItem[]` 參數。  
  
     定義工作可以耗用和發出的 MSBuild 來源檔案項目的陣列。  
  
-   **SuppressStartupBanner**  
  
     選擇性的 **Boolean** 參數。  
  
     如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。  
  
-   **TrackerLogDirectory**  
  
     選擇性的 **String** 參數。  
  
     指定追蹤器記錄檔的目錄。  
  
## <a name="see-also"></a>請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)