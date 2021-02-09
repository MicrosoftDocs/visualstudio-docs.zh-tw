---
title: 目標批次處理中的項目中繼資料 | Microsoft Docs
description: 瞭解 MSBuild 如何使用目標批次處理中的專案中繼資料，對組建目標的輸入和輸出執行相依性分析。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d3389d24ded805c7b1f8bbb8d31daef0cbef1a5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913892"
---
# <a name="item-metadata-in-target-batching"></a>目標批次處理中的項目中繼資料

MSBuild 可以對組建目標的輸入和輸出執行相依性分析。 如果判斷目標的輸入或輸出已是最新，即會略過目標繼續建置。 `Target` 項目會使用 `Inputs` 和 `Outputs` 屬性，來指定要在相依性分析期間檢查的項目。

如果目標包含使用批次處理專案做為輸入或輸出的工作， `Target` 則目標的專案應該在其或屬性中使用批次處理， `Inputs` `Outputs` 讓 MSBuild 略過最新的專案批次。

## <a name="batch-targets"></a>批次目標

下列範例包含名為 `Res` 的項目清單，並根據 `Culture` 項目中繼資料分成兩個批次。 這兩個批次均會傳入 `AL` 工作，以建立每個批次的輸出組件。 藉由在專案的屬性上使用批次處理 `Outputs` `Target` ，MSBuild 可以在執行目標之前，判斷每個個別批次是否為最新狀態。 如果沒有使用目標批次處理，在每次執行目標時，都會由工作來執行這兩個項目批次。

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

- [如何：以累加方式建立](../msbuild/how-to-build-incrementally.md)
- [批次處理](../msbuild/msbuild-batching.md)
- [MSBuild)  (目標元素 ](../msbuild/target-element-msbuild.md)
- [工作批次處理中的項目中繼資料](../msbuild/item-metadata-in-task-batching.md)
