---
title: Target 項目 (MSBuild) | Microsoft Docs
description: 深入瞭解 MSBuild 目標元素，其中包含一組可讓 MSBuild 依序執行的工作。
ms.custom: SEO-VS-2020
ms.date: 06/13/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Target
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Target element [MSBuild]
- <Target> element [MSBuild]
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 231ffd185eaf06fb91a709631082c2b68db372ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966119"
---
# <a name="target-element-msbuild"></a>Target 元素 (MSBuild)

包含一組要循序執行的 MSBuild 工作。

 \<Project> \<Target>

## <a name="syntax"></a>Syntax

```xml
<Target Name="Target Name"
        Inputs="Inputs"
        Outputs="Outputs"
        Returns="Returns"
        KeepDuplicateOutputs="true/false"
        BeforeTargets="Targets"
        AfterTargets="Targets"
        DependsOnTargets="DependentTarget"
        Condition="'String A' == 'String B'"
        Label="Label">
    <Task>... </Task>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <OnError... />
</Target>
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Name`|必要屬性。<br /><br /> 目標的名稱。 目標名稱可包含任何字元，但除外 `$@()%*?.` 。|
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如果條件評估為 `false`，目標將不會執行目標或 `DependsOnTargets` 屬性中所設定之任何目標的主體。 如需條件的詳細資訊，請參閱 [條件](../msbuild/msbuild-conditions.md)。|
|`Inputs`|選擇性屬性。<br /><br /> 構成此目標輸入的檔案。 若有多個檔案，則會以分號分隔。 檔案的時間戳記將會與 `Outputs` 中的檔案時間戳記相比較，以判斷 `Target` 是否為最新狀態。 如需詳細資訊，請參閱[累加建置](../msbuild/incremental-builds.md)、[如何：累加建置](../msbuild/how-to-build-incrementally.md)及[轉換](../msbuild/msbuild-transforms.md)。|
|`Outputs`|選擇性屬性。<br /><br /> 構成此目標輸出的檔案。 若有多個檔案，則會以分號分隔。 檔案的時間戳記將會與 `Inputs` 中的檔案時間戳記相比較，以判斷 `Target` 是否為最新狀態。 如需詳細資訊，請參閱[累加建置](../msbuild/incremental-builds.md)、[如何：累加建置](../msbuild/how-to-build-incrementally.md)及[轉換](../msbuild/msbuild-transforms.md)。|
|`Returns`|選擇性屬性。<br /><br /> 將可供叫用此目標的工作 (例如 MSBuild 工作) 使用的項目組。 若有多個目標，則會以分號分隔。 如果檔案中的目標沒有 `Returns` 屬性，即會基於此目的改用 Outputs 屬性。|
|`KeepDuplicateOutputs`|選擇性的 Boolean 屬性。<br /><br /> 如果是 `true`，即會記錄多個對目標 Returns 中相同項目的參考。  根據預設，此屬性為 `false`。|
|`BeforeTargets`|選擇性屬性。<br /><br /> 以分號分隔的目標名稱清單。  指定時，表示此目標應該在指定的一或多個目標之前執行。 這讓專案作者能夠擴充現有的目標組，而不需直接修改它們。 如需詳細資訊，請參閱[目標建置順序](../msbuild/target-build-order.md)。|
|`AfterTargets`|選擇性屬性。<br /><br /> 以分號分隔的目標名稱清單。 指定時，表示此目標應該在指定的一或多個目標之後執行。 這讓專案作者能夠擴充現有的目標組，而不需直接修改它們。 如需詳細資訊，請參閱[目標建置順序](../msbuild/target-build-order.md)。|
|`DependsOnTargets`|選擇性屬性。<br /><br /> 必須在此目標執行之前，或發生最上層相依性分析之前執行的目標。 若有多個目標，則會以分號分隔。|
|`Label`|選擇性屬性。<br /><br /> 用來識別或排序系統和使用者項目的識別項。|

### <a name="child-elements"></a>子元素

