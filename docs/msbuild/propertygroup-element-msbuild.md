---
title: PropertyGroup 項目 (MSBuild) | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: da16e2042ebd74684f7775fb41bc62242592e71a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852371"
---
# <a name="propertygroup-element-msbuild"></a>PropertyGroup 元素 (MSBuild)
包含一組使用者定義的 [Property](../msbuild/property-element-msbuild.md) 項目。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案中使用的每個 `Property` 項目都必須是 `PropertyGroup` 項目的子系。  

 \<Project>  
 \<PropertyGroup>  

## <a name="syntax"></a>語法  

```xml  
<PropertyGroup Condition="'String A' == 'String B'">  
    <Property1>...</Property1>  
    <Property2>...</Property2>  
</PropertyGroup>  
```  

## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子元素和父元素。  

### <a name="attributes"></a>屬性  

|屬性|說明|  
|---------------|-----------------|  
|條件|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|  

### <a name="child-elements"></a>子元素  

|元素|說明|  
|-------------|-----------------|  
|[Property](../msbuild/property-element-msbuild.md)|選擇性項目。<br /><br /> 使用者定義的屬性名稱，其中包含屬性值。 `PropertyGroup` 項目中可能有零或多個 *Property* 項目。|  

### <a name="parent-elements"></a>父元素  

| 元素 | 說明 |
| - | - |
| [專案](../msbuild/project-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔案的必要根項目。 |

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
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)  
 [MSBuild 屬性](../msbuild/msbuild-properties.md)
