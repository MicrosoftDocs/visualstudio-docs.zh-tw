---
title: windowsfeature-enable
description: devinit tool，啟用。
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
ms.openlocfilehash: b24f118613fa1004275702ad27a789ec16e6a347
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874516"
---
# <a name="windowsfeature-enable"></a>windowsfeature-enable

此 `windowsfeature-enable` 工具可用來啟用 Windows 功能。

## <a name="usage"></a>使用方式

| 名稱                                             | 類型   | 必要 | 值                                                                    |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                    |
| [**輸入**](#input)                              | 字串 | 是      | 要安裝的 Windows 功能。 如需詳細資料，請參閱下列 [輸入](#input) 。   |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。         |

### <a name="input"></a>輸入

`input`屬性應該是 `name` `windows feature` 要安裝的。 您可以藉由執行 PowerShell cmd 來找到可用功能的清單 `Get-WindowsFeature` 。

### <a name="additional-options"></a>Additional-Options

無。

### <a name="default-behavior"></a>預設行為

工具的預設行為 `windowsfeature-enable` 是在需要時發生錯誤 `input` 。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `windowsfeature-enable` `.devinit.json` 。

#### <a name="devinitjson-that-will-install-iis"></a>.devinit.js將會安裝 IIS：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "web-server",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-net-framework"></a>將會安裝 .NET Framework 的 .devinit.js：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "net-framework-features"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-net-framework-45"></a>.devinit.js將會安裝 .NET Framework 4.5：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "net-framework-45-features"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-windows-subsystem-for-linux-20"></a>.devinit.js將會安裝 Windows 子系統 Linux 版2.0：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "Microsoft-Windows-Subsystem-Linux"
        }
    ]
}
```
