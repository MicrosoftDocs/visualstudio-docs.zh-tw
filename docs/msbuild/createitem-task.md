---
title: CreateItem 工作 | Microsoft Docs
description: 使用 MSBuild CreateItem 工作可將輸入專案填入專案集合，允許將專案從一個清單複製到另一個清單。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateItem
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateItem task [MSBuild]
- MSBuild, CreateItem task
ms.assetid: c4311f38-979e-4324-b524-9e8c1cbdc41a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f2d0e165171cb3619d3690e129e18f778504969e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901391"
---
# <a name="createitem-task"></a>CreateItem 工作

使用輸入項目填入項目集合。 這可將項目從一個清單複製到另一個。

> [!NOTE]
> 此工作已被取代。 從 .NET Framework 3.5 開始，項目 (Item) 群組可以放在 [Target](../msbuild/target-element-msbuild.md) 項目 (Element) 內。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。

## <a name="attributes"></a>屬性

 下表說明 `CreateItem` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`AdditionalMetadata`|選擇性 `String` 陣列參數。<br /><br /> 指定要附加至輸出項目的其他中繼資料。  使用下列語法來指定項目的中繼資料名稱和值：<br /><br /> *MetadataName* `=` *MetadataValue*<br /><br /> 您應該使用分號來分隔多個中繼資料名稱/值組。 如果名稱或值包含分號或其他任何特殊字元，則必須逸出它們。 如需詳細資訊，請參閱 [如何：在 MSBuild 中 Escape 特殊字元](../msbuild/how-to-escape-special-characters-in-msbuild.md)。|
|`Exclude`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定要從輸出項目集合中排除的項目。 此參數可以包含萬用字元規格。 如需詳細資訊，請參閱 [專案](../msbuild/msbuild-items.md) 和作法 [：從組建中排除](../msbuild/how-to-exclude-files-from-the-build.md)檔案。|
|`Include`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要包含在輸出項目集合中的項目。 此參數可以包含萬用字元規格。|
|`PreserveExistingMetadata`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `True`，僅會套用其他中繼資料 (如果它們還不存在)。|

## <a name="remarks"></a>備註

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="example"></a>範例

 下列程式碼範例會從項目集合 `MySourceItems` 建立名為 `MySourceItemsWithMetadata` 的新項目集合。 `CreateItem` 工作會使用 `MySourceItems` 項目中的項目來填入新的項目集合。 接著它會將名為 `MyMetadata` 且值為 `Hello` 的其他中繼資料項目 (Entry) 加入至新集合中的每個項目 (Item)。

 執行此工作之後，`MySourceItemsWithMetadata` 項目 (Item) 集合會包含 file1.resx 和 file2.resx 項目，這兩者皆擁有 `MyMetadata` 的中繼資料項目 (Entry)。 `MySourceItems` 項目集合會保持不變。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceItems Include="file1.resx;file2.resx" />
    </ItemGroup>

    <Target Name="NewItems">
        <CreateItem
            Include="@(MySourceItems)"
            AdditionalMetadata="MyMetadata=Hello">
           <Output
               TaskParameter="Include"
               ItemName="MySourceItemsWithMetadata"/>
        </CreateItem>

    </Target>

</Project>
```

 下表描述工作執行之後輸出項目的值。 項目中繼資料會顯示在項目之後的括號內。

|項目集合。|目錄|
|---------------------|--------------|
|`MySourceItemsWithMetadata`|*file1* (`MyMetadata="Hello"`) <br /><br /> *file2 (的 .resx* `MyMetadata="Hello"`) |

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)
- [工作](../msbuild/msbuild-tasks.md)
