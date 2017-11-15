---
title: "Property 項目 (MSBuild) | Microsoft Docs"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
caps.latest.revision: "17"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: e931468b27807a99e86249008718faf4e044cbd7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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
 下列章節說明屬性、子項目和父項目。  

### <a name="attributes"></a>屬性  

|屬性|描述|  
|---------------|-----------------|  
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|  

### <a name="child-elements"></a>子項目  
 無。  

### <a name="parent-elements"></a>父項目  

|項目|描述|  
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

## <a name="see-also"></a>另請參閱
[MSBuild 屬性](../msbuild/msbuild-properties.md)  
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)
