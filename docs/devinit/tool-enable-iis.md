---
title: enable-iis
description: devinit tool enable-iis。
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
ms.openlocfilehash: 9b6ba2e22484850dd6079cfc7e4ab9cd68371dcb
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671923"
---
# <a name="enable-iis"></a>enable-iis

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