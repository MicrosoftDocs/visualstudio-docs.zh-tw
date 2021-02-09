---
title: FindAppConfigFile 工作 | Microsoft Docs
description: 瞭解如何使用 MSBuild FindAppConfigFile 工作，在提供的清單中尋找 app.config 檔案（如果有的話）。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ff26ee3505671d29df610278d701803b816d30f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877131"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile 工作

在提供的清單中尋找 *app.config* 檔案（如果有的話）。

## <a name="parameters"></a>參數

 下表說明 `FindAppConfigFile` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`AppConfigFile`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定清單中找到的第一個符合項目 (如果有的話)。|
|`PrimaryList`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要搜尋的主要清單。|
|`SecondaryList`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要搜尋的次要清單。|
|`TargetPath`|必要的 `String` 參數。<br /><br /> 指定要新增為中繼資料的值。|

## <a name="remarks"></a>備註

 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
