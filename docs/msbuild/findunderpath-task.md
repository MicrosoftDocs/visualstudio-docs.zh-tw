---
title: FindUnderPath 工作 | Microsoft Docs
description: 使用 MSBuild FindUnderPath 工作，在指定的專案集合中尋找具有指定之資料夾內或下方路徑的專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FindUnderPath task
- FindUnderPath task [MSBuild]
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 82275b14fbda0d63e6235b87b55a0dbb5f2416b0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949424"
---
# <a name="findunderpath-task"></a>FindUnderPath 工作

判斷指定項目集合中哪些項目的路徑位於指定資料夾或其子資料夾中。

## <a name="parameters"></a>參數

下表說明 `FindUnderPath` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`Files`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定其路徑應該與 `Path` 參數所指定的路徑進行比較的檔案。|
|`InPath`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含指定路徑下找到的項目。|
|`OutOfPath`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含指定路徑下未找到的項目。|
|`Path`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要作為參考的資料夾路徑。|
|`UpdateToAbsolutePaths`|選擇性的 `Boolean` 參數。<br /><br /> 如果輸出項目的路徑已更新為絕對路徑，則為 true。|

## <a name="remarks"></a>備註

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="example"></a>範例

下列範例使用 `FindUnderPath` 工作，來判斷 `MyFiles` 項目中所包含的檔案路徑是否已存在於 `SearchPath` 屬性指定的路徑下。 工作完成之後，`FilesNotFoundInPath` 項目包含 *File1.txt* 檔案，而 `FilesFoundInPath` 項目包含 *File2.txt* 檔案。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MyFiles Include="C:\File1.txt" />
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />
    </ItemGroup>

    <PropertyGroup>
        <SearchPath>C:\Projects\MyProject</SearchPath>
    </PropertyGroup>

    <Target Name="FindFiles">
        <FindUnderPath
            Files="@(MyFiles)"
            Path="$(SearchPath)">
            <Output
                TaskParameter="InPath"
                ItemName="FilesFoundInPath" />
            <Output
                TaskParameter="OutOfPath"
                ItemName="FilesNotFoundInPath" />
        </FindUnderPath>
    </Target>

</Project>
```

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)
- [工作](../msbuild/msbuild-tasks.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
