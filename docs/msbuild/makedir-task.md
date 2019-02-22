---
title: MakeDir 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MakeDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MakeDir task [MSBuild]
- MSBuild, MakeDir task
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e7e9e61ffd20828d73cef9c4ce3831d613d69bf
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922221"
---
# <a name="makedir-task"></a>MakeDir 工作
建立目錄，以及任何父目錄 (如有必要)。

## <a name="parameters"></a>參數
下表說明 `MakeDir` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`Directories`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 要建立的目錄集合。|
|`DirectoriesCreated`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 這項工作所建立的目錄。 如果無法建立某些目錄，就可能未包含所有已傳入 `Directories` 參數的項目。|

## <a name="remarks"></a>備註
除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其描述，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。

## <a name="example"></a>範例
下列程式碼範例使用 `MakeDir` 工作來建立 `OutputDirectory` 屬性所指定的目錄。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <OutputDirectory>\Output\</OutputDirectory>
    </PropertyGroup>

    <Target Name="CreateDirectories">
        <MakeDir
            Directories="$(OutputDirectory)"/>
    </Target>

</Project>
```

## <a name="see-also"></a>另請參閱
[工作](../msbuild/msbuild-tasks.md)  
[工作參考](../msbuild/msbuild-task-reference.md)
