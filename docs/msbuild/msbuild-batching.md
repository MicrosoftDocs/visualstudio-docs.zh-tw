---
title: MSBuild 批次處理 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78aeef8ea651aac1fe2a780207474399f4bbcf09
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633430"
---
# <a name="msbuild-batching"></a>MSBuild 批次處理

MSBuild 能夠根據專案中繼資料，將專案清單分割成不同的類別或批次，並使用每個批次執行一次目標或工作。

## <a name="task-batching"></a>工作批次處理

工作批次處理可讓您將項目清單分割成不同的批次，並分別將各批次傳遞給工作，以簡化專案檔案。 這表示即使工作可能要執行若干次，專案檔也只需要宣告一次工作和其屬性。

您可以使用其中一個工作屬性中的%\<ItemMetaDataName >）標記法，指定要讓 MSBuild 以工作執行批次處理。 下列範例會根據 `Example` 項目中繼資料值，將 `Color` 項目清單分割成批次，並將每個批次個別傳遞給 `MyTask` 工作。

> [!NOTE]
> 如果您不需參考工作屬性中其他位置的項目清單，或中繼資料名稱可能模稜兩可，您可以使用 %(\<ItemCollection.ItemMetaDataName>) 標記法，來完整限定要用於批次處理的項目中繼資料值。

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

MSBuild 會在執行目標之前檢查目標的輸入和輸出是否為最新狀態。 如果輸入和輸出都是最新的，則會略過目標。 如果目標內的工作使用批次處理，MSBuild 必須判斷每個專案批次的輸入和輸出是否為最新狀態。 否則，每次叫用目標時均會執行。

下列範例示範包含 `Target` 屬性與 %(`Outputs`ItemMetaDataName>) 標記法的 \< 項目。 MSBuild 會根據 `Color` 專案中繼資料，將 `Example` 專案清單分割成批次，並分析每個批次輸出檔案的時間戳記。 如果批次的輸出不是最新狀態，則會執行目標。 否則，會略過目標。

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

## <a name="property-functions-using-metadata"></a>使用中繼資料的屬性函式

批次處理可由包含中繼資料的屬性函式來控制。 例如：

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

會使用 <xref:System.IO.Path.Combine%2A> 來結合根資料夾路徑和編譯項目路徑。

屬性函式可能不會出現在中繼資料值內。 例如：

`%(Compile.FullPath.Substring(0,3))`

不允許。

如需屬性函式的詳細資訊，請參閱[屬性函式](../msbuild/property-functions.md)。

## <a name="see-also"></a>另請參閱

- [ItemMetadata 項目 (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [進階概念](../msbuild/msbuild-advanced-concepts.md)
