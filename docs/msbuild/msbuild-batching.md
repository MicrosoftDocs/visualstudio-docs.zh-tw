---
title: MSBuild 批次處理 | Microsoft Docs
description: 瞭解 MSBuild 如何根據專案中繼資料，將專案清單分割成不同的類別或批次，並使用每個批次一次執行一個目標或工作。
ms.custom: SEO-VS-2020
ms.date: 06/09/2020
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d14a979a166f7378c288453530b46b8ec6c98828
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919207"
---
# <a name="msbuild-batching"></a>MSBuild 批次處理

MSBuild 會根據專案中繼資料，將專案清單分割成不同的類別或批次，並使用每個批次一次執行一個目標或工作。

## <a name="task-batching"></a>工作批次處理

工作批次處理可讓您將項目清單分割成不同的批次，並分別將各批次傳遞給工作，以簡化專案檔案。 這表示即使工作可能要執行若干次，專案檔也只需要宣告一次工作和其屬性。

您可以使用 `%(ItemMetaDataName)` 其中一個工作屬性中的標記法，指定要讓 MSBuild 以工作執行批次處理。 下列範例會根據 `Color` 項目中繼資料值，將 `Example` 項目清單分割成批次，並將每個批次個別傳遞給 `MyTask` 工作。

> [!NOTE]
> 如果您沒有在工作屬性中的其他位置參考專案清單，或中繼資料名稱可能不明確，您可以使用% ( # B0 ItemCollection. >itemmetadataname>) 標記法來完整限定要用於批次處理的專案中繼資料值。

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

如需更具體的批次處理範例，請參閱[工作批次處理中的項目中繼資料](../msbuild/item-metadata-in-task-batching.md)。

## <a name="target-batching"></a>目標批次處理

MSBuild 會在執行目標之前檢查目標的輸入和輸出是否為最新狀態。 如果輸入和輸出都是最新的，則會略過目標。 如果目標內的工作使用批次處理，MSBuild 必須判斷每個專案批次的輸入和輸出是否為最新狀態。 否則，就會在每次點擊時執行目標。

下列範例顯示的 `Target` 元素包含 `Outputs` 具有 `%(ItemMetadataName)` 標記法的屬性。 MSBuild 會 `Example` 根據專案中繼資料，將專案清單分割成批次 `Color` ，並分析每個批次輸出檔案的時間戳記。 如果批次的輸出不是最新狀態，則會執行目標。 否則，會略過目標。

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask"
        Inputs="@(Example)"
        Outputs="%(Color)\MyFile.txt">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

如需目標批次處理的其他範例，請參閱[目標批次處理中的項目中繼資料](../msbuild/item-metadata-in-target-batching.md)。

## <a name="item-and-property-mutations"></a>專案和屬性突變

本節說明如何在使用目標批次處理或工作批次處理時瞭解變更屬性和/或專案中繼資料的效果。

因為目標批次處理和工作批次處理是兩個不同的 MSBuild 作業，所以請務必瞭解 MSBuild 在每個案例中所使用的批次處理形式。 當批次語法 `%(ItemMetadataName)` 出現在目標的工作中，但不在目標的屬性中時，MSBuild 會使用工作批次處理。 指定目標批次處理的唯一方法，是在目標屬性上使用批次處理語法，通常是 `Outputs` 屬性。

使用目標批次處理和工作批次處理時，可以將批次視為獨立執行。 所有批次都是以相同的屬性和專案中繼資料值的初始狀態複本開始。 在批次執行期間，不會對其他批次顯示任何屬性值突變。 請考慮下列範例：

```xml
  <ItemGroup>
    <Thing Include="2" Color="blue" />
    <Thing Include="1" Color="red" />
  </ItemGroup>

  <Target Name="DemoIndependentBatches">
    <ItemGroup>
      <Thing Condition=" '%(Color)' == 'blue' ">
        <Color>red</Color>
        <NeededColorChange>true</NeededColorChange>
      </Thing>
    </ItemGroup>
    <Message Importance="high"
             Text="Things: @(Thing->'%(Identity) is %(Color); needed change=%(NeededColorChange)')"/>
  </Target>
```

輸出如下：

```output
Target DemoIndependentBatches:
  Things: 2 is red; needed change=true;1 is red; needed change=
```

`ItemGroup`目標中的是隱含的工作，而且 `%(Color)` 在 `Condition` 屬性中，會執行工作批次處理。 有兩個批次：一個用於紅色，另一個用於藍色。 只有當 `%(NeededColorChange)` `%(Color)` 中繼資料為藍色時，才會設定屬性，而且此設定只會影響執行藍色批次時符合條件的個別專案。 工作 `Message` 的 `Text` 屬性不會觸發批次處理（儘管 `%(ItemMetadataName)` 語法），因為它是在專案轉換內使用。

批次會獨立執行，但不會平行執行。 當您存取批次執行中變更的中繼資料值時，這會有所差異。 如果您根據批次執行中的某些中繼資料來設定屬性，此屬性會採用 *最後一個* 設定的值：

```xml
   <PropertyGroup>
       <SomeProperty>%(SomeItem.MetadataValue)</SomeProperty>
   </PropertyGroup>
```

在批次執行之後，屬性會保留的最終值 `%(MetadataValue)` 。

雖然批次會獨立執行，但請務必考慮目標批次處理和工作批次處理之間的差異，並瞭解何種類型適用于您的情況。 請考慮下列範例，以進一步瞭解這項差異的重要性。

工作可以是隱含的，而不是明確的，這可能會在工作批次處理發生隱含的工作時造成混淆。 當 `PropertyGroup` 或 `ItemGroup` 元素出現在中時 `Target` ，群組中的每個屬性宣告都會隱含地處理，就像個別的 [CreateProperty](createproperty-task.md) 或 [CreateItem](createitem-task.md) 工作一樣。 這表示當目標批次處理時，其行為會不同，而不會批次處理目標 (也就是當它缺少 `%(ItemMetadataName)` 屬性) 中的語法時 `Outputs` 。 當目標為批次時，會 `ItemGroup` 針對每個目標執行一次，但是當目標未批次處理時， `CreateItem` 會使用工作批次處理來批次處理或工作的隱含對等專案， `CreateProperty` 因此目標只會執行一次，而群組中的每個專案或屬性會使用工作批次處理個別進行批次處理。

下列範例說明在中繼資料進行變化的情況下，目標批次處理與工作批次處理的比較。 假設您的資料夾 A 和 B 有一些檔案：

```
A\1.stub
B\2.stub
B\3.stub
```

現在看看這兩個類似專案的輸出。

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build" Outputs="%(StubDirs.Identity)">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

輸出如下：

```output
Test1:
  >> A\ 'A\' 'A'
Test1:
  >> B\ 'B\' 'B'
```

現在，移除 `Outputs` 指定目標批次處理的屬性。

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

輸出如下：

```output
Test1:
  >> A\ 'B\' 'B'
  >> B\ 'B\' 'B'
```

請注意，標題 `Test1` 只會列印一次，但在先前的範例中，它會列印兩次。 這表示不會批次處理目標。  因此，輸出 confusingly 不同。

原因是，當使用目標批次處理時，每個目標批次都會使用自己的所有屬性和專案的獨立複本來執行目標中的所有專案，但當您省略 `Outputs` 屬性時，屬性群組中的個別行會被視為相異、可能批次處理的工作。 在此情況下，工作 `ComponentDir` 會 (使用語法) 來批次處理，如此一來，程式程式碼的每 `%(ItemMetadataName)` `ComponentName` 個批次 `ComponentDir` 都已完成，而第二個則執行判斷值（如第二行所示）。

## <a name="property-functions-using-metadata"></a>使用中繼資料的屬性函式

批次處理可由包含中繼資料的屬性函式來控制。 例如，

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

會使用 <xref:System.IO.Path.Combine%2A> 來結合根資料夾路徑和編譯項目路徑。

屬性函式可能不會出現在中繼資料值內。 例如，

`%(Compile.FullPath.Substring(0,3))`

不允許。

如需屬性函式的詳細資訊，請參閱[屬性函式](../msbuild/property-functions.md)。

## <a name="see-also"></a>另請參閱

- [ItemMetadata 項目 (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [進階概念](../msbuild/msbuild-advanced-concepts.md)
