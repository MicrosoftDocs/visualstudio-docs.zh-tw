---
title: 啟用-iis
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
ms.openlocfilehash: 245ea76f988b9a9e320a51ba6b2df01382668cc0
ms.sourcegitcommit: 417ea66a8b07ec102ece2fa00e07b88edc404c00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91127823"
---
# <a name="enable-iis"></a>啟用-iis

此 `enable-iis` 工具可用來啟用 iis 功能，並安裝 [ASP.NET Core 模組](https://docs.microsoft.com/aspnet/core/host-and-deploy/aspnet-core-module) ，以使用 iis 進行 ASP.NET 開發。

## <a name="usage"></a>使用量

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

```json
{
    "$schema": "./devinit.schema-2.0.json",
    "run": [
        {
            "comments": "Example that will enable IIS features and install the latest ASP.NET hosting bundle.",
            "tool": "enable-iis"
        },
    ]
}
```
