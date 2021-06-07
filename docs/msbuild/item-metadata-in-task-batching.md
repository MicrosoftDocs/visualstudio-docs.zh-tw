---
title: 工作批次處理中的項目中繼資料 | Microsoft Docs
description: 瞭解 MSBuild 如何使用工作批次處理中的專案中繼資料，將專案清單分割成不同的類別或批次，並使用每個批次一次執行一項工作。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1675cf43cb9632d4480265f00a377c1f5c530b51
ms.sourcegitcommit: c5f2a142ebf9f00808314f79a4508a82e6df1198
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2021
ms.locfileid: "111395354"
---
# <a name="item-metadata-in-task-batching"></a>工作批次處理中的項目中繼資料

MSBuild 能夠根據專案中繼資料，將專案清單分割成不同的類別或批次，並使用每個批次執行一次工作。 要確切了解哪個批次要傳遞哪些項目，可能會相當混亂。 本主題涵蓋下列與批次處理相關的常見案例。

- 將項目清單分割成批次

- 將數個項目清單分割成批次

- 一次批次處理一個項目

- 篩選項目清單

如需使用 MSBuild 進行批次處理的詳細資訊，請參閱 [批次處理](../msbuild/msbuild-batching.md)。

## <a name="divide-an-item-list-into-batches"></a>將項目清單分割成批次

批次處理可讓您根據項目中繼資料，將項目清單分割成不同的批次，然後將每個批次個別傳遞給工作。 這適用於建置附屬組件。

下列範例示範如何根據項目中繼資料，將項目清單分割成批次。 `ExampColl` 項目清單會根據 `Number` 項目中繼資料分割成三個批次。 `%(ExampColl.Number)`屬性中的存在會 `Text` 通知 MSBuild 應該執行批次處理。 `ExampColl` 項目清單會根據 `Number` 中繼資料分割成三個批次，而系統會將每個批次個別傳遞給工作。

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>
        <ExampColl Include="Item4">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item5">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item6">
            <Number>3</Number>
        </ExampColl>
    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Number: %(ExampColl.Number) -- Items in ExampColl: @(ExampColl)"/>
    </Target>

</Project>
```

[Message 工作](../msbuild/message-task.md)顯示下列資訊：

`Number: 1 -- Items in ExampColl: Item1;Item4`

`Number: 2 -- Items in ExampColl: Item2;Item5`

`Number: 3 -- Items in ExampColl: Item3;Item6`

## <a name="divide-several-item-lists-into-batches"></a>將數個項目清單分割成批次

MSBuild 可以根據相同的中繼資料，將多個專案清單分割成多個批次。 這可讓您輕鬆將不同的項目清單分割成批次，以建置多個組件。 例如，您可以將 *.cs* 檔案的專案清單分割成應用程式批次和元件批次，以及將資源檔的專案清單分割成應用程式批次和元件批次。 接著，您可以使用批次處理將這些項目清單傳遞給一個工作，然後建置應用程式和組件。

> [!NOTE]
> 如果要傳遞給工作的項目清單未包含任何具有所參考中繼資料的項目，系統就會將該項目清單中的每個項目都傳遞給每個批次。

下列範例顯示如何根據專案中繼資料，將多個專案清單分割成批次。 `ExampColl` 和 `ExampColl2` 項目清單會分別根據 `Number` 項目中繼資料分割成三個批次。 `%(Number)`屬性中的存在會 `Text` 通知 MSBuild 應該執行批次處理。 `ExampColl` 和 `ExampColl2` 項目清單會根據 `Number` 中繼資料分割成三個批次，而系統會將每個批次個別傳遞給工作。

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>

        <ExampColl2 Include="Item4">
            <Number>1</Number>
        </ExampColl2>
        <ExampColl2 Include="Item5">
            <Number>2</Number>
        </ExampColl2>
        <ExampColl2 Include="Item6">
            <Number>3</Number>
        </ExampColl2>

    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Number: %(Number) -- Items in ExampColl: @(ExampColl) ExampColl2: @(ExampColl2)"/>
    </Target>

</Project>
```

