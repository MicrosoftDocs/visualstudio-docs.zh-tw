---
title: require-dotnetcoresdk
description: devinit 工具需要-dotnetcoresdk。
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 5c5b68b663d6ee4cd0294aa77bd89c2e778f8d2b
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399603"
---
# <a name="require-dotnetcoresdk"></a>require-dotnetcoresdk

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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest or, if present, the SDK version from a global.json file.",
            "tool": "require-dotnetcoresdk"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0"
        },
        {
            "comments": "Example that will install a specific version and the aspnetcore runtime.",
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0",
            "additionalOptions": "-Runtime aspnetcore"
        },
        {
            "comments": "Example that will install in a specific directory.",
            "tool": "require-dotnetcoresdk",
            "additionalOptions": "-InstallDir \"C:\\Program Files\\dotnet\""
        }
    ]
}
```