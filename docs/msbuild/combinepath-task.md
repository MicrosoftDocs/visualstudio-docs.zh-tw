---
title: CombinePath 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f7e6a79198ad54d3432f30fe9b57b3133a94165e
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288958"
---
# <a name="combinepath-task"></a>CombinePath 工作

將指定的路徑結合成單一路徑。
## <a name="task-parameters"></a>工作參數

 下表描述 [CombinePath 工作](../msbuild/combinepath-task.md)的參數。


|參數|說明|
|---------------|-----------------|
|`BasePath`|必要的 `String` 參數。<br /><br /> 要與其他路徑結合的基底路徑。 可以是相對路徑、絕對路徑或空白。|
|`Paths`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 要與 BasePath 結合以形成結合路徑的個別路徑清單。 路徑可為相對或絕對路徑。|
|`CombinedPaths`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 此工作所建立的結合路徑。|

## <a name="remarks"></a>備註

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其描述，請參閱[TaskExtension 基類](../msbuild/taskextension-base-class.md)。

 下列範例示範如何使用建立輸出檔案夾結構， `CombinePath` `$(OutputDirectory)` 方法是結合 `$(PublishRoot)` 與 `$(ReleaseDirectory)` 和子資料夾清單串連的根路徑來建立屬性 `$(LangDirectories)` 。

 ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <PublishRoot>C:\Site1\Release</PublishRoot>
  </PropertyGroup>

  <ItemGroup>
    <LangDirectories Include="en-us\;fr-fr\"/>
  </ItemGroup>

  <Target Name="CreateOutputDirectories" AfterTargets="Build">
    <CombinePath BasePath="$(PublishRoot)" Paths="@(LangDirectories)" >
      <Output TaskParameter="CombinedPaths" ItemName="OutputDirectories"/>
    </CombinePath>
    <MakeDir Directories="@(OutputDirectories)" />
  </Target>
```

唯一允許為清單的屬性 `CombinePath` 是 `Paths` ，在此情況下，輸出也是清單。 因此，如果 `$(PublishRoot)` 是*C:\Site1 \\ *，而且 `$(ReleaseDirectory)` 是*Release \\ *，而且 `@(LangDirectories)` 是*en-us \; fr-fr \\ *，則此範例會建立資料夾：

- C:\Site1\Release\en-us\
- C:\Site1\Release\fr-fr\

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
