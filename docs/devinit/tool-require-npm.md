---
title: require-npm
description: devinit 工具需要-npm。
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
ms.openlocfilehash: e28a1f896904c89a4553f18c73324293ea468ee6
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672122"
---
# <a name="require-npm"></a>require-npm

此 `require-npm` 工具是用來安裝 [NPM](https://www.npmjs.com/)。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                                       |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                                       |
| [**輸入**](#input)                              | 字串 | 是      | 指定 NPM 版本。 如需詳細資料，請參閱下列 [輸入](#input) 。                           |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 未使用。 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。                  |

### <a name="input"></a>輸入

`input`屬性是用來指定 npm 版本。

### <a name="additional-options"></a>其他選項

未使用的。

### <a name="default-behavior"></a>預設行為

此工具的預設行為 `require-nodejs` 是安裝最新的 LTS 版本的 npm。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `require-npm` `.devinit.json` 。 

#### <a name="devinitjson-that-will-install-the-lts-of-npm"></a>.devinit.js將會安裝 npm 的 LTS：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-npm"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-npm"></a>.devinit.js，會安裝特定版本的 npm：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-npm",
            "input": "6.14.6"
        }
    ]
}
```