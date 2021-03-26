---
title: 延伸建置流程
description: 學習各種修改組建流程的方式，讓您可以控制和自訂專案的建立方式。
ms.custom: seodec18, SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94e5680f8e8635c969e25555463a21bba069284a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055813"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>如何：擴充 Visual Studio 建置處理序

Visual Studio 組建程式是由匯入至您專案檔的一系列 MSBuild *.targets* 檔案所定義。 您可以擴充其中一個匯入的 *檔案，以* 允許您在組建程式中的數個點執行自訂工作。 本文說明可用於擴充 Visual Studio 組建程式的兩種方法：

- 覆寫一般目標中所定義的特定預先定義目標 (*Microsoft. 一般.* 或匯入) 的檔案。

- 覆寫在一般目標中定義的 "DependsOn" 屬性。

## <a name="override-predefined-targets"></a>覆寫預先定義的目標

一般目標包含一組預先定義的空目標，可在組建程式中的部分主要目標之前和之後呼叫。 例如，MSBuild 會在 `BeforeBuild` `CoreBuild` 目標之後的主要目標和目標之前呼叫目標 `AfterBuild` `CoreBuild` 。 根據預設，一般目標中的空目標不會執行任何動作，但是您可以在匯入共同目標的專案檔中定義您想要的目標，以覆寫其預設行為。 藉由覆寫預先定義的目標，您可以使用 MSBuild 工作，讓您更充分掌控組建流程。

> [!NOTE]
> SDK 樣式專案會在 *專案檔的最後一行之後* 隱含匯入目標。 這表示除非以手動方式指定匯入，否則您無法覆寫預設目標，如 [如何：使用 MSBuild 專案 sdk](how-to-use-project-sdk.md)中所述。

#### <a name="to-override-a-predefined-target"></a>覆寫預先定義的目標

1. 識別您想要覆寫的一般目標中預先定義的目標。 如需您可安全覆寫之目標的完整清單，請參閱下表。

2. 在專案檔結尾，於 `</Project>` 標記的正前方定義目標。 例如：

    ```xml
    <Project>
        ...
        <Target Name="BeforeBuild">
            <!-- Insert tasks to run before build here -->
        </Target>
        <Target Name="AfterBuild">
            <!-- Insert tasks to run after build here -->
        </Target>
    </Project>
    ```

3. 建置專案檔。

下表顯示您可以安全覆寫之一般目標中的所有目標。

|目標名稱|描述|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|在核心編譯完成之前或之後，會執行插入至其中一個目標的工作。 大部分的自訂是在這兩個目標的其中一個中完成。|
|`BeforeBuild`, `AfterBuild`|在組建的任何其他項目之前或之後，將會執行其中一個目標中插入的工作。 **注意︰**`BeforeBuild` 和 `AfterBuild` 目標定義於大部分專案檔結尾的註解中，可讓您輕鬆地將建置前和建置後事件新增至專案檔。|
|`BeforeRebuild`, `AfterRebuild`|在叫用核心重建功能之前或之後，執行插入至其中一個目標的工作。 在 *Microsoft* 中，目標執行的順序如下： `BeforeRebuild` 、 `Clean` 、 `Build` 和 `AfterRebuild` 。|
|`BeforeClean`, `AfterClean`|在叫用核心清除功能之前或之後，執行插入至其中一個目標的工作。|
|`BeforePublish`, `AfterPublish`|在叫用核心發行功能之前或之後，執行插入至其中一個目標的工作。|
|`BeforeResolveReferences`, `AfterResolveReferences`|在解析組件參考之前或之後，會執行插入至其中一個目標的工作。|
|`BeforeResGen`, `AfterResGen`|在產生資源之前或之後，會執行插入至其中一個目標的工作。|

## <a name="example-aftertargets-and-beforetargets"></a>範例： AfterTargets 和 BeforeTargets

下列範例將示範如何使用 `AfterTargets` 屬性來新增自訂目標，以對輸出檔案執行某些動作。 在此情況下，它會將輸出檔案複製到新的資料夾 *CustomOutput*。  此範例也會示範如何使用屬性來清除自訂群組建作業所建立的檔案 `CustomClean` `BeforeTargets` ，並指定在目標之前執行自訂清除作業 `CoreClean` 。

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
     <TargetFramework>netcoreapp3.1</TargetFramework>
     <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
  </PropertyGroup>

  <Target Name="CustomAfterBuild" AfterTargets="Build">
    <ItemGroup>
      <_FilesToCopy Include="$(OutputPath)**\*"/>
    </ItemGroup>
    <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

    <Message Text="DestFiles:
        @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

    <Copy SourceFiles="@(_FilesToCopy)"
          DestinationFiles=
          "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean" BeforeTargets="CoreClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

