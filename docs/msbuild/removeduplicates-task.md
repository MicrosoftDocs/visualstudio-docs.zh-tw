---
title: RemoveDuplicates 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 RemoveDuplicates 工作，從指定的專案集合中移除重複的專案。
ms.custom: SEO-VS-2020
ms.date: 03/01/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5bb2a260f0b9903837b6f1bb8ce8a2e4a2fe691e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931782"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates 工作

從指定的項目集合中移除重複項目。

## <a name="parameters"></a>參數

 下表說明 `RemoveDuplicates` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`Filtered`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含已移除所有重複項目的項目集合。 系統會保存輸入項目的順序，保留每個重複項目的第一個執行個體。|
|`Inputs`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 要從中移除重複項目的項目集合。|

## <a name="remarks"></a>備註

 此工作不區分大小寫，而且在判斷重複項目時不會比較項目中繼資料。

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="example"></a>範例

 下列範例使用 `RemoveDuplicates` 工作，以從 `MyItems` 項目集合中移除重複項目。 工作完成時，`FilteredItems` 項目集合會包含一個項目。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyItems Include="MyFile.cs"/>
        <MyItems Include="MyFile.cs">
            <Culture>fr</Culture>
        </MyItems>
        <MyItems Include="myfile.cs"/>
    </ItemGroup>

    <Target Name="RemoveDuplicateItems">
        <RemoveDuplicates
            Inputs="@(MyItems)">
            <Output
                TaskParameter="Filtered"
                ItemName="FilteredItems"/>
        </RemoveDuplicates>
    </Target>
</Project>
```

 下列範例顯示 `RemoveDuplicates` 工作會保留其輸入順序。 當工作完成時， `FilteredItems` 專案集合會以該順序包含 *MyFile2.cs*、 *MyFile1.cs* 和 *MyFile3.cs* 專案。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyItems Include="MyFile2.cs"/>
        <MyItems Include="MyFile1.cs" />
        <MyItems Include="MyFile3.cs" />
        <MyItems Include="myfile1.cs"/>
    </ItemGroup>

    <Target Name="RemoveDuplicateItems">
        <RemoveDuplicates
            Inputs="@(MyItems)">
            <Output
                TaskParameter="Filtered"
                ItemName="FilteredItems"/>
        </RemoveDuplicates>
    </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [工作](../msbuild/msbuild-tasks.md)
