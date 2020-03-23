---
title: 如何：參考 MSBuild 專案 SDK | Microsoft Docs
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74ccc29417cdee7a9f93c39509c0f7d06a5c72ff
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "76826467"
---
# <a name="how-to-use-msbuild-project-sdks"></a>如何：使用 MSBuild 專案 SDK

MSBuild 15.0 引入了"專案 SDK"的概念，它簡化了使用需要導入屬性和目標的軟體發展工具組。

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

在評估專案期間，MSBuild 在專案檔案的頂部和底部添加了隱式導入：

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

    如前所述，隱式導入將添加到專案的頂部和底部。
    
    要指定 SDK 的特定版本，請將其追加到`Sdk`屬性：

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

    > [!NOTE]
    > 這是目前在 Visual Studio for Mac 中參考專案 SDK 的唯一方法。

- 使用最上層的 `<Sdk/>` 元素：

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   如前所述，隱式導入將添加到專案的頂部和底部。
   
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

評估導入時，MSBuild 會根據指定的名稱和版本動態解析到專案 SDK 的路徑。  MSBuild 還具有已註冊的 SDK 解析器清單，該解析器是查找電腦上專案 SDK 的外掛程式。 這些外掛程式包括：

- 以 NuGet 為基礎的解析程式，可查詢 NuGet 套件的設定套件摘要，以尋找符合您所指定 SDK 的識別碼和版本。

   僅當指定了可選版本時，此解析器才處於活動狀態。 它可用於任何自訂專案 SDK。
   
- .NET CLI 解析器，用於解析與[.NET CLI](/dotnet/core/tools/)一起安裝的 SDK。

   此解析器定位專案 SDK，例如`Microsoft.NET.Sdk`和`Microsoft.NET.Sdk.Web`是產品的一部分。
   
- 預設的解析程式，可解析使用 MSBuild 安裝的 SDK。

基於 NuGet 的 SDK 解析器支援在[global.json](/dotnet/core/tools/global-json)檔中指定版本，允許您在一個位置而不是在每個單個專案中控制專案 SDK 版本：

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

在建置期間每個專案 SDK 都只能使用一個版本。 如果引用同一專案 SDK 的兩個不同版本，MSBuild 會發出警告。 如果在*global.json*檔中指定了版本，則建議**不要**在專案中指定版本。

## <a name="see-also"></a>另請參閱

- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [自訂您的組建](../msbuild/customize-your-build.md)
- [套件、中繼套件和架構](/dotnet/core/packages)
- [適用於 .NET Core 之 csproj 格式的新增項目](/dotnet/core/tools/csproj)
