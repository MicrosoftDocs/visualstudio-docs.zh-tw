---
title: CreateVisualBasicManifestResourceName 工作 | Microsoft Docs
description: 使用 MSBuild CreateVisualBasicManifestResourceName 工作，從給定的 .resx 檔案名或其他資源建立 Visual Basic 樣式的資訊清單名稱。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8e9f0868cb774ee82c79ba190acddebf63193cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901387"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName 工作

從給定的 *.resx* 檔案名或其他資源建立 Visual Basic 樣式的資訊清單名稱。

## <a name="parameters"></a>參數

 下表描述 [CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md)工作的參數。

| 參數 | Description |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem>`[]`輸出唯讀參數。<br /><br /> 產生的資訊清單名稱。 |
| `ResourceFiles` | 必要的 `String` 參數。<br /><br /> 建立 Visual Basic 資訊清單名稱的來源資源檔名稱。 |
| `RootNamespace` | 選擇性的 `String` 參數。<br /><br /> 資源檔的根命名空間，通常取自專案檔。 可以是 `null`。 |
| `PrependCultureAsDirectory` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，就會在資訊清單資源名稱正前方加入文化特性名稱做為目錄名稱。 預設值為 `true`。 |
| `ResourceFilesWithManifestResourceNames` | 選擇性的 `String` 唯讀輸出參數。<br /><br /> 傳回現在包含資訊清單資源名稱的資源檔名稱。 |

## <a name="remarks"></a>備註

 [CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md)工作會決定要指派給指定 *.resx* 或其他資源檔的適當資訊清單資源名稱。 此工作會為資源檔提供邏輯名稱，然後將它附加到輸出參數做為中繼資料。

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
