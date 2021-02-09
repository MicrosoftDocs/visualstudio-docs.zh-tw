---
title: 如何：參考 MSBuild 專案 SDK | Microsoft Docs
description: 瞭解如何使用 MSBuild 專案 Sdk，以簡化需要匯入屬性和目標的軟體發展工具組。
ms.custom: SEO-VS-2020
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e6303efce016a9e678e4c9e8aa62c91aa116e44f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914224"
---
# <a name="how-to-use-msbuild-project-sdks"></a>如何：使用 MSBuild 專案 SDK

MSBuild 15.0 引進了「專案 SDK」的概念，可簡化使用需要匯入屬性和目標的軟體發展工具組。

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

在專案評估期間，MSBuild 會在專案檔的頂端和底部加入隱含的匯入：

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

## <a name="reference-a-project-sdk"></a>參考專案 SDK

參考專案 SDK 的方式有三種：

- 使用 `<Project/>` 元素上的 `Sdk` 屬性：

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    如先前所述，會將隱含匯入新增至專案的頂端和底部。
    
    若要指定特定版本的 SDK，請將它附加至 `Sdk` 屬性：

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

- 使用最上層的 `<Sdk/>` 元素：

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   如先前所述，會將隱含匯入新增至專案的頂端和底部。
   
   不需要 `Version` 屬性。

- 在您專案中的任意位置使用 `<Import/>` 元素：

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

   當使用 `<Import/>` 元素時，您也可以指定選擇性的 `Version` 屬性。 例如，您可以指定 `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`。

## <a name="how-project-sdks-are-resolved"></a>解析專案 SDK 的方式

在評估匯入時，MSBuild 會根據您指定的名稱和版本，動態地解析專案 SDK 的路徑。  MSBuild 也有一個已註冊的 SDK 解析程式清單，這些解析程式是在您的電腦上尋找專案 Sdk 的外掛程式。 這些外掛程式包括：

- 以 NuGet 為基礎的解析程式，可查詢 NuGet 套件的設定套件摘要，以尋找符合您所指定 SDK 的識別碼和版本。

   只有在您指定了選用的版本時，此解析程式才有效。 它可用於任何自訂專案 SDK。
   
- .NET SDK 解析程式，可解析隨 [.NET sdk](/dotnet/core/sdk/)安裝的 MSBuild sdk。

   此解析程式會尋找屬於產品一部分的專案 Sdk，例如 `Microsoft.NET.Sdk` 和 `Microsoft.NET.Sdk.Web` 。
   
- 預設的解析程式，可解析使用 MSBuild 安裝的 SDK。

以 NuGet 為基礎的 SDK 解析程式支援在檔案的 [global.js](/dotnet/core/tools/global-json) 中指定版本，可讓您在單一位置（而不是在每個個別專案中）控制專案 SDK 版本：

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

在建置期間每個專案 SDK 都只能使用一個版本。 如果您參考相同專案 SDK 的兩個不同版本，MSBuild 會發出警告。 如果在檔案的 *global.js* 中指定了版本，建議您 **不要** 在專案中指定版本。

## <a name="see-also"></a>另請參閱

- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [自訂組建](../msbuild/customize-your-build.md)
- [套件、中繼套件和架構](/dotnet/core/packages)
- [適用於 .NET Core 之 csproj 格式的新增項目](/dotnet/core/tools/csproj)
