---
title: 目標建置順序 | Microsoft Docs
description: 瞭解如何指定執行 MSBuild 目標的順序，如果某個目標的輸入取決於另一個目標的輸出。
ms.custom: SEO-VS-2020
ms.date: 05/02/2019
ms.topic: conceptual
helpviewer_keywords:
- msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 873f669890e84281f73a96fa1739d267c10e83a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966132"
---
# <a name="target-build-order"></a>目標組建順序

如果某一個目標的輸入相依於另一個目標的輸出，則必須排序目標。 您可以使用這些屬性來指定執行目標的順序：

- `InitialTargets`. 這個 `Project` 屬性會指定優先執行的目標，即使已在命令列上或 `DefaultTargets` 屬性中指定目標也一樣。

- `DefaultTargets`. `Project`如果未在命令列上明確指定目標，則此屬性會指定要執行的目標。

- `DependsOnTargets`. 這個 `Target` 屬性會指定必須在此目標執行之前執行的目標。

- `BeforeTargets` 和 `AfterTargets`。 這些 `Target` 屬性會指定此目標應該在指定的目標之前或之後執行 (MSBuild 4.0)。

目標絕對不會在建置期間執行兩次，即使組建中的後續目標相依於它也一樣。 一旦執行目標之後，它對組建而言就已功成身退了。

目標可能會有 `Condition` 屬性。 如果指定的條件評估為 `false`，則不會執行目標，且不會對組建產生任何作用。 如需條件的詳細資訊，請參閱 [條件](../msbuild/msbuild-conditions.md)。

## <a name="initial-targets"></a>初始目標

[Project](../msbuild/project-element-msbuild.md) 項目的 `InitialTargets` 屬性會指定優先執行的目標，即使已在命令列上或 `DefaultTargets` 屬性中指定目標也一樣。 初始目標通常用於錯誤檢查。

`InitialTargets` 屬性的值可以是以分號分隔且已排序的目標清單。 下列範例會指定 `Warm` 目標執行，然後 `Eject` 目標執行。

```xml
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

匯入的專案可能會有自己的 `InitialTargets` 屬性。 所有的初始目標都會彙總在一起，並依序執行。

如需詳細資訊，請參閱 [如何：指定要先建立的目標](../msbuild/how-to-specify-which-target-to-build-first.md)。

## <a name="default-targets"></a>預設目標

如果未在命令列上明確指定目標，則 [Project](../msbuild/project-element-msbuild.md) 項目的 `DefaultTargets` 屬性會指定要建置哪些目標。

`DefaultTargets` 屬性的值可以是以分號分隔且已排序的預設目標清單。 下列範例會指定 `Clean` 目標執行，然後 `Build` 目標執行。

```xml
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

您可以在命令列上使用 **-target** 參數覆寫預設目標。 下列範例會指定 `Build` 目標執行，然後 `Report` 目標執行。 當您以這種方式指定目標時，就會忽略任何預設目標。

 `msbuild -target:Build;Report`

如果未指定初始目標和預設目標，以及如果未指定任何命令列目標，MSBuild 就會先執行初始目標，接著執行預設目標。

匯入的專案可能會有自己的 `DefaultTargets` 屬性。 第一個遇到的 `DefaultTargets` 屬性會判斷將執行哪些預設目標。

如需詳細資訊，請參閱 [如何：指定要先建立的目標](../msbuild/how-to-specify-which-target-to-build-first.md)。

## <a name="first-target"></a>第一個目標

如果沒有初始目標、預設目標或命令列目標，則 MSBuild 會執行它在專案檔或任何匯入的專案檔中遇到的第一個目標。

## <a name="target-dependencies"></a>目標相依性

目標可以說明彼此間的相依性關係。 `DependsOnTargets` 屬性會指出某一個目標相依於其他目標。 例如，

```xml
<Target Name="Serve" DependsOnTargets="Chop;Cook" />
```

告知 MSBuild，`Serve` 目標相依於 `Chop` 目標和 `Cook` 目標。 MSBuild 會執行 `Chop` 目標，然後在執行 `Serve` 目標之前先執行 `Cook` 目標。

## <a name="beforetargets-and-aftertargets"></a>BeforeTargets 和 AfterTargets

在 MSBuild 4.0 中，您可以使用 `BeforeTargets` 和 `AfterTargets` 屬性來指定目標順序。

請考慮下列指令碼。

```xml
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Compile">
        <Message Text="Compiling" />
    </Target>
    <Target Name="Link">
        <Message Text="Linking" />
    </Target>
</Project>
```

若要建立中繼目標 `Optimize`，在 `Compile` 目標之後，但在 `Link` 目標之前執行，請 在 `Project` 項目中的任一處加入下列目標。

```xml
<Target Name="Optimize"
    AfterTargets="Compile" BeforeTargets="Link">
    <Message Text="Optimizing" />
</Target>
```

## <a name="determine-the-target-build-order"></a>判斷目標建置順序

MSBuild 會以如下方式判斷目標建置順序：

1. 執行 `InitialTargets` 目標。

2. 執行命令列上使用 **-target** 參數指定的目標。 如果您未在命令列上指定目標，則會執行 `DefaultTargets` 目標。 如果兩者都不存在，則會執行第一個遇到的目標。

3. 評估目標的 `Condition` 屬性。 如果 `Condition` 屬性存在且評估為 `false`，則不會執行目標，且不會對組建產生任何進一步的作用。

   其他列出 `BeforeTargets` 或 `AfterTargets` 中條件式目標的目標，仍會根據指定的順序執行。

4. 在執行或跳過目標前，其 `DependsOnTargets` 目標仍會執行，除非 `Condition` 屬性已套用到目標，並評估為 `false`。

   > [!NOTE]
   > 若沒有執行，則會將目標視為跳過，因為其輸出項目已是最新狀態 (請參閱[累加建置](../msbuild/incremental-builds.md))。 這項檢查會在於目標內部執行工作前完成，且不會影響目標的執行順序。

5. 在執行或跳過目標前，任何在 `BeforeTargets` 屬性中列出目標的其他目標都會執行。

6. 在執行目標前，會先比較它的 `Inputs` 屬性和 `Outputs` 屬性。 如果 MSBuild 判斷有任何與一或多個對應輸入檔相關的輸出檔過時，則 MSBuild 會執行目標。 否則，MSBuild 會略過目標。

7. 在執行或跳過目標後，任何在 `AfterTargets` 屬性中列出它的其他目標都會執行。

## <a name="see-also"></a>另請參閱

- [目標](../msbuild/msbuild-targets.md)
