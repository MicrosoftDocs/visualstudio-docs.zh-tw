---
title: PropertyGroup 項目 (MSBuild) | Microsoft Docs
description: 瞭解 MSBuild PropertyGroup 元素，其中包含一組使用者定義的屬性元素。
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#PropertyGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <PropertyGroup> element [MSBuild]
- PropertyGroup element [MSBuild]
ms.assetid: ff1e6c68-b9a1-4263-a1ce-dc3b829a64d4
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5182708e848587439795f5d6c04d87382b36f84a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931990"
---
# <a name="propertygroup-element-msbuild"></a>PropertyGroup 元素 (MSBuild)

包含一組使用者定義的 [Property](../msbuild/property-element-msbuild.md) 項目。 `Property`MSBuild 專案中使用的每個專案都必須是元素的子項目 `PropertyGroup` 。

 \<Project> \<PropertyGroup>

## <a name="syntax"></a>Syntax

```xml
<PropertyGroup Condition="'String A' == 'String B'">
    <Property1>...</Property1>
    <Property2>...</Property2>
</PropertyGroup>
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|條件|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[屬性](../msbuild/property-element-msbuild.md)|選擇性項目。<br /><br /> 使用者定義的屬性名稱，其中包含屬性值。 `PropertyGroup` 項目中可能有零或多個 *Property* 項目。|

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| - | - |
| [專案](../msbuild/project-element-msbuild.md) | MSBuild 專案檔的必要根項目。 |

## <a name="example"></a>範例

 下列程式碼範例示範如何根據條件設定屬性。 在此範例中，如果 `CompileConfig` 屬性的值為 `DEBUG`，則會在 `PropertyGroup` 項目內設定 `Optimization`、`Obfuscate` 及 `OutputPath` 屬性。

```xml
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >
    <Optimization>false</Optimization>
    <Obfuscate>false</Obfuscate>
    <OutputPath>$(OutputPath)\debug</OutputPath>
</PropertyGroup>
```

## <a name="see-also"></a>另請參閱

- [專案檔案架構參考](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild 屬性](../msbuild/msbuild-properties.md)
