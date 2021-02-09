---
title: 參考專案檔的名稱或位置
description: 瞭解如何使用 MSBuild 保留屬性來參考專案檔名稱或位置，而不需要建立您自己的屬性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c6527a4f54abf147d54e73c8f887b57b70ff4243
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914188"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>如何：參考專案檔的名稱或位置

您可以在專案檔中使用專案的名稱或位置，而不需建立自己的屬性。 MSBuild 會提供保留的屬性，這些屬性會參考專案檔名稱以及與專案相關的其他屬性。 如需保留屬性的詳細資訊，請參閱 [MSBuild 保留和已知屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)。

## <a name="use-the-project-properties"></a>使用專案屬性

 MSBuild 提供一些保留的屬性，您可以在專案檔中使用這些屬性，而不需要每次定義它們。 例如，保留的屬性 `MSBuildProjectName` 提供專案檔名的參考。 保留的屬性 `MSBuildProjectDirectory` 提供專案檔案位置的參考。

#### <a name="to-use-the-project-properties"></a>使用專案屬性

- 使用 $() 標記法來參考專案檔中的屬性，就像您使用其他屬性一樣。 例如：

  ```xml
  <CSC Sources = "@(CSFile)"
      OutputAssembly = "$(MSBuildProjectName).exe"/>
  </CSC>
  ```

  使用保留屬性的一個優點是，會自動併入對專案檔名所做的任何變更。 當您下一次建置專案時，輸出檔將具備新名稱，而您不需採取任何進一步動作。

  如需在檔案或專案參考中使用特殊字元的詳細資訊，請參閱 [MSBuild 特殊字元](../msbuild/msbuild-special-characters.md)。

> [!NOTE]
> 您無法在專案檔中重新定義保留的屬性。

## <a name="example-1"></a>範例 1

 下列範例專案檔會參考專案名稱做為保留的屬性，來指定輸出的名稱。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    DefaultTargets = "Compile">

    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
     </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using
        input files of type CSFile -->
        <CSC Sources = "@(CSFile)"
            OutputAssembly = "$(MSBuildProjectName).exe" >
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the project -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example-2"></a>範例 2

 下列範例專案檔使用 `MSBuildProjectDirectory` 保留屬性，在專案檔案位置中建立檔案的完整路徑。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Build the path to a file in the root of the project -->
    <PropertyGroup>
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>
</Project>
```

此範例會使用 [Property 函數](property-functions.md) 語法來呼叫靜態 .NET Framework 方法 <xref:System.IO.Path.Combine*?displayProperty=fullName> 。

## <a name="see-also"></a>另請參閱

- [MSBuild](../msbuild/msbuild.md)
- [MSBuild 保留和已知屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)
