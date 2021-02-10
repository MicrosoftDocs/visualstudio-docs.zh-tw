---
title: FindInList 工作 | Microsoft Docs
description: 瞭解如何使用 MSBuild FindInList 工作，在指定的清單中尋找具有相符專案的專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 45ad1cc57412161e2510f93cacb5a043be59802e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967549"
---
# <a name="findinlist-task"></a>FindInList 工作

在指定的清單中，尋找擁有相符 itemspec 的項目。

## <a name="parameters"></a>參數

 下表描述 [FindInList](../msbuild/findinlist-task.md)工作的參數。

|參數|Description|
|---------------|-----------------|
|`CaseSensitive`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，搜尋會區分大小寫；否則不區分大小寫。 預設值為 `true`。|
|`FindLastMatch`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，則傳回最後一個相符項目；否則傳回第一個相符項目。 預設值為 `false`。|
|`ItemFound`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 唯讀輸出參數。<br /><br /> 清單中找到的第一個符合項目 (如有)。|
|`ItemSpecToFind`|必要的 `String` 參數。<br /><br /> 要搜尋的 itemspec。|
|`List`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 要在其中搜尋 itemspec 的清單。|
|`MatchFileNameOnly`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，只比對 itemspec 的檔案名稱部分；否則比對整個 itemspec。 預設值為 `true`。|

## <a name="remarks"></a>備註

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
