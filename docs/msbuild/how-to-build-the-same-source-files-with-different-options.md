---
title: 使用不同選項來建置相同的來源檔案
description: 瞭解如何建立不同的 MSBuild 組建設定，以使用不同的選項來建立相同的原始檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bd9d77e32f9c287ac2dfcf3905fe9335e119a3a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914488"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>如何：使用不同選項來建置相同的原始程式檔

當您建置專案時，經常會以不同的組建選項編譯相同的元件。 例如，您可以建立含有符號資訊的偵錯組建，或是不含符號資訊但已啟用最佳化的發行組建。 或者，您可以建立要在特定平臺上執行的專案，例如 x86 或 x64。 在這些情況下，大部分的建置選項都會保持不變。只會變更某些選項來控制組建組態。 使用 MSBuild 時，您可以使用屬性和條件來建立不同的組建設定。

## <a name="use-properties-to-control-build-settings"></a>使用屬性來控制組建設定

`Property` 項目會定義要在專案檔中多次參考的變數 (例如暫存目錄的位置)，或設定要在數個組態中使用的屬性值 (例如偵錯組建和發行組建)。 如需屬性的詳細資訊，請參閱 [MSBuild 屬性](../msbuild/msbuild-properties.md)。

您可以使用屬性來變更組建的組態，而不需變更專案檔。 `Property` 項目和 `PropertyGroup` 項目的 `Condition` 屬性 (Attribute) 可讓您變更屬性 (Property) 的值。 如需 MSBuild 條件的詳細資訊，請參閱 [條件](../msbuild/msbuild-conditions.md)。

### <a name="to-set-a-group-of-properties-that-depends-on-another-property"></a>設定相依于其他屬性的屬性群組

- 以如下方式使用 `PropertyGroup` 項目中的 `Condition` 屬性：

  ```xml
  <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
      <DebugType>full</DebugType>
      <Optimize>no</Optimize>
  </PropertyGroup>
  ```

### <a name="to-define-a-property-that-depends-on-another-property"></a>若要定義相依于其他屬性的屬性

- 以如下方式使用 `Property` 項目中的 `Condition` 屬性：

  ```xml
  <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>
  ```

## <a name="specify-properties-on-the-command-line"></a>在命令列上指定屬性

一旦將您的專案檔編寫為可接受多個組態之後，您就必須能夠在每次建置專案時變更這些設定。 MSBuild 可讓您使用 **-property** 或 **-p** 參數在命令列上指定屬性，以提供這項功能。

### <a name="to-set-a-project-property-at-the-command-line"></a>在命令列中設定專案屬性

- 使用 **-property** 參數搭配屬性和屬性值。 例如：

  ```cmd
  msbuild file.proj -property:Flavor=Debug
  ```

  或

  ```cmd
  Msbuild file.proj -p:Flavor=Debug
  ```

### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>在命令列中指定多個專案屬性

- 使用 **-property** 或 **-p** 參數多次搭配屬性和屬性值，或使用一個 **-property** 或 **-p** 參數，並以分號 (; ) 來分隔多個屬性。 例如：

  ```cmd
  msbuild file.proj -p:Flavor=Debug;Platform=x86
  ```

  或

  ```cmd
  msbuild file.proj -p:Flavor=Debug -p:Platform=x86
  ```

  環境變數也會被視為屬性，並由 MSBuild 自動併入。 如需使用環境變數的詳細資訊，請參閱 [如何：在組建中使用環境變數](../msbuild/how-to-use-environment-variables-in-a-build.md)。

  命令列上指定的屬性值優先於針對專案檔中相同屬性設定的任何值，而位於專案檔中的值會優先於環境變數中的值。

  您可以在專案標記中使用 `TreatAsLocalProperty` 屬性，來變更此行為。 如果是使用該屬性列出的屬性名稱，命令列上指定的屬性值不會優先於專案檔中的值。 您可以在本主題稍後找到相關範例。

## <a name="example-1"></a>範例 1

下列程式碼範例 "Hello World" 專案包含兩個新的屬性群組，其可用於建立偵錯組建及發行組建。

若要建置此專案的偵錯版本，請輸入：

```cmd
msbuild consolehwcs1.proj -p:flavor=debug
```

若要建置此專案的零售版本，請輸入：

```cmd
msbuild consolehwcs1.proj -p:flavor=retail
```

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Sets the default flavor if an environment variable called
    Flavor is not set or specified on the command line -->
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
    </PropertyGroup>

    <!-- Define the DEBUG settings -->
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
        <DebugType>full</DebugType>
        <Optimize>no</Optimize>
    </PropertyGroup>

    <!-- Define the RETAIL settings -->
    <PropertyGroup Condition="'$(Flavor)'=='RETAIL'">
        <DebugType>pdbonly</DebugType>
        <Optimize>yes</Optimize>
    </PropertyGroup>

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldCS</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input files
        of type CSFile -->
        <CSC  Sources = "@(CSFile)"
            DebugType="$(DebugType)"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe" >

            <!-- Set the OutputAssembly attribute of the CSC
            task to the name of the executable file that is
            created -->
            <Output TaskParameter="OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example-2"></a>範例 2

下列範例示範如何使用 `TreatAsLocalProperty` 屬性。 `Color` 屬性在專案檔中的值為 `Blue`，而在命令列中的值為 `Green`。 在專案標記中使用 `TreatAsLocalProperty="Color"`，命令列屬性 (`Green`) 就不會覆寫專案檔中定義的屬性 (`Blue`)。

若要建置專案，請輸入下列命令：

```cmd
msbuild colortest.proj -t:go -property:Color=Green
```

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
ToolsVersion="4.0" TreatAsLocalProperty="Color">

    <PropertyGroup>
        <Color>Blue</Color>
    </PropertyGroup>

    <Target Name="go">
        <Message Text="Color: $(Color)" />
    </Target>
</Project>

<!--
  Output with TreatAsLocalProperty="Color" in project tag:
     Color: Blue

  Output without TreatAsLocalProperty="Color" in project tag:
     Color: Green
-->
```

## <a name="see-also"></a>另請參閱

- [MSBuild](../msbuild/msbuild.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [ (MSBuild) 的專案元素 ](../msbuild/project-element-msbuild.md)
