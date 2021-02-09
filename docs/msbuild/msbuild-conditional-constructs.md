---
title: MSBuild 條件式建構 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 Choose、When 和其他專案，提供條件式處理的機制。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10b26e9bdc0c632f924a29cd2ad09c21f8048d31
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919134"
---
# <a name="msbuild-conditional-constructs"></a>MSBuild 條件式建構

MSBuild 提供了一種機制，可使用 [Choose](../msbuild/choose-element-msbuild.md)、 [When](../msbuild/when-element-msbuild.md)和 [其他](../msbuild/otherwise-element-msbuild.md) 專案進行/或處理。

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

在此範例中，會使用編譯器常數上的條件 `DEFINED_CONSTANT` 。 這些會包含在 `DefinedConstants` 屬性中。 正則運算式會用來比對分號分隔清單中的精確常數。

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
- [當元素 (MSBuild 時) ](../msbuild/when-element-msbuild.md)
- [Otherwise 元素 (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
