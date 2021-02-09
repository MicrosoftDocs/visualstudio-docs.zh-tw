---
title: RequiresFramework35SP1Assembly 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 RequiresFramework35SP1Assembly 工作，判斷應用程式是否需要 .NET Framework 3.5 SP1。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RequiresFramework35SP1Assembly task [MSBuild]
- MSBuild, RequiresFramework35SP1Assembly task
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04b435df9b028689ea6c0d1f2c61e7e8df8bb8bb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931756"
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly 工作

判斷應用程式是否需要 .NET Framework 3.5 SP1。

## <a name="parameters"></a>參數

 下表說明 `RequiresFramework35SP1Assembly` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`Assemblies`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定應用程式中所參考的組件。|
|`CreateDesktopShortcut`|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true`，會在安裝期間於桌面上建立捷徑圖示。|
|`DeploymentManifestEntryPoint`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定應用程式的資訊清單檔名稱。|
|`EntryPoint`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定應該在執行應用程式時所執行的組件。|
|`ErrorReportUrl`|選擇性的 `String` 參數。<br /><br /> 指定在 ClickOnce 安裝期間所產生的對話方塊中顯示的網站。|
|`Files`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定將在發行應用程式時部署的檔案清單。|
|`ReferencedAssemblies`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定專案中所參考的組件。|
|`RequiresMinimumFramework35SP1`|選擇性的 `Boolean` 輸出參數。<br /><br /> 如果 `true`，則應用程式需要 .NET Framework 3.5 SP1。|
|`SigningManifests`|選擇性的 `Boolean` 輸出參數。<br /><br /> 如果 `true`，會簽署 ClickOnce 資訊清單。|
|`SuiteName`|選擇性的 `String` 參數。<br /><br /> 指定 [啟動] 功能表上將安裝應用程式的資料夾名稱。|
|`TargetFrameworkVersion`|選擇性的 `String` 參數。<br /><br /> 指定此應用程式作為目標的 .NET Framework 版本。|

## <a name="remarks"></a>備註

 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)