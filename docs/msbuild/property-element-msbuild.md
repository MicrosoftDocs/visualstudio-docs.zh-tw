---
title: Property 項目 (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f98e1cc8b3ce016580e477dfa648a493df1c1e8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31570882"
---
# <a name="property-element-msbuild"></a>Property 項目 (MSBuild)
包含使用者定義的屬性名稱和值。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案中使用的每個屬性，都必須指定為 `PropertyGroup` 項目的子系。  

 \<Project>  
 \<PropertyGroup>  

## <a name="syntax"></a>語法  

```  
<Property Condition="'String A' == 'String B'">  
    Property Value  
</Property>  
```  

## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  

### <a name="attributes"></a>屬性  

|屬性|描述|  
|---------------|-----------------|  
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|  

### <a name="child-elements"></a>子項目  
 無。  

### <a name="parent-elements"></a>父項目  

|元素|描述|  
|-------------|-----------------|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|屬性的群組項目。|  

## <a name="text-value"></a>文字值  
 可選擇使用文字值。  

 此文字會指定屬性值，而且可能包含 XML。  

## <a name="remarks"></a>備註  
 屬性名稱只能使用 ASCII 字元。 將專案名稱放在 "`$(`" 和 "`)`" 之間，以參考專案中的屬性值。 例如，如果 `builddir` 屬性值為 `build`，即會將 `$(builddir)\classes` 解析為 "build\classes"。 如需屬性的詳細資訊，請參閱 [MSBuild 屬性](../msbuild/msbuild-properties.md)。  

## <a name="example"></a>範例  
 下列程式碼會將 `Optimization` 屬性設為 `false`，而且如果 `Version` 屬性是空的，會將 `DefaultVersion` 屬性設為`1.0`。  

```xml  
<PropertyGroup>  
    <Optimization>false</Optimization>  
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>  
</PropertyGroup>  
```  

## <a name="see-also"></a>請參閱
[MSBuild 屬性](../msbuild/msbuild-properties.md)  
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)
