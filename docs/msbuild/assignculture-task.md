---
title: AssignCulture 工作 | Microsoft Docs
description: 使用 MSBuild AssignCulture 工作產生具有名為文化特性之中繼資料的專案，其中包含對應的文化特性識別碼。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AssignCulture task
- AssignCulture task [MSBuild]
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c837046380550f5a0a73aaba888cbf26be0c1586
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923837"
---
# <a name="assignculture-task"></a>AssignCulture 工作

這項工作接受項目清單檔案名稱中包含有效的 .NET 文化特性識別碼字串，而產生的項目有包含對應的文化特性識別碼中繼資料，名為 `Culture`。 例如，檔案名 *Form1.fr-fr* 具有內嵌文化特性識別碼 "fr-fr"，因此此工作會產生具有與中繼資料相等的相同檔案名的專案 `Culture` `fr-fr` 。 工作也會產生檔名移除了文化特性的檔案名稱清單。

## <a name="task-parameters"></a>工作參數

下表說明 `AssignCulture` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`AssignedFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含以 `Files` 參數接收到的項目清單，每個項目都會新增 `Culture` 中繼資料項目。<br /><br /> 如果從 `Files` 參數傳入的項目已包含 `Culture` 中繼資料項目，則使用原始的中繼資料項目。<br /><br /> 如果檔案名稱中包含有效的文化特性識別碼，此工作只會指派 `Culture` 中繼資料項目。 文化特性識別碼必須介於檔案名稱的最後兩個點之間。|
|`AssignedFilesWithCulture`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含來自 `AssignedFiles` 參數，具有 `Culture` 中繼資料項目的項目子集。|
|`AssignedFilesWithNoCulture`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含來自 `AssignedFiles` 參數，沒有 `Culture` 中繼資料項目的項目子集。|
|`CultureNeutralAssignedFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含在 `AssignedFiles` 參數中產生的相同項目清單，除非檔案名稱移除文化特性。<br /><br /> 如果是有效的文化特性識別碼，此工作只會移除檔案名稱中的文化特性。|
|`Files`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定檔案清單，內嵌要指派文化特性的文化特性名稱。|

## <a name="remarks"></a>備註

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="example"></a>範例

 下列範例會執行附 `ResourceFiles` 項目集合的 `AssignCulture` 工作。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ResourceFiles Include="MyResource1.fr.resx"/>
        <ResourceFiles Include="MyResource2.XX.resx"/>
    </ItemGroup>

    <Target Name="Culture">
        <AssignCulture
            Files="@(ResourceFiles)"
            <Output TaskParameter="AssignedFiles"
                ItemName="OutAssignedFiles"/>
            <Output TaskParameter="AssignedFilesWithCulture"
                ItemName="OutAssignedFilesWithCulture"/>
            <Output TaskParameter="AssignedFilesWithNoCulture"
                ItemName="OutAssignedFilesWithNoCulture"/>
            <Output TaskParameter="CultureNeutralAssignedFiles"
                ItemName="OutCultureNeutralAssignedFiles"/>
        </AssignCulture>
    </Target>
</Project>
```

下表描述工作執行之後輸出項目的值。 項目中繼資料會顯示在項目之後的括號內。

|項目集合。|目錄|
|---------------------|--------------|
|`OutAssignedFiles`|*MyResource1.fr.resx* (Culture="fr")<br /><br /> *MyResource2.XX.resx* (沒有額外的中繼資料)|
|`OutAssignedFilesWithCulture`|*MyResource1.fr.resx* (Culture="fr")|
|`OutAssignedFilesWithNoCulture`|*MyResource2.XX.resx* (沒有額外的中繼資料)|
|`OutCultureNeutralAssignedFiles`|*MyResource1.resx* (Culture="fr")<br /><br /> *MyResource2.XX.resx* (沒有額外的中繼資料)|

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
