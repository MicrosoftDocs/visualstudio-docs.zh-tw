---
title: dotnet-toolinstall
description: devinit tool dotnet-toolinstall。
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
ms.openlocfilehash: 4daa3722abd169c03656adec39aafc29d5e7e435
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671634"
---
# <a name="dotnet-toolinstall"></a>dotnet-toolinstall

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

此 `dotnet-toolinstall` 工具是用來透過命令安裝 [.Net Core 工具](https://dotnet.microsoft.com/) `dotnet tool update` 。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                 |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                 |
| [**輸入**](#input)                              | 字串 | Yes      | 要安裝的 .NET Core 工具。 如需詳細資料，請參閱下列 [輸入](#input) 。 |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。      |

### <a name="input"></a>輸入

`input`屬性可用來指定要安裝的 .Net Core 工具。 中有一份非官方的工具清單 [https://github.com/natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) 。

### <a name="additional-options"></a>其他選項

您可以將其他設定選項傳入作為的值 `additionalOptions` 。 這些引數是命令所使用之引數的直接傳遞 [`dotnet tool update`](/dotnet/core/tools/global-tools#update-a-tool) 。

此 `dotnet tool update` 命令可用來安全地處理已安裝工具的情況。

### <a name="default-behavior"></a>預設行為

工具的預設行為 `dotnet-toolinstall` 是在需要時發生錯誤 `input` 。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `dotnet-toolinstall` `.devinit.json` 。

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool"></a>.devinit.js將會安裝 dotnet 追蹤工具：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool-as-a-global-tool"></a>.devinit.js，會將 dotnet 追蹤工具安裝為通用工具：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace",
            "additionalOptions": "--global"
        }
    ]
}
```