[Message 工作](../msbuild/message-task.md)顯示下列資訊：

`Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`

`Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`

`Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`

## <a name="batch-one-item-at-a-time"></a>一次批次處理一個項目

在於建立每個項目時指派給項目的已知項目中繼資料上，也可以執行批次處理。 這可確保集合中的每個項目都具有相同的中繼資料可用於批次處理。 `Identity`中繼資料值適用于將專案清單中的每個專案分割成不同的批次。 如需已知專案中繼資料的完整清單，請參閱 [已知的專案中繼資料](../msbuild/msbuild-well-known-item-metadata.md)。

下列範例示範如何以一次一個的方式，批次處理項目清單中的每個項目。 `ExampColl`專案清單分為六個批次，每個批次包含專案清單中的一個專案。 `%(Identity)`屬性中的存在會 `Text` 通知 MSBuild 應該執行批次處理。

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1"/>
        <ExampColl Include="Item2"/>
        <ExampColl Include="Item3"/>
        <ExampColl Include="Item4"/>
        <ExampColl Include="Item5"/>
        <ExampColl Include="Item6"/>

    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Identity: '%(Identity)' -- Items in ExampColl: @(ExampColl)"/>
    </Target>

</Project>
```

[Message 工作](../msbuild/message-task.md)顯示下列資訊：

```output
Identity: 'Item1' -- Items in ExampColl: Item1
Identity: 'Item2' -- Items in ExampColl: Item2
Identity: 'Item3' -- Items in ExampColl: Item3
Identity: 'Item4' -- Items in ExampColl: Item4
Identity: 'Item5' -- Items in ExampColl: Item5
Identity: 'Item6' -- Items in ExampColl: Item6
```

但是， `Identity` 不保證是唯一的，其值為屬性的評估最終值 `Include` 。 因此，如果 `Include` 多次使用任何屬性，它們會一起批次處理。 如下列範例所示，這項技術要求 `Include` 群組中的每個專案都必須有唯一的屬性。 為了說明這一點，請考慮下列程式碼：

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Item Include="1">
      <M>1</M>
    </Item>
    <Item Include="1">
      <M>2</M>
    </Item>
    <Item Include="2">
      <M>3</M>
    </Item>
  </ItemGroup>

  <Target Name="Batching">
    <Warning Text="@(Item->'%(Identity): %(M)')" Condition=" '%(Identity)' != '' "/>
  </Target>
</Project>
```

輸出會顯示前兩個專案都在相同的批次中，因為 `Include` 它們的屬性相同：

```output
test.proj(15,5): warning : 1: 1;1: 2
test.proj(15,5): warning : 2: 3
```

## <a name="filter-item-lists"></a>篩選項目清單

批次處理可用來先篩除項目清單中的特定項目，再將其傳遞給工作。 例如，篩選 `Extension` 已知項目中繼資料值可讓您只在具有特定副檔名的檔案上執行工作。

下列範例示範如何根據項目中繼資料，將項目清單分割成批次，然後在將這些批次傳遞給工作時，進行篩選。 `ExampColl` 項目清單會根據 `Number` 項目中繼資料分割成三個批次。 工作的 `Condition` 屬性指定只將 `Number` 項目中繼資料值為 `2` 的批次傳遞給工作

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>
        <ExampColl Include="Item4">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item5">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item6">
            <Number>3</Number>
        </ExampColl>

    </ItemGroup>

    <Target Name="Exec">
        <Message
            Text = "Items in ExampColl: @(ExampColl)"
            Condition="'%(Number)'=='2'"/>
    </Target>

</Project>
```

[Message 工作](../msbuild/message-task.md)顯示下列資訊：

```
Items in ExampColl: Item2;Item5
```

## <a name="see-also"></a>另請參閱

- [已知的專案中繼資料](../msbuild/msbuild-well-known-item-metadata.md)
- [Item 項目 (MSBuild)](../msbuild/item-element-msbuild.md)
- [ItemMetadata 項目 (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [批次處理](../msbuild/msbuild-batching.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
