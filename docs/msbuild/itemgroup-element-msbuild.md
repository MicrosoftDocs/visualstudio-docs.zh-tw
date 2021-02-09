---
title: ItemGroup 項目 (MSBuild) | Microsoft Docs
description: 瞭解 MSBuild ItemGroup 元素，其中包含一組使用者定義的專案元素。 每個專案都必須是 ItemGroup 的子系。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eff27467aeea5068f3ec086b490ca9c735861549
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913849"
---
# <a name="itemgroup-element-msbuild"></a>ItemGroup 項目 (MSBuild)

包含一組使用者定義的 [Item](../msbuild/item-element-msbuild.md) 元素。 MSBuild 專案中使用的每個專案都必須指定為元素的子系 `ItemGroup` 。

\<Project>
\<ItemGroup>

## <a name="syntax"></a>Syntax

```xml
<ItemGroup Condition="'String A' == 'String B'"
           Label="Label">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemGroup>
```

## <a name="attributes-and-elements"></a>屬性和元素

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Condition`|選擇性屬性。 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|
|`Label`|選擇性屬性。 識別 `ItemGroup`。 |

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|定義建置程序的輸入。 `ItemGroup` 中可能有零或多個 `Item` 項目。|

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| - | - |
| [專案](../msbuild/project-element-msbuild.md) | MSBuild 專案檔的必要根項目。 |
| [Target](../msbuild/target-element-msbuild.md) | 從 .NET Framework 3.5 開始，`ItemGroup` 項目可以出現在 `Target` 項目內部。 如需詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)。 |

## <a name="example"></a>範例

下列程式碼範例示範使用者定義的項目 (Item) 集合 `Res`，以及在 `ItemGroup` 項目 (Element) 內部宣告的 `CodeFiles`。 `Res` 項目 (Item) 集合中的每個項目 (Item)，都會包含使用者定義的子系 [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) 項目 (Element)。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Res Include = "Strings.fr.resources" >
            <Culture>fr</Culture>
        </Res>
        <Res Include = "Dialogs.fr.resources" >
            <Culture>fr</Culture>
        </Res>

        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />
        <CodeFiles Include="..\..\Resources\Constants.cs" />
    </ItemGroup>
...
</Project>
```

在簡單的專案檔中，您通常會使用單一專案 `ItemGroup` ，但您也可以使用多個 `ItemGroup` 元素。 使用多個 `ItemGroup` 元素時，專案會合並為單一 `ItemGroup` 。 例如，某些專案可能包含在匯入的檔案 `ItemGroup` 中所定義的個別元素。

ItemGroups 可以使用屬性來套用條件 `Condition` 。 在此情況下，只有在符合條件時，才會將專案新增至專案清單。 查看 [MSBuild 條件](msbuild-conditions.md)

在 `Label` 某些組建系統中，屬性是用來控制組建行為的方式。 您只能在宣告中使用它，以建立更容易理解的 MSBuild 腳本，或做為控制設定以影響組建動作。

## <a name="see-also"></a>另請參閱

- [專案檔案架構參考](../msbuild/msbuild-project-file-schema-reference.md)
- [項目](../msbuild/msbuild-items.md)
- [一般 MSBuild 專案項目](../msbuild/common-msbuild-project-items.md)
