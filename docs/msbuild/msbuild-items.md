---
title: MSBuild 項目 | Microsoft Docs
description: 瞭解如何使用 ItemGroup 的 MSBuild Include 屬性來指定要包含在組建中的檔案。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d4bfc58c9be578514598fce2d447ef921d091177
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919075"
---
# <a name="msbuild-items"></a>MSBuild 項目

MSBuild 項目是建置系統的輸入，而且它們通常代表檔案 (檔案是在 `Include` 屬性中指定)。 項目 (Item) 會依據它們的項目 (Element) 名稱分組為項目 (Item) 類型。 項目類型是具名的項目清單，可用來做為工作的參數。 工作會使用項目值來執行建置程序的步驟。

 由於項目是根據其所屬的項目類型來命名，因此可交換使用「項目」和「項目值」等詞彙。

## <a name="create-items-in-a-project-file"></a>在專案檔中建立項目

 您會將專案檔中的項目 (Item) 宣告為 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 項目 (Element) 的子項目 (Element)。 子項目 (Element) 的名稱是項目 (Item) 的類型。 項目 (Element) 的 `Include` 屬性會指定要包含於該項目 (Item) 類型的項目 (Item) (檔案)。 例如，下列 XML 會建立名為 `Compile` 的項目類型，其中包含兩個檔案。

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 專案 *file2.cs* 不會取代專案 *file1.cs*;相反地，檔案名會附加至專案類型的值清單 `Compile` 。

 下列 XML 會在一個 `Include` 屬性中宣告這兩個檔案，來建立相同的項目類型。 請注意，檔案名稱是以分號分隔的。

```xml
<ItemGroup>
    <Compile Include = "file1.cs;file2.cs"/>
</ItemGroup>
```

`Include`屬性（attribute）是相對於專案檔資料夾 $ (MSBuildProjectPath) 的路徑，即使專案是在匯入的檔案中（例如 *.targets* 檔案）也是一樣。

## <a name="create-items-during-execution"></a>執行期間建立項目

 [Target](../msbuild/target-element-msbuild.md) 項目 (Element) 以外的項目 (Item) 值是在組建的評估階段所指派。 在後續的執行階段，可以使用下列方式來建立或修改項目：

- 任何工作均可發出項目。 若要發出項目 (Item)，[Task](../msbuild/task-element-msbuild.md) 項目 (Element) 必須含有具 `ItemName` 屬性的子系 [Output](../msbuild/output-element-msbuild.md) 項目 (Element)。

- [CreateItem](../msbuild/createitem-task.md) 工作可以發出項目。 這種使用方式已過時。

- 從 .NET Framework 3.5 開始，`Target` 項目可能會包含 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 項目，其中可能包含 Item 項目。

## <a name="reference-items-in-a-project-file"></a>參考專案檔中的項目

 若要在整個專案檔中參考項目類型，您可以使用語法 @(\<ItemType>)。 例如，您應該使用 `@(Compile)`，來參考前一個範例中的項目類型。 使用下列語法，您可以藉由指定項目類型做為工作的參數，來將項目傳遞給該工作。 如需詳細資訊，請參閱 [如何：選取要建立的](../msbuild/how-to-select-the-files-to-build.md)檔案。

 根據預設，項目類型的項目在展開時會以分號 (;) 分隔。 您可以使用語法 @ (\<ItemType> ，' \<separator> ' ) 指定預設值以外的分隔符號。 如需詳細資訊，請參閱 [如何：顯示以逗號分隔的專案清單](../msbuild/how-to-display-an-item-list-separated-with-commas.md)。

## <a name="use-wildcards-to-specify-items"></a>使用萬用字元指定項目

您可以使用 `**`、`*` 和 `?` 萬用字元指定一組檔案作為組建的輸入，而不是個別列出每個檔案。

- `?` 萬用字元會比對單一字元。
- `*` 萬用字元會比對零或多個字元。
- `**` 萬用字元會循序比對部分路徑。

