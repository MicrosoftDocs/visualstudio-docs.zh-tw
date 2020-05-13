---
title: WriteLinesToFile 工作 | Microsoft Docs
ms.date: 09/20/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b78ac2347a5143aeb532a4bcc294551430584b4a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630661"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile 工作

將所指定項目的路徑寫入至指定的文字檔。

## <a name="task-parameters"></a>工作參數

 下表說明 `WriteLinestoFile` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`File`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要寫入項目的檔案。|
|`Lines`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要寫入至檔案的項目。|
|`Overwrite`|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true`，則工作會覆寫檔案中的任何現有內容。|
|`Encoding`|選擇性的 `String` 參數。<br /><br /> 選取字元編碼 (例如，"Unicode")。  另請參閱 <xref:System.Text.Encoding>。|
|`WriteOnlyWhenDifferent`|選擇性的 `Boolean` 參數。<br /><br /> 若為 `true`，則會先讀取指定的目標檔案 (如果存在)，以便與已經寫入的工作進行比較。 如果相同，則不會將檔案寫入到磁碟，而且將會保留時間戳記。|

## <a name="remarks"></a>備註

 如果 `Overwrite` 是 `true`，會建立新檔案，並將內容寫入至檔案，然後關閉檔案。 如果檔案已經存在，則會覆寫該檔案。 如果 `Overwrite` 是 `false`，會將內容附加至檔案，如果目標檔案不存在，則會建立該檔案。

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 有關這些附加參數及其說明的清單，請參閱[任務擴展基類](../msbuild/taskextension-base-class.md)。

## <a name="example"></a>範例

 下列範例會使用 `WriteLinesToFile` 工作將 `MyItems` 項目集合中的項目路徑寫入至 `MyTextFile` 項目集合所指定的檔案。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyTextFile Include="Items.txt"/>
        <MyItems Include="*.cs"/>
    </ItemGroup>

    <Target Name="WriteToFile">
        <WriteLinesToFile
            File="@(MyTextFile)"
            Lines="@(MyItems)"
            Overwrite="true"
            Encoding="Unicode"/>
    </Target>

</Project>
```

在此範例中，我們使用內嵌新行字元的屬性來撰寫多行文字檔案。 如果 `Lines` 中的項目內嵌新行字元，則輸出檔案中將會包含新行。 如此一來，就可以參考多行屬性。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <Target Name="WriteLaunchers" AfterTargets="CopyFilesToOutputDirectory">
      <PropertyGroup>
        <LauncherCmd>
@ECHO OFF
dotnet %~dp0$(AssemblyName).dll %*
        </LauncherCmd>
      </PropertyGroup>

      <WriteLinesToFile
        File="$(OutputPath)$(AssemblyName).cmd"
        Overwrite="true"
        Lines="$(LauncherCmd)" />
  </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [任務引用](../msbuild/msbuild-task-reference.md)
