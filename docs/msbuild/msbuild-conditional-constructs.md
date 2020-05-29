---
title: MSBuild 條件式建構 | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7d6693a24d208cab6bd3b58ce16dcba8a32b190
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184285"
---
# <a name="msbuild-conditional-constructs"></a>MSBuild 條件式建構

MSBuild 提供一種機制，可使用[Choose](../msbuild/choose-element-msbuild.md)、 [When](../msbuild/when-element-msbuild.md)和[其他](../msbuild/otherwise-element-msbuild.md)專案來進行/或處理。

## <a name="use-the-choose-element"></a>使用 Choose 元素

 `Choose` 項目包含一系列的 `When` 項目與 `Condition` 屬性，其會按由上到下的順序進行測試，直到其中一個項目評估為 `true` 為止。 如果有一個以上的 `When` 項目評估為 `true`，則只會使用第一個項目。 如果 `When` 項目上沒有任何條件評估為 `true`，則會評估 `Otherwise` 項目 (如果有的話)。

 `Choose` 項目可以作為 `Project`、`When` 和 `Otherwise` 項目的子項目。 `When` 和 `Otherwise` 項目可以有 `ItemGroup`、`PropertyGroup` 或 `Choose` 子項目。

## <a name="example"></a>範例

 下列範例使用 `Choose` 和 `When` 項目來進行二選一處理。 專案的屬性與項目會依據 `Configuration` 屬性的值而設定。

```xml
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

在此範例中，會使用編譯器常數的條件 `DEFINED_CONSTANT` 。 這些包含在屬性中 `DefinedConstants` 。 正則運算式會用來比對以分號分隔之清單中的確切常數。

```xml
<Choose>
   <When Condition="$([System.Text.RegularExpressions.Regex]::IsMatch(
         $(DefineConstants), '^(.*;)*DEFINED_CONSTANT(;.*)*$'))">
      <!-- When DEFINED_CONSTANT is defined. -->
   </When>
   <!-- other conditions -->
</Choose>
```

## <a name="see-also"></a>另請參閱

- [Choose 項目 (MSBuild)](../msbuild/choose-element-msbuild.md)
- [When 元素（MSBuild）](../msbuild/when-element-msbuild.md)
- [Otherwise 元素 (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
