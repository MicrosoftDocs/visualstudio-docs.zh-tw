---
title: CreateCSharpManifestResourceName 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8e72ef282911ecb36fb9a16838f6cc311e253e1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634353"
---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName 工作

從給定*的 .resx*檔案名或其他資源創建 C#樣式的清單名稱。

## <a name="parameters"></a>參數

 下表描述了[CreateCSharpManifest 資源名稱任務的](../msbuild/createcsharpmanifestresourcename-task.md)參數。

| 參數 | 描述 |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem>`[]`輸出唯讀參數。<br /><br /> 產生的資訊清單名稱。 |
| `ResourceFiles` | 必要的 `String` 參數。<br /><br /> 建立 C# 資訊清單名稱的來源資源檔名稱。 |
| `RootNamespace` | 選擇性的 `String` 參數。<br /><br /> 資源檔的根命名空間，通常取自專案檔。 可能為 `null`。 |
| `PrependCultureAsDirectory` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，就會在資訊清單資源名稱正前方加入文化特性名稱做為目錄名稱。 預設值為 `true`。 |
| `ResourceFilesWithManifestResourceNames` | 選擇性的 `String` 唯讀輸出參數。<br /><br /> 傳回現在包含資訊清單資源名稱的資源檔名稱。 |

## <a name="remarks"></a>備註

 [CreateVisualBasicManifestResourceName 任務](../msbuild/createvisualbasicmanifestresourcename-task.md)確定要分配給給定 *.resx*或其他資源檔的相應清單資源名稱。 此工作會為資源檔提供邏輯名稱，然後將它附加到輸出參數做為中繼資料。

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 有關這些附加參數及其說明的清單，請參閱[任務擴展基類](../msbuild/taskextension-base-class.md)。

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [任務引用](../msbuild/msbuild-task-reference.md)
