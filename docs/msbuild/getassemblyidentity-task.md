---
title: GetAssemblyIdentity 工作 | Microsoft Docs
description: 使用 MSBuild GetAssemblyIdentity 工作從指定的檔案中取出元件身分識別，並輸出身分識別資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GetAssemblyIdentity task
- GetAssemblyIdentity task [MSBuild]
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 91a155e340f9ab246935f7b8cd6da46f3f364010
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914717"
---
# <a name="getassemblyidentity-task"></a>GetAssemblyIdentity 工作

從指定的檔案擷取組件識別，並輸出識別資訊。

## <a name="task-parameters"></a>工作參數

下表說明 `GetAssemblyIdentity` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`Assemblies`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含擷取的組件識別。|
|`AssemblyFiles`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要從中擷取識別的檔案。|

## <a name="remarks"></a>備註

`Assemblies` 參數所輸出的項目包含名為 `Version`、`PublicKeyToken` 和 `Culture` 的項目中繼資料項目。

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="example"></a>範例

下列範例會擷取 `MyAssemblies` 項目中指定的檔案識別，並將其輸出到 `MyAssemblyIdentities` 項目。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MyAssemblies Include="File1.dll;File2.dll" />
    </ItemGroup>
    <Target Name="RetrieveIdentities">
        <GetAssemblyIdentity AssemblyFiles="@(MyAssemblies)">
            <Output TaskParameter="Assemblies" ItemName="MyAssemblyIdentities" />
        </GetAssemblyIdentity>
    </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