| 元素 | 描述 |
| - | - |
| [Task](../msbuild/task-element-msbuild.md) | 建立並執行 MSBuild 工作的實例。 目標中可能有零或多個工作。 |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | 包含一組使用者定義的 `Property` 項目。 從 .NET Framework 3.5 開始，`Target` 項目可以包含 `PropertyGroup` 項目。 |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | 包含一組使用者定義的 `Item` 項目。 從 .NET Framework 3.5 開始，`Target` 項目可以包含 `ItemGroup` 項目。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。 |
| [OnError](../msbuild/onerror-element-msbuild.md) | 如果 `ContinueOnError` 屬性是失敗工作的 ErrorAndStop (或 `false`)，則會導致執行一或多個目標。 目標中可能有零或多個 `OnError` 項目。 如果有 `OnError` 項目存在，則它們必須是 `Target` 項目中的最後一個項目。<br /><br /> 如需 `ContinueOnError` 屬性的相關資訊，請參閱 [Task 元素 (MSBuild)](../msbuild/task-element-msbuild.md)。 |

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| - | - |
| [專案](../msbuild/project-element-msbuild.md) | MSBuild 專案檔的必要根項目。 |

## <a name="remarks"></a>備註

 在執行階段指定要執行的第一個目標。 目標可以相依於其他目標。 例如，適用於部署的目標相依於適用於編譯的目標。 MSBuild 引擎會依照這些相依性在屬性中的出現順序來執行相依性 `DependsOnTargets` ，從左至右。 如需詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)。

 MSBuild 需相依於匯入順序，且具特定 `Name` 屬性之目標的最後一個定義將會是系統所使用的定義。

 目標在建置期間只會執行一次，即使有多個目標相依於該目標也一樣。

 若因目標的 `Condition` 屬性評估為 `false` 而略過該目標，如果稍後在組建中叫用該目標且其 `Condition` 屬性在該時點評估為 `true`，則仍會執行該目標。

 在 MSBuild 4 之前，`Target` 會傳回 `Outputs` 屬性中所指定的任何項目。  若要這樣做，MSBuild 必須記錄這些項目，以防組建中後續的工作需要用到它們。 由於沒有任何方法可指出哪些目標具有呼叫端所要求的輸出，因此，MSBuild 會在所有叫用的 `Target` 上累積來自所有 `Outputs` 的所有項目。 這會導致含有大量輸出項目的組建問題範圍擴大。

 如果使用者在專案中的任何 `Target` 項目上指定 `Returns`，則只有具 `Returns` 屬性的 `Target` 會記錄這些項目。

 `Target` 可能同時包含 `Outputs` 屬性和 `Returns` 屬性。  `Outputs` 會與 `Inputs` 搭配使用，以判斷目標是否為最新狀態。 如果有 `Returns`，即會覆寫 `Outputs` 的值，來判斷要將哪些項目傳回給呼叫端。  如果 `Returns` 不存在，則會將 `Outputs` 開放給呼叫端使用，但稍早所述的案例除外。

 在 MSBuild 4 之前，任何時候，只要 `Target` 在其 `Outputs` 中包含多個對相同項目的參考，就會記錄這些重複項目。 若含有大量輸出和許多專案相依性的組建數量非常多，這會造成大量記憶體的浪費，因為重複項目不具任何用途。 將 `KeepDuplicateOutputs` 屬性設為 `true` 時，就會記錄這些重複項目。

## <a name="example"></a>範例

 下列程式碼範例示範執行 `Csc` 工作的 `Target` 項目。

```xml
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">
    <Csc Sources="@(CSFile)"
          TargetType="library"
          Resources="@(CompiledResources)"
          EmitDebugInformation="$(includeDebugInformation)"
          References="@(Reference)"
          DebugType="$(debuggingType)" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
    </Csc>
</Target>
```

## <a name="see-also"></a>另請參閱

- [目標](../msbuild/msbuild-targets.md)
- [專案檔案架構參考](../msbuild/msbuild-project-file-schema-reference.md)
