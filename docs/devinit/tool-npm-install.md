---
title: npm-install
description: devinit tool npm-安裝。
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
ms.openlocfilehash: 21630f5dbc80294547be33ab4a82bdf286a0b08f
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671903"
---
# <a name="npm-install"></a>npm-install

此 `npm-install` 工具可用於安裝 [NPM](https://www.npmjs.com/) 套件。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具不會執行任何動作。

| 名稱                                             | 類型   | 必要 | 值                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                                                          |
| [**輸入**](#input)                              | 字串 | 是      | 要取得安裝的封裝。 如需詳細資料，請參閱下列 [輸入](#input) 。                                                 |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 傳遞至工具的其他選項。 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。       |

### <a name="input"></a>輸入

`input`屬性可用來指定要安裝 (的封裝名稱，例如 ' mongo ' ) 。

### <a name="additional-options"></a>其他選項

您可以將其他設定選項傳入作為的值 `additionalOptions` 。 這些引數可直接傳遞至 [npm install](https://docs.npmjs.com/cli/install)所使用的引數。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `npm-install` `.devinit.json` 。 

#### <a name="devinitjson-that-will-install-mongo"></a>.devinit.js將會安裝 mongo：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "npm-install",
            "input": "mongo",
        }
    ]
}
```
