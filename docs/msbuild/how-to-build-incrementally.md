---
title: 如何：累加建置 | Microsoft Docs
description: 瞭解如何使用 MSBuild 以累加方式建立，因此不會重建先前建立但仍處於最新狀態的元件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fa0f03869f61ef55e5a2346135c32dc0a5d7bbf0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914509"
---
# <a name="how-to-build-incrementally"></a>如何：累加建置

當您建置大型專案時，很重要的一點是，如果先前建置的元件仍是最新，就不會重建。 如果每次都建置所有目標，每次建置會花很長的時間才能完成。 若要啟用累加組建 (組建，其中只有未在過期或目標之前建立的目標，會) 重建，Microsoft Build Engine (MSBuild) 可以比較輸入檔案的時間戳記與輸出檔案的時間戳記，並判斷是否要跳過、建立或部分重建目標。 不過，在輸入和輸出之間必須有一對一的對應。 您可以使用轉換，讓目標可以找出這種直接對應。 如需轉換的詳細資訊，請參閱[轉換](../msbuild/msbuild-transforms.md)。

## <a name="specify-inputs-and-outputs"></a>指定輸入和輸出

如果專案檔中指定了輸入和輸出，您就可以累加方式來建置目標。

#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>指定目標的輸入和輸出

- 使用 `Target` 項目的 `Inputs` 和 `Outputs` 屬性。 例如：

  ```xml
  <Target Name="Build"
      Inputs="@(CSFile)"
      Outputs="hello.exe">
  ```

MSBuild 可以比較輸入檔案的時間戳記與輸出檔案的時間戳記，並判斷要跳過、建立還是部分重建目標。 在下列範例中，如果專案清單中的任何檔案 `@(CSFile)` 比 *hello.exe* 檔案新，則 MSBuild 會執行目標，否則會略過：

```xml
<Target Name="Build"
    Inputs="@(CSFile)"
    Outputs="hello.exe">

    <Csc
        Sources="@(CSFile)"
        OutputAssembly="hello.exe"/>
</Target>
```

當目標中指定輸入和輸出時，可能每個輸出對應到唯一的一個輸入，或者是輸出和輸入之間不能有直接對應。 例如，在先前的 [Csc](../msbuild/csc-task.md)工作中，輸出 *hello.exe* 不能對應至任何單一輸入，這取決於所有的輸入。

> [!NOTE]
> 輸入和輸出之間沒有直接對應的目標，一律會比每個輸出只能對應到一個輸入的目標更頻繁地建立，因為 MSBuild 無法判斷某些輸入變更時需要重建的輸出。

您可以識別輸出和輸入之間有直接對應的工作，例如 [LC 工作](../msbuild/lc-task.md)，最適合進行累加建置，而不像 [Csc](../msbuild/csc-task.md) 和 [Vbc](../msbuild/vbc-task.md) 之類的工作，它們會從許多輸入產生一個輸出組件。

## <a name="example"></a>範例

下列範例使用為假定說明系統建置說明檔的專案。 專案的運作方式是將來源 *.txt* 檔轉換成 *中繼檔案* ，然後結合 XML 中繼資料檔案來產生說明系統所使用的 *最後一個* 說明檔。 專案會使用下列假定的工作︰

- `GenerateContentFiles`：將 *.txt* 檔案轉換成 *content-type* 檔。

- `BuildHelp`：結合 *. 內容* 檔案和 XML 中繼資料檔案來 *建立最終的說明檔。*

專案會使用轉換來為 `GenerateContentFiles` 工作建立輸入與輸出之間的一對一對應。 如需詳細資訊，請參閱[轉換](../msbuild/msbuild-transforms.md)。 此外，`Output` 項目設定為自動使用來自 `GenerateContentFiles` 工作的輸出，作為 `BuildHelp` 工作的輸入。

這個專案檔同時包含 `Convert` 和 `Build` 目標。 `GenerateContentFiles` 和 `BuildHelp` 工作分別放在 `Convert` 和 `Build`目標，以便能以累加方式建置每個目標。 藉由使用 `Output` 項目，`GenerateContentFiles` 工作的輸出會放在 `ContentFile` 項目清單，在這裡它們可以作為 `BuildHelp` 工作的輸入。 這樣使用 `Output` 項目，會自動提供一個工作的輸出作為另一個工作的輸入，您便不需要以手動方式在每個工作列出個別項目或項目清單。

> [!NOTE]
> 雖然 `GenerateContentFiles` 目標可以以累加方式建置，該目標的所有輸出永遠必須作為 `BuildHelp` 目標的輸入。 當您使用專案時，MSBuild 會自動提供一個目標的所有輸出做為另一個目標的輸入 `Output` 。

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <ItemGroup>
        <TXTFile Include="*.txt"/>
        <XMLFiles Include="\metadata\*.xml"/>
    </ItemGroup>

    <Target Name = "Convert"
        Inputs="@(TXTFile)"
        Outputs="@(TXTFile->'%(Filename).content')">

        <GenerateContentFiles
            Sources = "@(TXTFile)">
            <Output TaskParameter = "OutputContentFiles"
                ItemName = "ContentFiles"/>
        </GenerateContentFiles>
    </Target>

    <Target Name = "Build" DependsOnTargets = "Convert"
        Inputs="@(ContentFiles);@(XMLFiles)"
        Outputs="$(MSBuildProjectName).help">

        <BuildHelp
            ContentFiles = "@(ContentFiles)"
            MetadataFiles = "@(XMLFiles)"
            OutputFileName = "$(MSBuildProjectName).help"/>
    </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [目標](../msbuild/msbuild-targets.md)
- [MSBuild)  (目標元素 ](../msbuild/target-element-msbuild.md)
- [轉換](../msbuild/msbuild-transforms.md)
- [Csc 工作](../msbuild/csc-task.md)
- [Vbc 工作](../msbuild/vbc-task.md)
