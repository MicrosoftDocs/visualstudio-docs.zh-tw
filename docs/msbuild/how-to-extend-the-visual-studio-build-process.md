---
title: 延伸建置流程
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6a465a752282f4a0dc00f3fb294ade4169bb19b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093942"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>如何：擴充 Visual Studio 建置處理序

Visual Studio 生成過程由一系列導入到專案檔案中的 MSBuild *.target*檔定義。 其中一個導入的檔 *，Microsoft.Common.target，* 可以擴展，以允許您在生成過程中的多個點運行自訂任務。 本文介紹了可用於擴展視覺化工作室生成過程的兩種方法：

- 重寫在共同目標 *（Microsoft.Common.target*或它導入的檔）中定義的特定預定義目標。

- 重寫在常見目標中定義的"DependsOn"屬性。

## <a name="override-predefined-targets"></a>覆寫預先定義的目標

公共目標包含一組預定義的空目標，在生成過程中的某些主要目標之前和之後調用。 例如，MSBuild`BeforeBuild`在主要目標`CoreBuild`和目標之前調用`AfterBuild``CoreBuild`目標，在目標之後調用目標。 預設情況下，公共目標中的空目標不執行任何操作，但您可以通過在導入公共目標的專案檔案中定義所需的目標來覆蓋其預設行為。 通過重寫預定義的目標，可以使用 MSBuild 任務來讓您對生成過程進行更多控制。
公共目標包含一組預定義的空目標，在生成過程中的某些主要目標之前和之後調用。 例如，MSBuild`BeforeBuild`在主要目標`CoreBuild`和目標之前調用`AfterBuild``CoreBuild`目標，在目標之後調用目標。 預設情況下，公共目標中的空目標不執行任何操作，但您可以通過在導入公共目標的專案檔案中定義所需的目標來覆蓋其預設行為。 通過重寫預定義的目標，可以使用 MSBuild 任務來讓您對生成過程進行更多控制。

> [!NOTE]
> SDK 樣式專案在*專案檔案的最後一行之後*具有隱含的目標導入。 這意味著，除非手動指定導入，否則無法覆蓋預設目標[：使用 MSBuild 專案 SDK](how-to-use-project-sdk.md)。

#### <a name="to-override-a-predefined-target"></a>覆寫預先定義的目標

1. 在要覆蓋的常見目標中標識預定義的目標。 如需您可安全覆寫之目標的完整清單，請參閱下表。

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

下表顯示了可以安全覆蓋的常見目標中的所有目標。

|目標名稱|描述|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|在核心編譯完成之前或之後，會執行插入至其中一個目標的工作。 大部分的自訂是在這兩個目標的其中一個中完成。|
|`BeforeBuild`, `AfterBuild`|在組建的任何其他項目之前或之後，將會執行其中一個目標中插入的工作。 **注意︰**`BeforeBuild` 和 `AfterBuild` 目標定義於大部分專案檔結尾的註解中，可讓您輕鬆地將建置前和建置後事件新增至專案檔。|
|`BeforeRebuild`, `AfterRebuild`|在叫用核心重建功能之前或之後，執行插入至其中一個目標的工作。 *Microsoft.Common.target*中的目標執行順序是： `BeforeRebuild`，，`Build``AfterRebuild``Clean`然後。|
|`BeforeClean`, `AfterClean`|在叫用核心清除功能之前或之後，執行插入至其中一個目標的工作。|
|`BeforePublish`, `AfterPublish`|在叫用核心發行功能之前或之後，執行插入至其中一個目標的工作。|
|`BeforeResolveReferences`, `AfterResolveReferences`|在解析組件參考之前或之後，會執行插入至其中一個目標的工作。|
|`BeforeResGen`, `AfterResGen`|在產生資源之前或之後，會執行插入至其中一個目標的工作。|

## <a name="example-aftertargets-and-beforetargets"></a>示例：目標後和目標之前

下面的示例演示如何使用 屬性`AfterTargets`添加對輸出檔案執行某些操作的自訂目標。 在這種情況下，它將輸出檔案複製到新的資料夾*自訂輸出*。  該示例還演示如何使用`CustomClean``BeforeTargets`屬性並指定自訂清理操作在`CoreClean`目標之前運行，從而使用目標清理由自訂生成操作創建的檔。

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
> 請務必使用與上一節中表中列出的預定義目標不同的名稱（例如，我們在這裡命名了自訂生成目標`CustomAfterBuild`，而不是`AfterBuild`），因為這些預定義的目標被 SDK 導入覆蓋，SDK 導入也定義了它們。 您看不到覆蓋這些目標的目的檔案的導入，但在使用引用 SDK`Sdk`的屬性方法時，該檔將隱式添加到專案檔案的末尾。

## <a name="override-dependson-properties"></a>覆寫 DependsOn 屬性

重寫預定義目標是擴展生成過程的簡便方法，但由於 MSBuild 按順序評估目標的定義，因此無法阻止導入專案的另一個專案覆蓋已有的目標重寫。 因此，例如，在匯入所有其他專案之後，專案檔中所定義的最後一個 `AfterBuild` 目標就是建置期間所使用的目標。

通過重寫在整個常見目標的屬性中使用的`DependsOnTargets`DependsOn 屬性，可以防止意外覆蓋目標。 例如，`Build` 目標包含 `"$(BuildDependsOn)"` 的 `DependsOnTargets` 屬性值。 請考慮：

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

1. 在要覆蓋的常見目標中標識預定義的 DependsOn 屬性。 如需經常覆寫的 DependsOn 屬性清單，請參閱下表。

2. 在專案檔結尾定義另一個屬性執行個體。 在新屬性中，包含原始屬性 (例如 `$(BuildDependsOn)`)。

3. 在屬性定義之前或之後，定義您的自訂目標。

4. 建置專案檔。

### <a name="commonly-overridden-dependson-properties"></a>經常覆寫的 DependsOn 屬性

|屬性名稱|描述|
|-------------------|-----------------|
|`BuildDependsOn`|如果您想要在整個建置處理序之前或之後插入自訂目標，這是要覆寫的屬性。|
|`CleanDependsOn`|如果您想要清除自訂建置處理序的輸出，這是要覆寫的屬性。|
|`CompileDependsOn`|如果您想要在編譯步驟之前或之後插入自訂處理序，這是要覆寫的屬性。|

## <a name="example-builddependson-and-cleandependson"></a>示例：構建"構建"和"清潔"功能

下面的示例與`BeforeTargets`和`AfterTargets`示例類似，但演示如何實現類似的功能。 它`BuildDependsOn`通過使用 添加自己的任務來擴展生成，該`CustomAfterBuild`任務在生成後複製輸出檔案，並且還使用`CustomClean``CleanDependsOn`添加相應的任務。  

在此示例中，這是一個 SDK 樣式的專案。 如本文前面有關 SDK 樣式專案的注釋中所述，您必須使用手動導入方法，而不是 Visual Studio`Sdk`生成專案檔案時使用的屬性。

```xml
<Project>
<Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>

<Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />

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
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

元素的順序很重要。 和`BuildDependsOn``CleanDependsOn`元素必須在導入標準 SDK 目的檔案後顯示。

## <a name="see-also"></a>另請參閱

- [視覺化工作室集成](../msbuild/visual-studio-integration-msbuild.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [.目的檔案](../msbuild/msbuild-dot-targets-files.md)
