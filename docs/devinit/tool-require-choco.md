---
title: require-choco
description: devinit 工具需要-choco。
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
ms.openlocfilehash: 68e944813e7084b13c15058e4f66aef4aadb9494
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900367"
---
# <a name="require-choco"></a>require-choco

您 `require-choco` 可以使用此工具來安裝 [chocolatey](https://chocolatey.org/)。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                      |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                      |
| [**輸入**](#input)                              | 字串 | No       | 未使用。 如需詳細資料，請參閱下列 [輸入](#input) 。                           |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 未使用。 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。 |

### <a name="input"></a>輸入

未使用。

### <a name="additional-options"></a>其他選項

未使用。

### <a name="default-behavior"></a>預設行為

工具的預設行為 `require-choco` 是安裝 chocolatey，並將它新增至 `PATH` 。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `require-choco` `.devinit.json` 。

#### <a name="devinitjson-that-will-install-chocolatey"></a>.devinit.js將會安裝 chocolatey：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-choco"
        }
    ]
}
```