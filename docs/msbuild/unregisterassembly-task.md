---
title: UnregisterAssembly 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 UnregisterAssembly 工作來取消註冊指定的元件，以供 COM interop 之用。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 23fe04834ebd66bae2bce50a63f7db9cb8281f2c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902514"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly 工作

針對 COM Interop 用途取消註冊指定的組件。 與 [RegisterAssembly 工作](../msbuild/registerassembly-task.md)執行的方式相反。

## <a name="parameters"></a>參數

 下表說明 `UnregisterAssembly` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`Assemblies`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要取消註冊的組件。|
|`AssemblyListFile`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 包含 `RegisterAssembly` 工作與 `UnregisterAssembly` 工作之間狀態的相關資訊。 如此可防止工作嘗試取消註冊無法在 `RegisterAssembly` 工作中註冊的組件。<br /><br /> 如果已指定此參數，則會忽略 `Assemblies` 和 `TypeLibFiles` 參數。|
|`TypeLibFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 從指定的組件中取消註冊指定的類型程式庫。 **注意：** 只有在類型程式庫檔案名稱與組件名稱不同時才需要此參數。|

## <a name="remarks"></a>備註

 此工作的成功不一定需要組件存在。 如果您嘗試取消註冊不存在的組件，工作將會完成並隨附警告。 這是因為此工作作業的目的是從登錄中移除組件註冊。 如果組件並不存在，就不存在於登錄中，因此工作就會成功。

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension> 類別中的參數，而該類別本身又繼承 <xref:System.MarshalByRefObject> 類別。 `MarshalByRefObject` 類別提供與 <xref:Microsoft.Build.Utilities.Task> 類別相同的功能，但可以在其專屬應用程式定義域中進行具現化。

## <a name="example"></a>範例

 下列範例會使用 `UnregisterAssembly` 工作來將 `OutputPath` 和 `FileName` 屬性所指定之路徑中的組件取消註冊 (如果存在的話)。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <OutputPath>\Output\</OutputPath>
        <FileName>MyFile.dll</FileName>
    </PropertyGroup>
    <Target Name="UnregisterAssemblies">
        <UnregisterAssembly
            Condition="Exists('$(OutputPath)$(FileName)')"
            Assemblies="$(OutputPath)$(FileName)" />
    </Target>

</Project>
```

## <a name="see-also"></a>另請參閱

- [RegisterAssembly 工作](../msbuild/registerassembly-task.md)
- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)