---
title: GetReferenceAssemblyPaths 工作 | Microsoft Docs
description: 使用 MSBuild GetReferenceAssemblyPaths 工作可傳回各種架構的參考元件路徑。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d3e0afdc7486e4337a92e3639c23c404050a84c4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914617"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths 工作

傳回各種架構的參考組件路徑。

## <a name="parameters"></a>參數

 下表說明 `GetReferenceAssemblyPaths` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`ReferenceAssemblyPaths`|選擇性的 `String[]` 輸出參數。<br /><br /> 根據 `TargetFrameworkMoniker` 參數傳回路徑。 如果 `TargetFrameworkMoniker` 是 Null 或空白，則此路徑為 `String.Empty`。|
|`FullFrameworkReferenceAssemblyPaths`|選擇性的 `String[]` 輸出參數。<br /><br /> 根據 `TargetFrameworkMoniker` 參數傳回路徑，而不考慮 Moniker 的設定檔部分。 如果 `TargetFrameworkMoniker` 是 Null 或空白，則此路徑為 `String.Empty`。|
|`TargetFrameworkMoniker`|選擇性的 `String` 參數。<br /><br /> 指定與參考組件路徑建立關聯的目標 Framework Moniker。|
|`RootPath`|選擇性的 `String` 參數。<br /><br /> 指定要用來產生參考組件路徑的根路徑。|
|`BypassFrameworkInstallChecks`|選擇性的 <xref:System.Boolean> 參數。<br /><br /> 如果為 `true`，則會略過 `GetReferenceAssemblyPaths` 預設執行的基本檢查，以確定已根據目標 Framework 來安裝特定執行階段 Framework。|
|`TargetFrameworkMonikerDisplayName`|選擇性的 `String` 輸出參數。<br /><br /> 指定目標 Framework Moniker 的顯示名稱。|

## <a name="remarks"></a>備註

 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)