例如，您可以在專案檔中使用下列項目，來指定包含該專案檔之目錄中的所有 `.cs` 檔案。

```xml
<CSFile Include="*.cs"/>
```

下列項目會選取 `D:` 磁碟機上的所有 `.vb` 檔案：

```xml
<VBFile Include="D:/**/*.vb"/>
```

如果您想要在沒有萬用字元展開的項目中包含常值 `*` 或 `?` 字元，您必須[逸出萬用字元](../msbuild/how-to-escape-special-characters-in-msbuild.md)。

如需萬用字元的詳細資訊，請參閱 [如何：選取要建立的](../msbuild/how-to-select-the-files-to-build.md)檔案。

## <a name="use-the-exclude-attribute"></a>使用 Exclude 屬性

 Item 項目 (Element) 可以包含 `Exclude` 屬性，以從項目 (Item) 類型中排除特定的項目 (Item) (檔案)。 `Exclude` 屬性通常會與萬用字元搭配使用。 例如，下列 XML 會將目錄中的每個 *.cs* 檔案新增至 CSFile 項目類型，但 *DoNotBuild.cs* 檔案除外。

```xml
<ItemGroup>
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>
</ItemGroup>
```

 `Exclude` 屬性只會影響包含這兩者之 Item 項目 (Element) 中由 `Include` 屬性所加入的項目 (Item)。 下列範例不會排除 *Form1.cs* 檔案，這是在先前的 item 專案中加入的。

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

 如需詳細資訊，請參閱 [如何：從組建中排除](../msbuild/how-to-exclude-files-from-the-build.md)檔案。

## <a name="item-metadata"></a>項目中繼資料

 在 `Include` 和 `Exclude` 屬性中，除了資訊，項目可能還會包含中繼資料。 若工作需要更多關於項目的資訊，就會使用此中繼資料，或使用此中繼資料來批次處理工作和目標。 如需詳細資訊，請參閱[批次處理](../msbuild/msbuild-batching.md)。

 中繼資料是一個索引鍵值組的集合，可在專案檔中宣告為 Item 項目的子項目。 子項目的名稱是中繼資料的名稱，而子項目的值是中繼資料的值。

 中繼資料會與包含它的 Item 項目相關聯。 例如，下列 XML `Culture` 會將具有值的中繼資料加入 `Fr` 至新增至 csfile 專案類型的 *one.cs* 和 *two.cs* 專案。

```xml
<ItemGroup>
    <CSFile Include="one.cs;two.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 項目可以有零或多個中繼資料值。 您可以隨時變更中繼資料值。 如果您將中繼資料設為空值，就能有效地從組建中移除它。

### <a name="reference-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> 在專案檔中參考項目中繼資料

 您可以使用語法 %(\<ItemMetadataName>)，在整個專案檔中參考項目中繼資料。 如果發生模稜兩可的情況，您可以使用項目類型的名稱來限定參考。 例如，您可以指定% (\<ItemType.ItemMetaDataName>) 。下列範例會使用顯示中繼資料來批次處理訊息工作。 如需如何使用項目中繼資料進行批次處理的詳細資訊，請參閱[工作批次處理中的項目中繼資料](../msbuild/item-metadata-in-task-batching.md)。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Stuff Include="One.cs" >
            <Display>false</Display>
        </Stuff>
        <Stuff Include="Two.cs">
            <Display>true</Display>
        </Stuff>
    </ItemGroup>
    <Target Name="Batching">
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>
    </Target>
</Project>
```

### <a name="well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a> 已知的專案中繼資料

 將項目加入至項目類型時，即會為該項目指派一些已知的中繼資料。 例如，所有專案都具有已知的中繼資料% (\<Filename>) ，其值為專案的檔案名， (不含副檔名) 。 如需詳細資訊，請參閱 [已知的專案中繼資料](../msbuild/msbuild-well-known-item-metadata.md)。

