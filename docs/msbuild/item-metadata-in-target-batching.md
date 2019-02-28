---
title: 目標批次處理中的項目中繼資料 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff9aa4cdc2e3a406b21aeccf5538bcbfdd6b4249
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606312"
---
# <a name="item-metadata-in-target-batching"></a>目標批次處理中的項目中繼資料
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 可針對建置目標的輸入和輸出執行相依性分析作業。 如果判斷目標的輸入或輸出已是最新，即會略過目標繼續建置。 `Target` 項目會使用 `Inputs` 和 `Outputs` 屬性，來指定要在相依性分析期間檢查的項目。

如果目標包含的工作會將批次項目作為輸入或輸出，則目標的 `Target` 項目應該在其 `Inputs` 或 `Outputs` 屬性中使用批次處理，以讓 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 略過已是最新的項目批次。

## <a name="batch-targets"></a>批次目標
下列範例包含名為 `Res` 的項目清單，並根據 `Culture` 項目中繼資料分成兩個批次。 這兩個批次均會傳入 `AL` 工作，以建立每個批次的輸出組件。 在 `Target` 項目的 `Outputs` 屬性上使用批次處理時，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 可以先判斷每個個別批次是否為最新狀態，再執行目標。 如果沒有使用目標批次處理，在每次執行目標時，都會由工作來執行這兩個項目批次。

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
- [如何：以累加方式建置](../msbuild/how-to-build-incrementally.md)
- [批次處理](../msbuild/msbuild-batching.md)
- [Target 項目 (MSBuild)](../msbuild/target-element-msbuild.md)
- [工作批次處理中的項目中繼資料](../msbuild/item-metadata-in-task-batching.md)
