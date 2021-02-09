---
title: Property 項目 (MSBuild) | Microsoft Docs
description: 深入瞭解 MSBuild Property 元素，其中包含使用者定義的屬性名稱，以及必須指定為 PropertyGroup 元素子系的值。
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 617a6d3712b137d76334d4063f36a1b8dde1d101
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918846"
---
# <a name="property-element-msbuild"></a>Property 元素 (MSBuild)

包含使用者定義的屬性名稱和值。 MSBuild 專案中使用的每個屬性都必須指定為元素的子系 `PropertyGroup` 。

 \<Project> \<PropertyGroup>

## <a name="syntax"></a>Syntax

```xml
<Property Condition="'String A' == 'String B'">
    Property Value
</Property>
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|

### <a name="child-elements"></a>子元素

 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|屬性的群組項目。|

## <a name="text-value"></a>文字值

 可選擇使用文字值。

 此文字會指定屬性值，而且可能包含 XML。

## <a name="remarks"></a>備註

 屬性名稱只能使用 ASCII 字元。 將專案名稱放在 "`$(`" 和 "`)`" 之間，以參考專案中的屬性值。 例如， `$(builddir)\classes` 如果屬性具有值，就會解析為 *build\classes* `builddir` `build` 。 如需屬性的詳細資訊，請參閱 [MSBuild 屬性](../msbuild/msbuild-properties.md)。

## <a name="example"></a>範例

 下列程式碼會將 `Optimization` 屬性設為 `false`，而且如果 `Version` 屬性是空的，會將 `DefaultVersion` 屬性設為`1.0`。

```xml
<PropertyGroup>
    <Optimization>false</Optimization>
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>
</PropertyGroup>
```

## <a name="see-also"></a>另請參閱

- [MSBuild 屬性](../msbuild/msbuild-properties.md)
- [專案檔案架構參考](../msbuild/msbuild-project-file-schema-reference.md)
