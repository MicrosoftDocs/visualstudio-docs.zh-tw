---
title: 目標批次處理中的項目中繼資料 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83a5d0c9dec280633d0a39573581c083e6ddd4d8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633664"
---
# <a name="item-metadata-in-target-batching"></a>目標批次處理中的項目中繼資料

MSBuild 能夠對生成目標的輸入和輸出執行依賴項分析。 如果判斷目標的輸入或輸出已是最新，即會略過目標繼續建置。 `Target` 項目會使用 `Inputs` 和 `Outputs` 屬性，來指定要在相依性分析期間檢查的項目。

如果目標包含使用批次處理項作為輸入或輸出的任務，則目標`Target`的元素應使用其`Inputs`或`Outputs`屬性中的批次處理，以使 MSBuild 跳過已更新的批次處理。

## <a name="batch-targets"></a>批次目標

下列範例包含名為 `Res` 的項目清單，並根據 `Culture` 項目中繼資料分成兩個批次。 這兩個批次均會傳入 `AL` 工作，以建立每個批次的輸出組件。 通過使用`Outputs``Target`元素屬性的批次處理，MSBuild 可以確定每個單個批次處理在運行目標之前是否處於最新狀態。 如果沒有使用目標批次處理，在每次執行目標時，都會由工作來執行這兩個項目批次。

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Res Include="Strings.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Strings.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.jp.resources">
            <Culture>jp</Culture>
        </Res>
    </ItemGroup>

    <Target Name="Build"
        Inputs="@(Res)"
        Outputs="%(Culture)\MyApp.resources.dll">

        <AL Resources="@(Res)"
            TargetType="library"
            OutputAssembly="%(Culture)\MyApp.resources.dll">

    </Target>

</Project>
```

## <a name="see-also"></a>另請參閱

- [如何：增量生成](../msbuild/how-to-build-incrementally.md)
- [配料](../msbuild/msbuild-batching.md)
- [目標元素 （MSBuild）](../msbuild/target-element-msbuild.md)
- [任務批次處理中的項中繼資料](../msbuild/item-metadata-in-task-batching.md)