> [!WARNING]
> 請務必使用與上一節表格中所列的預先定義目標不同的名稱 (例如，我們在這裡命名為自訂群組建目標 `CustomAfterBuild` ，而不是 `AfterBuild`) ，因為這些預先定義的目標會由 SDK 匯入（也會加以定義）覆寫。 您看不到會覆寫這些目標的目標檔案匯入，但是當您使用參考 SDK 的屬性方法時，它會隱含地加入至專案檔的結尾 `Sdk` 。

## <a name="override-dependson-properties"></a>覆寫 DependsOn 屬性

覆寫預先定義的目標是延伸組建程式的簡單方法，但因為 MSBuild 會依序評估目標的定義，所以無法防止匯入專案的另一個專案覆寫您已覆寫的目標。 因此，例如，在匯入所有其他專案之後，專案檔中所定義的最後一個 `AfterBuild` 目標就是建置期間所使用的目標。

您可以藉由覆寫整個通用目標的屬性中所使用的 DependsOn 屬性，防止非預期的目標覆寫 `DependsOnTargets` 。 例如，`Build` 目標包含 `"$(BuildDependsOn)"` 的 `DependsOnTargets` 屬性值。 考量：

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

這部分的 XML 指出必須先執行 `BuildDependsOn` 屬性中所指定的所有目標，才能執行 `Build` 目標。 `BuildDependsOn` 屬性定義為：

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

您可以在專案檔結尾宣告名為 `BuildDependsOn` 的另一個屬性，來覆寫此屬性值。 在新屬性中包含先前的 `BuildDependsOn` 屬性，即可將新目標新增至目標清單開頭和結尾。 例如：

```xml
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

匯入您專案檔的專案可以覆寫這些屬性，而不覆寫您進行的自訂。

#### <a name="to-override-a-dependson-property"></a>覆寫 DependsOn 屬性

1. 識別您想要覆寫的一般目標中預先定義的 DependsOn 屬性。 如需經常覆寫的 DependsOn 屬性清單，請參閱下表。

2. 在專案檔結尾定義另一個屬性執行個體。 在新屬性中，包含原始屬性 (例如 `$(BuildDependsOn)`)。

3. 在屬性定義之前或之後，定義您的自訂目標。

4. 建置專案檔。

### <a name="commonly-overridden-dependson-properties"></a>經常覆寫的 DependsOn 屬性

|屬性名稱|描述|
|-------------------|-----------------|
|`BuildDependsOn`|如果您想要在整個建置處理序之前或之後插入自訂目標，這是要覆寫的屬性。|
|`CleanDependsOn`|如果您想要清除自訂建置處理序的輸出，這是要覆寫的屬性。|
|`CompileDependsOn`|如果您想要在編譯步驟之前或之後插入自訂處理序，這是要覆寫的屬性。|

## <a name="example-builddependson-and-cleandependson"></a>範例： BuildDependsOn 和 CleanDependsOn

下列範例類似于 `BeforeTargets` 和 `AfterTargets` 範例，但會示範如何達成類似的功能。 它會擴充組建，方法是使用 `BuildDependsOn` 來新增您自己 `CustomAfterBuild` 的工作，以便在組建之後複製輸出檔，也會使用加入對應的工作 `CustomClean` `CleanDependsOn` 。  

在此範例中，這是 SDK 樣式專案。 如本文稍早關於 SDK 樣式專案的注意事項中所述，您必須使用手動匯入方法，而不是 `Sdk` Visual Studio 在產生專案檔時使用的屬性。

```xml
<Project>
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk"/>

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk"/>

  <PropertyGroup>
    <BuildDependsOn>
      $(BuildDependsOn);CustomAfterBuild
    </BuildDependsOn>

    <CleanDependsOn>
      $(CleanDependsOn);CustomClean
    </CleanDependsOn>

    <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
  </PropertyGroup>

  <Target Name="CustomAfterBuild">
    <ItemGroup>
      <_FilesToCopy Include="$(OutputPath)**\*"/>
    </ItemGroup>
    <Message Importance="high" Text="_FilesToCopy: @(_FilesToCopy)"/>

    <Message Text="DestFiles:
      @(_FilesToCopy-&gt;'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

    <Copy SourceFiles="@(_FilesToCopy)"
          DestinationFiles="@(_FilesToCopy-&gt;'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean">
    <Message Importance="high" Text="Inside Custom Clean"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files="@(_CustomFilesToDelete)"/>
  </Target>
</Project>
```

元素的順序很重要。 匯 `BuildDependsOn` `CleanDependsOn` 入標準 SDK 目標檔案之後必須出現和元素。

## <a name="see-also"></a>另請參閱

- [Visual Studio 整合](../msbuild/visual-studio-integration-msbuild.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [.targets 檔案](../msbuild/msbuild-dot-targets-files.md)
