---
title: XSD 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 XSD 工作包裝 XML 架構定義工具 xsd.exe，其會從來源產生架構或類別檔案。
ms.custom: SEO-VS-2020
ms.date: 06/27/2018
ms.topic: reference
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
- XSD task (MSBuild (C++))
- MSBuild (C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7227fff5dd4c58e1bce81ef8cad5c32f854abf55
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960321"
---
# <a name="xsd-task"></a>XSD 工作

包裝 XML 架構定義工具 (*xsd.exe*) ，它會從來源產生架構或類別檔案。

> [!NOTE]
> 從 Visual Studio 2017 開始，*xsd.exe* 的 C++ 專案支援已過時。 您仍然可以將 *CppCodeProvider.dll* 手動新增至 GAC 來使用 **Microsoft.VisualC.CppCodeProvider** API。

## <a name="parameters"></a>參數

 下表說明 **XSD** 工作的參數。

- **AdditionalOptions**

     選擇性的 **字串** 參數。

     選項的清單，如命令列上所指定。 例如，/ \<option1>  / \<option2>  / \<option#> 。 使用這個參數來指定任何其他 **XSD** 工作參數未表示的選項。

- **GenerateFromSchema**

  選擇性的 **字串** 參數。

  指定從指定的結構描述產生的類型。

  指定下列其中一個值，每個值會分別對應至一個 XSD 選項。

  - **類別**  - **/classes**

  - **資料集**  - **/dataset**

- **Language**

     選擇性的 **字串** 參數。

     指定產生的程式碼要使用的程式語言。

     可以選擇 **CS** (C#，此為預設值)、**VB** (Visual Basic) 或 **JS** (JScript)。 您可以對實作 `System.CodeDom.Compiler.CodeDomProvider Class` 的類別指定完整名稱。

- **Namespace**

     選擇性的 **字串** 參數。

     指定產生的型別的執行階段命名空間。

- **來源**

     必要的 `ITaskItem[]` 參數。

     定義工作可以耗用和發出的 MSBuild 來源檔案項目的陣列。

- **SuppressStartupBanner**

     選擇性的 **布林值** 參數。

     如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。

- **TrackerLogDirectory**

     選擇性的 **字串** 參數。

     指定追蹤器記錄檔的目錄。

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)
