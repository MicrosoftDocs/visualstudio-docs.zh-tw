---
title: Otherwise 項目 (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Otherwise
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
ms.assetid: de3997e9-1595-4263-a886-95530b56a319
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb9f6056b83c7701e4d0e5e6eed72bbba1da778d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895788"
---
# <a name="otherwise-element-msbuild"></a>Otherwise 元素 (MSBuild)
指定只有當所有 `When` 項目的條件評估為 `false` 時，才需執行的程式碼區塊。  

 \<Project>  
 \<Choose>  
 \<When>  
 \<Choose>  
 ...  
 \<Otherwise>  
 \<Choose>  
 ...  

## <a name="syntax"></a>語法  

```xml  
<Otherwise>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</Otherwise>  
```  

## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子元素和父元素。  

### <a name="attributes"></a>屬性  
 無。  

### <a name="child-elements"></a>子元素  

|元素|說明|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|選擇性項目。<br /><br /> 評估子項目，以選取一個要執行的程式碼區段。 `Otherwise` 元素中可能有零個或多個 `Choose` 元素。|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|選擇性項目。<br /><br /> 包含一組使用者定義的 [Item](../msbuild/item-element-msbuild.md) 項目。 `Otherwise` 項目中可能有零或多個 `ItemGroup` 項目。|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|選擇性項目。<br /><br /> 包含一組使用者定義的 [Property](../msbuild/property-element-msbuild.md) 項目。 `Otherwise` 元素中可能有零個或多個 `PropertyGroup` 元素。|  

### <a name="parent-elements"></a>父元素  

|元素|說明|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|評估子元素，以選取要執行的一個程式碼區段。|  

## <a name="remarks"></a>備註  
 `Choose` 項目中可能只有一個 `Otherwise` 項目，而且它必須是最後一個項目。  

 `Choose`、`When` 和 `Otherwise` 元素會一起用來提供選取一個程式碼區段的方式，以執行一些可能的替代方案。 如需詳細資訊，請參閱[條件式建構](../msbuild/msbuild-conditional-constructs.md)。  

## <a name="example"></a>範例  
 下列專案使用 `Choose` 元素來選取 `When` 元素中要設定的屬性值集合。 如果兩個 `When` 元素的 `Condition` 屬性都評估為 `false`，則 `Otherwise` 元素中的屬性值已設定。  

```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='debug' ">  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <DebugType>full</DebugType>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\Debug\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
            <ItemGroup>  
                <Compile Include="UnitTesting\*.cs" />  
                <Reference Include="NUnit.dll" />  
            </ItemGroup>  
        </When>  
        <When Condition=" '$(Configuration)'=='retail' ">  
            <PropertyGroup>  
                <DebugSymbols>false</DebugSymbols>  
                <Optimize>true</Optimize>  
                <OutputPath>.\bin\Release\</OutputPath>  
                <DefineConstants>TRACE</DefineConstants>  
            </PropertyGroup>  
        </When>  
        <Otherwise>  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\$(Configuration)\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
        </Otherwise>  
        </Choose>  
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
</Project>  
```  

## <a name="see-also"></a>另請參閱  
 [條件式建構](../msbuild/msbuild-conditional-constructs.md)   
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)
