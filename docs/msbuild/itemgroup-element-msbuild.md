---
title: ItemGroup 項目 (MSBuild) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 588118bf31c5d310e947b02fda476a63d0d9df7a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573439"
---
# <a name="itemgroup-element-msbuild"></a>ItemGroup 項目 (MSBuild)
包含一組使用者定義的 [Item](../msbuild/item-element-msbuild.md) 元素。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案中使用的每個項目 (Item)，都必須指定為 `ItemGroup` 項目 (Element) 的子系。

\<Project> \<ItemGroup>

## <a name="syntax"></a>語法

```xml
<ItemGroup Condition="'String A' == 'String B'">
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

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|定義建置程序的輸入。 `ItemGroup` 中可能有零或多個 `Item` 項目。|

### <a name="parent-elements"></a>父元素

| 項目 | 描述 |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔案的必要根項目。 |
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

## <a name="see-also"></a>請參閱
- [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)
- [項目](../msbuild/msbuild-items.md)
- [通用的 MSBuild 專案項目](../msbuild/common-msbuild-project-items.md)
