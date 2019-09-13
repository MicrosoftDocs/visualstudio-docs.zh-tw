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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba701d123e739bc2dfa24ff798aef5338c51f532
ms.sourcegitcommit: b60a00ac3165364ee0e53f7f6faef8e9fe59ec4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913174"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>作法：延伸 Visual Studio 建置流程
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 建置處理序是由匯入至您專案檔的一系列 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .targets 檔案所定義。 可以擴充其中一個已匯入的檔案 (Microsoft.Common.targets)，以讓您在建置處理序的數個點執行自訂工作。 本文說明您可以使用兩種方法來擴充 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 建置處理序：

- 覆寫一般目標中定義的特定預先定義目標（*Microsoft common .targets*或其匯入的檔案）。

- 覆寫在一般目標中定義的 "DependsOn" 屬性。

## <a name="override-predefined-targets"></a>覆寫預先定義的目標
一般目標包含一組預先定義的空目標，可在組建程式中的某些主要目標之前和之後呼叫。 例如，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 在主要 `CoreBuild` 目標之前呼叫 `BeforeBuild` 目標，而在 `CoreBuild` 目標之後呼叫 `AfterBuild` 目標。 根據預設，一般目標中的空白目標不會執行任何動作，但您可以在匯入通用目標的專案檔中定義想要的目標，以覆寫其預設行為。 覆寫預先定義的目標，即可使用 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工作，更充分地控制建置處理序。

> [!NOTE]
> SDK 樣式專案會在*專案檔案的最後一行之後*，隱含匯入目標。 這表示您無法覆寫預設目標，除非您以手動[方式指定匯入，如如何：使用 MSBuild 專案 Sdk](how-to-use-project-sdk.md)。

#### <a name="to-override-a-predefined-target"></a>覆寫預先定義的目標

1. 識別您想要覆寫之一般目標中的預先定義目標。 如需您可安全覆寫之目標的完整清單，請參閱下表。

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
|`BeforeCompile`、 `AfterCompile`|在核心編譯完成之前或之後，會執行插入至其中一個目標的工作。 大部分的自訂是在這兩個目標的其中一個中完成。|
|`BeforeBuild`、 `AfterBuild`|在組建的任何其他項目之前或之後，將會執行其中一個目標中插入的工作。 **注意：** `BeforeBuild` 和 `AfterBuild` 目標已定義於大部分專案檔結尾的註解中，可讓您輕鬆地將建置前和建置後事件新增至專案檔。|
|`BeforeRebuild`、 `AfterRebuild`|在叫用核心重建功能之前或之後，執行插入至其中一個目標的工作。 *Microsoft.Common.targets* 中的目標執行順序是：`BeforeRebuild`、`Clean`、`Build` 和 `AfterRebuild`。|
|`BeforeClean`、 `AfterClean`|在叫用核心清除功能之前或之後，執行插入至其中一個目標的工作。|
|`BeforePublish`、 `AfterPublish`|在叫用核心發行功能之前或之後，執行插入至其中一個目標的工作。|
|`BeforeResolveReferences`、 `AfterResolveReferences`|在解析組件參考之前或之後，會執行插入至其中一個目標的工作。|
|`BeforeResGen`、 `AfterResGen`|在產生資源之前或之後，會執行插入至其中一個目標的工作。|

## <a name="override-dependson-properties"></a>覆寫 DependsOn 屬性
覆寫預先定義的目標是擴充建置處理序的簡單方法，但因為 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 會循序評估目標的定義，所以沒有任何方法可防止另一個匯入您專案的專案覆寫您已覆寫的目標。 因此，例如，在匯入所有其他專案之後，專案檔中所定義的最後一個 `AfterBuild` 目標就是建置期間所使用的目標。

您可以覆寫整個一般目標的屬性中`DependsOnTargets`所使用的 DependsOn 屬性，以防止非預期的目標覆寫。 例如，`Build` 目標包含 `"$(BuildDependsOn)"` 的 `DependsOnTargets` 屬性值。 請考慮：

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

1. 識別您想要覆寫之一般目標中的預先定義 DependsOn 屬性。 如需經常覆寫的 DependsOn 屬性清單，請參閱下表。

2. 在專案檔結尾定義另一個屬性執行個體。 在新屬性中，包含原始屬性 (例如 `$(BuildDependsOn)`)。

3. 在屬性定義之前或之後，定義您的自訂目標。

4. 建置專案檔。

### <a name="commonly-overridden-dependson-properties"></a>經常覆寫的 DependsOn 屬性

|屬性名稱|描述|
|-------------------|-----------------|
|`BuildDependsOn`|如果您想要在整個建置處理序之前或之後插入自訂目標，這是要覆寫的屬性。|
|`CleanDependsOn`|如果您想要清除自訂建置處理序的輸出，這是要覆寫的屬性。|
|`CompileDependsOn`|如果您想要在編譯步驟之前或之後插入自訂處理序，這是要覆寫的屬性。|

## <a name="see-also"></a>另請參閱
- [Visual Studio 整合](../msbuild/visual-studio-integration-msbuild.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [.targets 檔案](../msbuild/msbuild-dot-targets-files.md)
