---
title: PropertyGroup 項目 (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
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
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6590464b78d6b5452ce266d701aefc0f739185b3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155941"
---
# <a name="propertygroup-element-msbuild"></a>PropertyGroup 項目 (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

包含一組使用者定義的 [Property](../msbuild/property-element-msbuild.md) 項目。 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 專案中使用的每個 `Property` 項目都必須是 `PropertyGroup` 項目的子系。  
  
 \<Project>  
 \<PropertyGroup>  
  
## <a name="syntax"></a>語法  
  
```  
<PropertyGroup Condition="'String A' == 'String B'">  
    <Property1>...</Property1>  
    <Property2>...</Property2>  
</PropertyGroup>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|條件|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|說明|  
|-------------|-----------------|  
|[Property](../msbuild/property-element-msbuild.md)|選擇性項目。<br /><br /> 使用者定義的屬性名稱，其中包含屬性值。 `PropertyGroup` 項目中可能有零或多個 *Property* 項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|說明|  
|-------------|-----------------|  
|[專案](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 專案檔案的必要根項目。|  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何根據條件設定屬性。 在此範例中，如果 `CompileConfig` 屬性的值為 `DEBUG`，則會在 `PropertyGroup` 項目內設定 `Optimization`、`Obfuscate` 及 `OutputPath` 屬性。  
  
```  
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >  
    <Optimization>false</Optimization>  
    <Obfuscate>false</Obfuscate>  
    <OutputPath>$(OutputPath)\debug</OutputPath>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>另請參閱  
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)  
 [MSBuild 屬性](msbuild-properties1.md)
