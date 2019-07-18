---
title: ItemMetadata 元素 (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 825c6b897447a5a628d9a97e4c7e64f1427fb4d7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817667"
---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata 項目 (MSBuild)
包含使用者定義的項目中繼資料索引鍵，其中含有項目中繼資料值。 項目可能有任何數目的中繼資料索引鍵值組。

 \<Project> \<ItemGroup> \<Item>

## <a name="syntax"></a>語法

```xml
<ItemMetadataName> Item Metadata value</ItemMetadataName>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|說明|
|---------------|-----------------|
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|說明|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|使用者定義的元素，可定義建置程序的輸入。|

## <a name="text-value"></a>文字值
 可選擇使用文字值。

 此文字會指定項目中繼資料值，它可以是文字或 XML。

## <a name="example"></a>範例
 下列程式碼範例示範如何新增含有值 `fr` 的 `Culture` 中繼資料到項目 `CSFile`。

```xml
<ItemGroup>
    <CSFile Include="main.cs" >
        <Culture>fr</Culture>
    </CSFile>
</ItemGroup>
```

## <a name="see-also"></a>另請參閱
- [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)
- [項目](../msbuild/msbuild-items.md)
