---
title: MSBuild 條件式建構 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
- conditional constructs [MSBuild]
- MSBuild, conditional constructs
- <When> Element [MSBuild]
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
- When Element [MSBuild]
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b7b22f63d5d3d6e0b1f7789561029bbfbfb4cdf4
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59667504"
---
# <a name="msbuild-conditional-constructs"></a>MSBuild 條件式建構
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 提供搭配使用 [Choose](../msbuild/choose-element-msbuild.md)、[When](../msbuild/when-element-msbuild.md) 和 [Otherwise](../msbuild/otherwise-element-msbuild.md) 項目的二選一處理機制。  
  
## <a name="using-the-choose-element"></a>使用 Choose 項目  
 `Choose` 項目包含一系列的 `When` 項目與 `Condition` 屬性，其會按由上到下的順序進行測試，直到其中一個項目評估為 `true` 為止。 如果有一個以上的 `When` 項目評估為 `true`，則只會使用第一個項目。 如果 `When` 項目上沒有任何條件評估為 `true`，則會評估 `Otherwise` 項目 (如果有的話)。  
  
 `Choose` 項目可以作為 `Project`、`When` 和 `Otherwise` 項目的子項目。 `When` 和 `Otherwise` 項目可以有 `ItemGroup`、`PropertyGroup` 或 `Choose` 子項目。  
  
## <a name="example"></a>範例  
 下列範例使用 `Choose` 和 `When` 項目來進行二選一處理。 專案的屬性與項目會依據 `Configuration` 屬性的值而設定。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='Debug' ">  
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
    </Choose>  
    <!-- Rest of Project -->  
</Project>  
```  
  
## <a name="see-also"></a>請參閱  
 [Choose 項目 (MSBuild)](../msbuild/choose-element-msbuild.md)   
 [When 項目 (MSBuild)](../msbuild/when-element-msbuild.md)   
 [Otherwise 項目 (MSBuild)](../msbuild/otherwise-element-msbuild.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)
