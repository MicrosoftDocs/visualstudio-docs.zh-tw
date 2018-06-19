---
title: 如何：參考 MSBuild 專案 SDK | Microsoft Docs
ms.custom: ''
ms.date: 01/25/2018
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b595f08883023d1150612415fcdb6c50411db7e3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31569884"
---
# <a name="how-to-use-msbuild-project-sdks"></a>如何：使用 MSBuild 專案 SDK
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 15.0 版導入「專案 SDK」的概念，簡化了需要匯入屬性和目標之軟體開發套件的使用。

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```  
  
在專案的評估期間，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 在您專案的頂端和底部新增隱含的匯入：

```xml
<Project>
    <!-- Implicit top import -->
    <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>

    <!-- Implicit bottom import -->
    <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>  
```  

## <a name="referencing-a-project-sdk"></a>參考專案 SDK
 參考專案 SDK 的方式有三種

1. 使用 `<Project/>` 元素上的 `Sdk` 屬性：
    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```
    如上所述，隱含的匯入會新增到專案的頂端和底部。  `Sdk` 屬性的格式為 `Name[/Version]`，其中 Version 是選擇性的。  例如，您可以指定 `My.Custom.Sdk/1.2.3`。

2. 使用最上層的 `<Sdk/>` 元素：
    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```
   如上所述，隱含的匯入會新增到專案的頂端和底部。  不需要 `Version` 屬性。

3. 在您專案中的任意位置使用 `<Import/>` 元素：
    ```xml
    <Project>
        <PropertyGroup>
            <MyProperty>Value</MyProperty>
        </PropertyGroup>
        <Import Project="Sdk.props" Sdk="My.Custom.Sdk" />
        ...
        <Import Project="Sdk.targets" Sdk="My.Custom.Sdk" />
    </Project>
   ```
   在您的專案中明確包含匯入可讓您完全控制順序。

   當使用 `<Import/>` 元素時，您也可以指定選擇性的 `Version` 屬性。  例如，您可以指定 `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`。

## <a name="how-project-sdks-are-resolved"></a>解析專案 SDK 的方式
在評估匯入時，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 根據您指定的名稱和版本，動態地解析專案 SDK 的路徑。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 也具有已註冊之 SDK 解析程式的清單，它們是在電腦上找出專案 SDK 的外掛程式。  這些外掛程式包括：

1. 以 NuGet 為基礎的解析程式，可查詢 NuGet 套件的設定套件摘要，以尋找符合您所指定 SDK 的識別碼和版本。<br/>
   只有當您指定選擇性的版本，且它可用於任何自訂專案 SDK 時，此解析程式才會啟動。  
2. .NET CLI 解析程式，可解析使用 .NET CLI 安裝的 SDK。<br/>
   此解析程式會找出 `Microsoft.NET.Sdk` 和 `Microsoft.NET.Sdk.Web` 等屬於產品一部分的專案 SDK。
3. 預設的解析程式，可解析使用 MSBuild 安裝的 SDK。

以 NuGet 為基礎的 SDK 解析程式支援在您的 [global.json](https://docs.microsoft.com/en-us/dotnet/core/tools/global-json) 中指定版本，讓您可以在一個位置控制專案 SDK 版本，而不需要在個別的專案中指定：

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```
在建置期間每個專案 SDK 都只能使用一個版本。  如果您參考同一個專案 SDK 的兩個不同版本，MSBuild 會發出警告。  如果您的 `global.json` 中已經指定了版本，建議您**不要**再於專案中指定版本。  

## <a name="see-also"></a>請參閱  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [自訂您的組建](../msbuild/customize-your-build.md)   
