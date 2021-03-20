---
title: enable-iis
description: devinit tool enable-iis。
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
ms.openlocfilehash: eecdc2a020117b7345682068cb27509df805ff9b
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671627"
---
# <a name="enable-iis"></a>enable-iis

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

此 `enable-iis` 工具可用來啟用 iis 功能，並安裝 [ASP.NET Core 模組](/aspnet/core/host-and-deploy/aspnet-core-module) ，以使用 iis 進行 ASP.NET 開發。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                               |
| [**輸入**](#input)                              | 字串 | No       | 未使用。                                                                           |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 未使用。                                                                           |

### <a name="input"></a>輸入

未使用。

### <a name="additional-options"></a>其他選項

未使用。

### <a name="default-behavior"></a>預設行為

此工具的預設行為 `enable-iis` 是啟用 iis 功能： iis-web 伺服器、Iis iis-webserverrole、iis-websocket 和 IIS WebAuthentication，然後安裝包含 ASP.NET Core 模組的最新版 ASP.NET 裝載套件組合。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `enable-iis` `.devinit.json` 。

#### <a name="devinitjson-that-will-enable-iis-development"></a>.devinit.js，將會啟用 IIS 開發：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "tool": "enable-iis"
        },
    ]
}
```