---
title: 如何：累加建置 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4911bb131f5c5c878b82865b3dee61fd7bedbe1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634158"
---
# <a name="how-to-build-incrementally"></a>如何：累加建置

當您建置大型專案時，很重要的一點是，如果先前建置的元件仍是最新，就不會重建。 如果每次都建置所有目標，每次建置會花很長的時間才能完成。 要啟用增量生成（其中僅生成之前尚未生成的目標或已重建的目標），Microsoft 生成引擎 （MSBuild） 可以將輸入檔的時間戳記與輸出檔案的時間戳記進行比較，並且確定是跳過、生成還是部分重建目標。 不過，在輸入和輸出之間必須有一對一的對應。 您可以使用轉換，讓目標可以找出這種直接對應。 如需轉換的詳細資訊，請參閱[轉換](../msbuild/msbuild-transforms.md)。

## <a name="specify-inputs-and-outputs"></a>指定輸入和輸出

如果專案檔中指定了輸入和輸出，您就可以累加方式來建置目標。

#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>指定目標的輸入和輸出

- 使用 `Target` 項目的 `Inputs` 和 `Outputs` 屬性。 例如：

  ```xml
  <Target Name="Build"
      Inputs="@(CSFile)"
      Outputs="hello.exe">
  ```

MSBuild 可以將輸入檔的時間戳記與輸出檔案的時間戳記進行比較，並確定是跳過、生成還是部分重建目標。 在下面的示例中，如果`@(CSFile)`專案清單中的任何檔比 hello.exe 檔更新，MSBuild 將運行目標;如果專案清單中的任何檔比*hello.exe*檔更新，則 MSBuild 將運行目標。否則將跳過：

```xml
<Target Name="Build"
    Inputs="@(CSFile)"
    Outputs="hello.exe">

    <Csc
        Sources="@(CSFile)"
        OutputAssembly="hello.exe"/>
</Target>
```

當目標中指定輸入和輸出時，可能每個輸出對應到唯一的一個輸入，或者是輸出和輸入之間不能有直接對應。 例如，在以前的[Csc 任務中](../msbuild/csc-task.md)，輸出*hello.exe*無法映射到任何單個輸入-它取決於所有輸入。

> [!NOTE]
> 在輸入和輸出之間沒有直接映射的目標始終比每個輸出只能映射到一個輸入的目標更頻繁，因為 MSBuild 無法確定某些輸入已更改時需要重新生成哪些輸出。

您可以識別輸出和輸入之間有直接對應的工作，例如 [LC 工作](../msbuild/lc-task.md)，最適合進行累加建置，而不像 [Csc](../msbuild/csc-task.md) 和 [Vbc](../msbuild/vbc-task.md) 之類的工作，它們會從許多輸入產生一個輸出組件。

## <a name="example"></a>範例

下列範例使用為假定說明系統建置說明檔的專案。 該專案的工作原理是將 source *.txt*檔轉換為中間*的 .content*檔，然後將這些檔與 XML 元資料檔案合併，以生成説明系統使用的最終 *.help*檔。 專案會使用下列假定的工作︰

- `GenerateContentFiles`：將 *.txt*檔轉換為 *.content*檔。

- `BuildHelp`：合併 *.content*檔和 XML 元資料檔案以生成最終的 *.help*檔。

專案會使用轉換來為 `GenerateContentFiles` 工作建立輸入與輸出之間的一對一對應。 如需詳細資訊，請參閱[轉換](../msbuild/msbuild-transforms.md)。 此外，`Output` 項目設定為自動使用來自 `GenerateContentFiles` 工作的輸出，作為 `BuildHelp` 工作的輸入。

這個專案檔同時包含 `Convert` 和 `Build` 目標。 `GenerateContentFiles` 和 `BuildHelp` 工作分別放在 `Convert` 和 `Build`目標，以便能以累加方式建置每個目標。 藉由使用 `Output` 項目，`GenerateContentFiles` 工作的輸出會放在 `ContentFile` 項目清單，在這裡它們可以作為 `BuildHelp` 工作的輸入。 這樣使用 `Output` 項目，會自動提供一個工作的輸出作為另一個工作的輸入，您便不需要以手動方式在每個工作列出個別項目或項目清單。

> [!NOTE]
> 雖然 `GenerateContentFiles` 目標可以以累加方式建置，該目標的所有輸出永遠必須作為 `BuildHelp` 目標的輸入。 當您使用元素時，MSBuild 會自動提供來自一個目標的所有輸出作為另一個目標的`Output`輸入。

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
- [目標元素 （MSBuild）](../msbuild/target-element-msbuild.md)
- [轉換](../msbuild/msbuild-transforms.md)
- [Csc 工作](../msbuild/csc-task.md)
- [Vbc 任務](../msbuild/vbc-task.md)