### <a name="transform-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> 使用中繼資料轉換項目類型

 您可以使用中繼資料，來將項目清單轉換為新的項目清單。 例如，您可以使用運算式，將具有代表 .cpp 檔案之專案的專案類型轉換 `CppFiles` 成 .obj 檔案的對應清單 *。* `@(CppFiles -> '%(Filename).obj')`

 下列程式碼會建立 `CultureResource` 項目類型，其中包含所有具 `Culture` 中繼資料之 `EmbeddedResource` 項目的複本。 `Culture` 中繼資料值會成為新中繼資料 `CultureResource.TargetDirectory` 的值。

```xml
<Target Name="ProcessCultureResources">
    <ItemGroup>
        <CultureResource Include="@(EmbeddedResource)"
            Condition="'%(EmbeddedResource.Culture)' != ''">
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>
        </CultureResource>
    </ItemGroup>
</Target>
```

 如需詳細資訊，請參閱[轉換](../msbuild/msbuild-transforms.md)。

## <a name="item-definitions"></a>項目定義

 從 .NET Framework 3.5 開始，您可以使用 [ItemDefinitionGroup 項目](../msbuild/itemdefinitiongroup-element-msbuild.md) (Element)，來將預設的中繼資料加入至任何項目類型。 如同已知的中繼資料，預設的中繼資料會與您指定之項目類型的所有項目相關聯。 您可以在項目定義中明確覆寫預設的中繼資料。 例如，下列 XML 會提供 `Compile` 專案 *one.cs* ，並 *Three.cs* `BuildDay` 值為 "Monday" 的中繼資料。 此程式碼會為專案 *two.cs* `BuildDay` 值為 "星期二" 的中繼資料。

```xml
<ItemDefinitionGroup>
    <Compile>
        <BuildDay>Monday</BuildDay>
    </Compile>
</ItemDefinitionGroup>
<ItemGroup>
    <Compile Include="one.cs;three.cs" />
    <Compile Include="two.cs">
        <BuildDay>Tuesday</BuildDay>
    </Compile>
</ItemGroup>
```

 如需詳細資訊，請參閱[項目定義](../msbuild/item-definitions.md)。

## <a name="attributes-for-items-in-an-itemgroup-of-a-target"></a>目標 ItemGroup 中的項目屬性

 從 .NET Framework 3.5 開始，`Target` 項目可能會包含 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 項目，其中可能包含 Item 項目。 如果已針對 `ItemGroup` (位於 `Target`) 中的項目指定本節中的屬性，則它們是有效的。

### <a name="remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> 移除屬性

 `Remove` 屬性會移除項目類型中的特定項目 (檔案)。 這個屬性是在 .NET Framework 3.5 中引進，但在目標中 (僅) 。 從 MSBuild 15.0 開始支援內部和外部目標。

 下列範例會從 Compile 專案類型移除每個 *.config* 檔案。

```xml
<Target>
    <ItemGroup>
        <Compile Remove="*.config"/>
    </ItemGroup>
</Target>
```

### <a name="keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> KeepMetadata 屬性

 如果在目標內產生項目 (Item)，則 Item 項目 (Element) 可以包含 `KeepMetadata` 屬性。 如果指定了這個屬性，只會將以分號分隔之名稱清單中指定的中繼資料從來源項目傳輸到目標項目。 若此屬性的值為空值，就相當於未指定它。 `KeepMetadata` 屬性是在 .NET Framework 4.5 中引入的。

 下列範例示範如何使用 `KeepMetadata` 屬性。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
ToolsVersion="4.0">

    <ItemGroup>
        <FirstItem Include="rhinoceros">
            <Class>mammal</Class>
            <Size>large</Size>
        </FirstItem>

    </ItemGroup>
    <Target Name="MyTarget">
        <ItemGroup>
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />
        </ItemGroup>

        <Message Text="FirstItem: %(FirstItem.Identity)" />
        <Message Text="  Class: %(FirstItem.Class)" />
        <Message Text="  Size:  %(FirstItem.Size)"  />

        <Message Text="SecondItem: %(SecondItem.Identity)" />
        <Message Text="  Class: %(SecondItem.Class)" />
        <Message Text="  Size:  %(SecondItem.Size)"  />
    </Target>
