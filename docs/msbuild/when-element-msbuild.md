---
title: When 元素 (MSBuild) | Microsoft Docs
description: 深入瞭解 MSBuild When 元素，這會指定要選取之 Choose 元素的可能程式碼區塊。
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#When
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <When> Element [MSBuild]
- When Element [MSBuild]
ms.assetid: eb27de6f-4e71-4e87-87e2-d93f7bf5899c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 36d96eacc0fbc88a3fcf082493e064a77c5c403a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933813"
---
# <a name="when-element-msbuild"></a>When 元素 (MSBuild)

指定 `Choose` 元素的可能程式碼區塊以選取。

 \<Project> \<Choose>
 \<When>
 \<Choose>
... \<Otherwise>
 \<Choose>
...

## <a name="syntax"></a>Syntax

```xml
<When Condition="'StringA'=='StringB'">
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Choose>... </Choose>
</When>
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|條件|必要屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[選擇](../msbuild/choose-element-msbuild.md)|選擇性項目。<br /><br /> 評估子元素，以選取要執行的一個程式碼區段。 `Choose` 元素中可能有零個或多個 `When` 元素。|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|選擇性項目。<br /><br /> 包含一組使用者定義的 [Item](../msbuild/item-element-msbuild.md) 元素。 `ItemGroup` 元素中可能有零個或多個 `When` 元素。|
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|選擇性項目。<br /><br /> 包含一組使用者定義的 [Property](../msbuild/property-element-msbuild.md) 項目。 `When` 元素中可能有零個或多個 `PropertyGroup` 元素。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[Choose 項目 (MSBuild)](../msbuild/choose-element-msbuild.md)|評估子元素，以選取要執行的一個程式碼區段。|

## <a name="remarks"></a>備註

 如果 `Condition` 屬性評估為 true，則會執行 `When` 元素的子元素 `ItemGroup` 和 `PropertyGroup`，且略過所有後續的 `When` 元素。

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

- [條件式結構](../msbuild/msbuild-conditional-constructs.md)
- [專案檔案架構參考](../msbuild/msbuild-project-file-schema-reference.md)
