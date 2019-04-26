---
title: ResolveManifestFiles 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cebb7c2449657112f3f13abc6c4589cba4f7ceb4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970779"
---
# <a name="resolvemanifestfiles-task"></a>ResolveManifestFiles 工作
將建置流程中的下列項目解析為檔案，以產生資訊清單：建置的項目、相依性、附屬項目、內容、偵錯符號和文件。

## <a name="parameters"></a>參數
 下表說明 `ResolveManifestFiles` 工作的參數。

|參數|說明|
|---------------|-----------------|
|`DeploymentManifestEntryPoint`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定部署資訊清單的名稱。|
|`EntryPoint`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定 Managed 組件或 ClickOnce 資訊清單參考，此為資訊清單的進入點。|
|`ExtraFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定額外的檔案。|
|`ManagedAssemblies`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定 Managed 組件。|
|`NativeAssemblies`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定原生組件。|
|`OutputAssemblies`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定產生的組件。|
|`OutputDeploymentManifestEntryPoint`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定輸出部署資訊清單的進入點。|
|`OutputEntryPoint`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定輸出進入點。|
|`OutputFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定輸出檔案。|
|`PublishFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定發行檔案。|
|`SatelliteAssemblies`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定附屬組件。|
|`SigningManifests`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，表示已簽署資訊清單。|
|`TargetCulture`|選擇性的 `String` 參數。<br /><br /> 指定附屬組件的目標文化特性。|
|`TargetFrameworkVersion`|選擇性的 `String` 參數。<br /><br /> 指定目標 .NET Framework 版本。|

## <a name="remarks"></a>備註
 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其描述，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。

## <a name="see-also"></a>另請參閱
- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)