</Project>

<!--
Output:
  FirstItem: rhinoceros
    Class: mammal
    Size:  large
  SecondItem: rhinoceros
    Class: mammal
    Size:
-->
```

### <a name="removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a> RemoveMetadata 屬性

 如果在目標內產生項目 (Item)，則 Item 項目 (Element) 可以包含 `RemoveMetadata` 屬性。 如果指定了此屬性，則會將所有中繼資料從來源項目傳輸到目標項目，但名稱位於以分號分隔之名稱清單內的中繼資料除外。 若此屬性的值為空值，就相當於未指定它。 `RemoveMetadata` 屬性是在 .NET Framework 4.5 中引入的。

 下列範例示範如何使用 `RemoveMetadata` 屬性。

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <MetadataToRemove>Size;Material</MetadataToRemove>
    </PropertyGroup>

    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />
        </ItemGroup>

        <Message Text="Item1: %(Item1.Identity)" />
        <Message Text="  Size:     %(Item1.Size)" />
        <Message Text="  Color:    %(Item1.Color)" />
        <Message Text="  Material: %(Item1.Material)" />
        <Message Text="Item2: %(Item2.Identity)" />
        <Message Text="  Size:     %(Item2.Size)" />
        <Message Text="  Color:    %(Item2.Color)" />
        <Message Text="  Material: %(Item2.Material)" />
    </Target>
</Project>

<!--
Output:
  Item1: stapler
    Size:     medium
    Color:    black
    Material: plastic
  Item2: stapler
    Size:
    Color:    black
    Material:
-->
```

### <a name="keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> KeepDuplicates 屬性

 如果在目標內產生項目 (Item)，則 Item 項目 (Element) 可以包含 `KeepDuplicates` 屬性。 `KeepDuplicates` 為 `Boolean` 屬性，會指定項目如果與現有項目完全重複，是否應加入目標群組。

 如果來源和目標項目具有相同的 Include 值，但中繼資料不同，則即使已將 `KeepDuplicates` 設定為 `false`，也會加入該項目。 若此屬性的值為空值，就相當於未指定它。 `KeepDuplicates` 屬性是在 .NET Framework 4.5 中引入的。

 下列範例示範如何使用 `KeepDuplicates` 屬性。

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Item1 Include="hourglass;boomerang" />
        <Item2 Include="hourglass;boomerang" />
    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <Item1 Include="hourglass" KeepDuplicates="false" />
            <Item2 Include="hourglass" />
        </ItemGroup>

        <Message Text="Item1: @(Item1)" />
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />
        <Message Text="Item2: @(Item2)" />
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />
    </Target>
</Project>

<!--
Output:
  Item1: hourglass;boomerang
    hourglass  Count: 1
    boomerang  Count: 1
  Item2: hourglass;boomerang;hourglass
    hourglass  Count: 2
    boomerang  Count: 1
-->
```

## <a name="updating-metadata-on-items-in-an-itemgroup-outside-of-a-target"></a>更新目標外部 ItemGroup 專案的中繼資料

目標外的專案可以透過屬性來更新其現有中繼資料 `Update` 。 目標底下的專案 **無法** 使用這個屬性。

```xml
<Project>
    <PropertyGroup>
        <MetadataToUpdate>pencil</MetadataToUpdate>
    </PropertyGroup>

    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Color>red</Color>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="notebook">
            <Size>SMALL</Size>
            <Color>YELLOW</Color>
        </Item2>

        <!-- Metadata can be expressed either as attributes or as elements -->
        <Item1 Update="$(MetadataToUpdate);stapler;er*r;@(Item2)" Price="10" Material="">
            <Color>RED</Color>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: medium
    Color: RED
    Material:
    Price: 10
