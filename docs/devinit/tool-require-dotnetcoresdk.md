---
title: require-dotnetcoresdk
description: devinit 工具需要-dotnetcoresdk。
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 1963ad8dfe1bd31eb3f98ec6fdf57524a274cfb6
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671788"
---
# <a name="require-dotnetcoresdk"></a>require-dotnetcoresdk

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

此 `require-dotnetcoresdk` 工具是用來透過[dotnet](/dotnet/core/tools/dotnet-install-script)安裝腳本安裝[.NET Core SDK](https://dotnet.microsoft.com/)和共用執行時間。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                               |
| [**輸入**](#input)                              | 字串 | No       | 要安裝的 .NET Core SDK 版本。 如需詳細資料，請參閱下列 [輸入](#input) 。 |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。                    |

### <a name="input"></a>輸入

`input`屬性可用來指定要安裝的 .NET Core SDK 版本。 您可以在 [dotnet 核心網站](https://dotnet.microsoft.com/download/dotnet-core)上找到版本清單。

### <a name="additional-options"></a>其他選項

您可以將其他設定選項傳入作為的值 `additionalOptions` 。 這些引數是直接傳遞給 [dotnet 安裝](/dotnet/core/tools/dotnet-install-script) 腳本中使用的引數。 如需可用參數的詳細資訊，請參閱[dotnet-安裝](/dotnet/core/tools/dotnet-install-script)腳本[檔](/dotnet/core/tools/dotnet-install-script)。 使用時 `additionalOptions` ，請務必使用 PowerShell 引數名稱和格式。

> [!NOTE]
> 包含空格的引數的任何額外值都必須包含一組額外的轉義引號 (使用反斜線) 。 您可以使用中的 [範例](#example-usage) 使用方式來看到範例 `-InstallDir` 。

### <a name="default-behavior"></a>預設行為

工具的預設行為 `require-dotnetcoresdk` 是在 `global.json` 目前的工作目錄中安裝 [ (檔) ](/dotnet/core/tools/global-json?tabs=netcore3x) 檔案中指定的 .NET Core SDK 版本。 如果找不到任何檔案 `global.json` ，則 `require-dotnetcoresdk` 會安裝最新版本的 .NET Core SDK 和共用執行時間。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `require-dotnetcoresdk` `.devinit.json` 。

#### <a name="devinitjson-that-will-install-the-latest-version-of-net-core"></a>.devinit.js將會安裝最新版本的 .NET Core：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-net-core"></a>.devinit.js在上會安裝特定版本的 .NET Core：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-net-core-and-aspnet-core"></a>.devinit.js將會安裝特定版本的 .NET Core 和 ASP.NET Core：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0",
            "additionalOptions": "-Runtime aspnetcore"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-net-core-in-a-specific-directory"></a>.devinit.js，會在特定目錄中安裝 .NET Core：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "additionalOptions": "-InstallDir \"C:\\Program Files\\dotnet\""
        }
    ]
}
```