---
title: windowsfeature-disable
description: devinit tool 的-disable。
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: e48ba0a288aec76588e3d984d4c1577e053e35ae
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442156"
---
# <a name="windowsfeature-disable"></a>windowsfeature-disable

此 `windowsfeature-disable` 工具可用來取得 Windows 功能。

## <a name="usage"></a>使用方式

| 名稱                                             | 類型   | 必要 | 值                                                                  |
|--------------------------------------------------|--------|----------|------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                  |
| [**輸入**](#input)                              | 字串 | 是      | 要安裝的 Windows 功能。 如需詳細資料，請參閱下列 [輸入](#input) 。 |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。       |

### <a name="input"></a>輸入

`input`屬性應該是 `name` 要停用的 `windows feature` 。

### <a name="additional-options"></a>Additional-Options

無。

### <a name="default-behavior"></a>預設行為

工具的預設行為 `windowsfeature-disable` 是在需要時發生錯誤 `input` 。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `windowsfeature-disable` `.devinit.json` 。

#### <a name="devinitjson-that-will-disable-a-specified-feature"></a>.devinit.js將停用指定的功能：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-windowsfeature",
            "input": "web-server",
        }
    ]
}
```