Item1: pencil
    Size: small
    Color: RED
    Material:
    Price: 10
Item1: eraser
    Size:
    Color: RED
    Material:
    Price: 10
Item1: notebook
    Size: large
    Color: RED
    Material:
    Price: 10
-->
```

:::moniker range=">=vs-2019"
在 MSBuild 16.6 版和更新版本中， `Update` 屬性支援限定的中繼資料參考，以協助從兩個或多個專案匯入中繼資料。

```xml
<Project>
    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Size>small</Size>
            <Color>red</Color>
            <Material>gum</Material>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="pencil">
            <Size>MEDIUM</Size>
            <Color>RED</Color>
            <Material>PLASTIC</Material>
            <Price>10</Price>
        </Item2>

        <Item3 Include="notebook">
            <Size>SMALL</Size>
            <Color>BLUE</Color>
            <Price>20</Price>
        </Item3>

        <!-- Metadata can be expressed either as attributes or as elements -->
        <Item1 Update="@(Item2);er*r;@(Item3)" Size="%(Size)" Color="%(Item2.Color)" Price="%(Item3.Price)" Model="2020">
            <Material Condition="'%(Item2.Material)' != ''">Premium %(Item2.Material)</Material>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)
    Model: %(Item1.Model)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: medium
    Color: black
    Material: plastic
    Price:
    Model:
Item1: pencil
    Size: small
    Color: RED
    Material: Premium PLASTIC
    Price:
    Model: 2020
Item1: eraser
    Size: small
    Color:
    Material: gum
    Price:
    Model: 2020
Item1: notebook
    Size: large
    Color:
    Material: paper
    Price: 20
    Model: 2020
-->
```

備註：
- 不合格的中繼資料 (% (M) # A3 系結至 `Item1` 上述範例) 中 (更新的專案類型。 限定的中繼資料 () 系結至 `%(Item2.Color)` 來自更新運算式的一組已從相符專案類型內。
- 如果專案在多個參考專案之間和之間符合多次：
  - 每個參考專案類型的最後一個相符專案都會被捕獲 (因此，每個專案類型的一個捕捉專案) 。
  - 這符合目標下工作專案批次處理的行為。
- 其中一個可放置% ( # A1 參考：
  - 中繼資料
  - 中繼資料條件
- 中繼資料名稱比對不區分大小寫。
:::moniker-end

## <a name="updating-metadata-on-items-in-an-itemgroup-of-a-target"></a>更新目標 ItemGroup 中專案的中繼資料

您也可以使用較不明確的語法，在目標內部修改中繼資料 `Update` 。

```xml
<Project>
    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Size>small</Size>
            <Color>red</Color>
            <Material>gum</Material>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="pencil">
            <Size>MEDIUM</Size>
            <Color>RED</Color>
            <Material>PLASTIC</Material>
            <Price>10</Price>
        </Item2>

        <Item2 Include="ruler">
            <Color>GREEN</Color>
        </Item2>

    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <!-- Metadata can be expressed either as attributes or as elements -->
            <Item1 Size="GIGANTIC" Color="%(Item2.Color)">
                <Material Condition="'%(Item2.Material)' != ''">Premium %(Item2.Material)</Material>
            </Item1>
        </ItemGroup>

        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)
    Model: %(Item1.Model)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: pencil
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: eraser
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: notebook
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
-->
```

## <a name="see-also"></a>另請參閱

- [Item 項目 (MSBuild)](../msbuild/item-element-msbuild.md)
- [一般 MSBuild 專案項目](../msbuild/common-msbuild-project-items.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [如何：選取要建置的檔案](../msbuild/how-to-select-the-files-to-build.md)
- [如何：從組建中排除檔案](../msbuild/how-to-exclude-files-from-the-build.md)
- [如何：顯示以逗號分隔的專案清單](../msbuild/how-to-display-an-item-list-separated-with-commas.md)
- [項目定義](../msbuild/item-definitions.md)
- [批次處理](../msbuild/msbuild-batching.md)
