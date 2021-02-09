---
title: WriteCodeFragment 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 WriteCodeFragment 工作，從指定的產生的程式碼片段產生暫存程式碼檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1bdab6066ce93475a2f6bb193c67da87c4fcaddd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888078"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment 工作

從指定產生的程式碼片段來產生暫存程式碼檔。 不會刪除該檔案。

## <a name="parameters"></a>參數

 下表說明 `WriteCodeFragment` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`AssemblyAttributes`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 要撰寫之屬性的描述。 項目 `Include` 值是屬性的完整類型名稱，例如，"System.AssemblyVersionAttribute"。<br /><br /> 每個中繼資料都是參數的名稱/值組，其必須為類型 `String`。 有些屬性只允許位置建構函式引數。 不過，您可以在任何屬性中使用這類引數。 若要設定位置建構函式屬性，請使用與 "_Parameter1"、"_Parameter2" 等等類似的中繼資料名稱。<br /><br /> 參數索引不能予以跳過。|
|`Language`|必要的 `String` 參數。<br /><br /> 指定要產生之程式碼的語言。<br /><br /> `Language` 可以是 CodeDom 提供者所提供的任何語言 (例如 "C#" 或 "VisualBasic")。 發出的檔案會具有該語言的預設副檔名。|
|`OutputDirectory`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定所產生程式碼的目的地資料夾，通常是中繼資料夾。|
|`OutputFile`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定已產生檔案的路徑。 如果使用檔案名稱來設定此參數，則會在檔案名稱的前面加上目的地資料夾。 如果使用根設定它，則會忽略目的地資料夾。<br /><br /> 如果未設定此參數，輸出檔案名稱就是目的地資料夾、任意檔案名稱，以及所指定語言的預設副檔名。|

## <a name="remarks"></a>備註

 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
