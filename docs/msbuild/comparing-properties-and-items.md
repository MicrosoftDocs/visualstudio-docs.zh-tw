---
title: 比較屬性和項目 | Microsoft Docs
description: 瞭解 MSBuild 屬性和專案如何將資訊傳遞至工作、評估條件，以及儲存專案檔可以參考的值。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, msbuild properties
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 226b86d621de2faee5a71d9fdb3fea39f20b984e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888117"
---
# <a name="compare-properties-and-items"></a>比較屬性和項目

MSBuild 屬性和項目都可用來將資訊傳遞至工作、評估條件，以及儲存可在整個專案檔中參考的值。

- 屬性是名稱/值組。 如需詳細資訊，請參閱 [MSBuild 屬性](../msbuild/msbuild-properties.md)。

- 項目是通常代表檔案的物件。 項目物件可具有相關聯的中繼資料集合。 中繼資料是名稱/值組。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。

## <a name="scalars-and-vectors"></a>純量和向量

由於 MSBuild 屬性是只有一個字串值的名稱/值組，因此，通常會以「純量」來描述它們。 因為 MSBuild 項目類型是項目清單，所以，通常會以「向量」來描述它們。 不過，在實務上，屬性可以代表多個值，而項目類型可以有零個或一個項目。

### <a name="target-dependency-injection"></a>目標相依性插入

若要查看屬性如何代表多個值，請考慮使用常見使用模式來將目標加入至要建置的目標清單。 此清單通常是由屬性值來表示，並以分號分隔目標名稱。

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

通常會使用 `BuildDependsOn` 屬性 (Property) 做為目標 `DependsOnTargets` 屬性 (Attribute) 的引數，以便有效地將它轉換至項目清單。 您可以覆寫這個屬性，以加入目標，或是變更目標執行順序。 例如，

```xml
<PropertyGroup>
    <BuildDependsOn>
        $(BuildDependsOn);
        CustomBuild;
    </BuildDependsOn>
</PropertyGroup>
```

將 CustomBuild 目標加入至目標清單，並為 `BuildDependsOn` 提供`BeforeBuild;CoreBuild;AfterBuild;CustomBuild` 值。

從 MSBuild 4.0 開始，已取代目標相依性插入。 改為使用 `AfterTargets` 和 `BeforeTargets` 屬性。 如需詳細資訊，請參閱[目標建置順序](../msbuild/target-build-order.md)。

### <a name="conversions-between-strings-and-item-lists"></a>字串與項目清單之間的轉換

MSBuild 會視需要在項目類型和字串值之間來回執行轉換。 若要查看項目清單如何變成字串值，請考慮在使用項目類型做為 MSBuild 屬性的值時，會發生什麼事：

```xml
<ItemGroup>
    <OutputDir Include="KeyFiles\;Certificates\" />
</ItemGroup>
<PropertyGroup>
    <OutputDirList>@(OutputDir)</OutputDirList>
</PropertyGroup>
```

項目類型 OutputDir 具有 `Include` 屬性以及 "KeyFiles\\;Certificates\\"值。 MSBuild 會將此字串剖析成兩個項目︰KeyFiles\ 和 Certificates\\。 將項目類型 OutputDir 用來做為 OutputDirList 屬性的值時，MSBuild 會將此項目類型轉換或「扁平化」為以分號分隔的字串 "KeyFiles\\;Certificates\\"。

## <a name="properties-and-items-in-tasks"></a>工作中的屬性和項目

屬性和項目可用來做為 MSBuild 工作的輸入和輸出。 如需詳細資訊，請參閱[工作](../msbuild/msbuild-tasks.md)。

屬性是當成屬性傳遞到工作。 在工作中，MSBuild 屬性是以值可來回轉換為字串的屬性類型來表示。 支援的屬性類型包含 `bool`、`char`、`DateTime`、`Decimal`、`Double`、`int`、`string`，以及 <xref:System.Convert.ChangeType%2A> 可處理的所有類型。

項目會以 <xref:Microsoft.Build.Framework.ITaskItem> 物件形式傳遞給工作。 在工作內，<xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> 代表項目的值，而 <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> 會擷取其中繼資料。

