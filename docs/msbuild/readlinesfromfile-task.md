---
title: ReadLinesFromFile 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ReadLinesFromFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ReadLinesFromFile task
- ReadLinesFromFile task [MSBuild]
ms.assetid: a18af929-b53a-4d9e-b7bf-e3d3737ee85f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aeb6e43e315aceef5028e77480b2817cd8edb030
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597356"
---
# <a name="readlinesfromfile-task"></a>ReadLinesFromFile 工作
從文字檔讀取項目清單。

## <a name="parameters"></a>參數
 下表說明 `ReadLinesFromFile` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`File`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要讀取的檔案。 檔案的每一行都必須有一個項目。|
|`Lines`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含從檔案讀取的行。|

## <a name="remarks"></a>備註
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其描述，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。

## <a name="example"></a>範例
 下列範例使用 `ReadLinesFromFile` 工作，以從文字檔的清單中建立項目。 從檔案讀取的項目會儲存在 `ItemsFromFile` 項目集合中。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyTextFile Include="Items.txt"/>
    </ItemGroup>

    <Target Name="ReadFromFile">
        <ReadLinesFromFile
            File="@(MyTextFile)" >
            <Output
                TaskParameter="Lines"
                ItemName="ItemsFromFile"/>
        </ReadLinesFromFile>
    </Target>

</Project>
```

## <a name="see-also"></a>請參閱
- [工作參考](../msbuild/msbuild-task-reference.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [工作](../msbuild/msbuild-tasks.md)
