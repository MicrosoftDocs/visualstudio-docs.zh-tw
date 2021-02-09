---
title: FormatUrl 工作 | Microsoft Docs
description: 瞭解如何使用 MSBuild FormatUrl 工作，將輸入 URL 轉換成正確的輸出 URL 格式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9a05ce16289c012b067faa5bc302a3921cbe1c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888091"
---
# <a name="formaturl-task"></a>FormatUrl 工作

將 URL 轉換為正確的 URL 格式。

## <a name="parameters"></a>參數

 下表說明 `FormatUrl` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`InputUrl`|選擇性的 `String` 參數。<br /><br /> 指定要格式化的 URL。|
|`OutputUrl`|選擇性的 `String` 輸出參數。<br /><br /> 指定已格式化 URL。|

## <a name="remarks"></a>備註

 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)