項目類型的項目清單可以當成 `ITaskItem` 物件陣列來傳遞。 從 .NET Framework 3.5 開始，就能在目標中使用 `Remove` 屬性，從項目清單中移除項目。 因為可從項目清單中移除項目，所以項目類型可能會有零個項目。 如果將項目清單傳遞到工作，工作中的程式碼應該會檢查這種可能性。

## <a name="property-and-item-evaluation-order"></a>屬性和項目評估順序

在組建的評估階段，會將匯入的檔案以其出現的順序併入組建。 屬性和項目是以下列順序分三個階段來定義：

- 屬性是以其出現的順序來定義和修改。

- 項目定義是以其出現的順序來定義和修改。

- 項目是以其出現的順序來定義和修改。

在組建的執行階段，目標內所定義的屬性和項目會在單一階段以其出現的順序一併進行評估。

不過，這不是完整的資訊。 在定義屬性、項目定義或項目時，會評估它的值。 運算式評估工具會展開字串來指定值。 字串展開是取決於建置階段。 以下是更詳細的屬性和項目評估順序：

- 在組建的評估階段：

  - 屬性是以其出現的順序來定義和修改。 屬性函式會執行。 在運算式內展開表單 $(PropertyName) 中的屬性值。 屬性值會設為展開的運算式。

  - 項目定義是以其出現的順序來定義和修改。 已在運算式內展開屬性函式。 中繼資料值會設為展開的運算式。

  - 項目類型都是以其出現的順序來定義和修改。 表單 @(ItemType) 中的項目值均會展開。 同時也會展開項目轉換。 已在運算式內展開屬性函式和值。 項目清單和中繼資料值會設為展開的運算式。

- 在組建的執行階段：

  - 目標內所定義的屬性和項目會以其出現的順序一併進行評估。 屬性函式會執行，並在運算式內展開屬性值。 同時也會展開項目值和項目轉換。 屬性值、項目類型值和中繼資料值均會設為展開的運算式。

### <a name="subtle-effects-of-the-evaluation-order"></a>評估順序的微妙效果

在組建的評估階段，屬性評估是在項目評估之前。 不過，屬性可以具有取決於項目值而出現的值。 請考慮下列指令碼。

```xml
<ItemGroup>
    <KeyFile Include="KeyFile.cs">
        <Version>1.0.0.3</Version>
    </KeyFile>
</ItemGroup>
<PropertyGroup>
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
</PropertyGroup>
<Target Name="AfterBuild">
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

執行 Message 工作會顯示下列訊息：

```
KeyFileVersion: 1.0.0.3
```

這是因為 `KeyFileVersion` 的值實際上是 "\@(KeyFile->'%(Version)')" 字串。 項目和項目轉換並未在第一次定義屬性時展開，因此已為 `KeyFileVersion` 屬性指派未展開的字串值。

在組建的執行階段，當它處理 Message 工作時，MSBuild 會展開字串 "\@(KeyFile->'%(Version)')" 以得出 "1.0.0.3"。

請注意，即使反轉了屬性和項目群組的順序，還是會出現相同的訊息。

在第二個範例中，請考慮當屬性和項目群組位於目標內時可發生什麼情況：

```xml
<Target Name="AfterBuild">
    <PropertyGroup>
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
    </PropertyGroup>
    <ItemGroup>
        <KeyFile Include="KeyFile.cs">
            <Version>1.0.0.3</Version>
        </KeyFile>
    </ItemGroup>
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

Message 工作會顯示下列訊息：

```
KeyFileVersion:
```

這是因為在組建的執行階段，會以從上到下的方式同時評估目標內定義的屬性和項目群組。 若定義了 `KeyFileVersion`，`KeyFile` 即為未知的。 因此，項目轉換會展開為空字串。

在此情況下，反轉屬性和項目群組的順序會還原原始的訊息：

```xml
<Target Name="AfterBuild">
    <ItemGroup>
        <KeyFile Include="KeyFile.cs">
            <Version>1.0.0.3</Version>
        </KeyFile>
    </ItemGroup>
    <PropertyGroup>
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
    </PropertyGroup>
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

`KeyFileVersion` 的值會設為 "1.0.0.3"，而不是 "\@(KeyFile->'%(Version)')"。 Message 工作會顯示下列訊息：

```
KeyFileVersion: 1.0.0.3
```

## <a name="see-also"></a>另請參閱

- [進階概念](../msbuild/msbuild-advanced-concepts.md)
