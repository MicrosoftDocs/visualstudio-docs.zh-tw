---
title: （啟用）
description: devinit tool，啟用。
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 679f8599516cc63aa56d327f69164612db8bb3ca
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810397"
---
# <a name="windowsfeature-enable"></a>（啟用）

此 `windowsfeature-enable` 工具可用來啟用 Windows 功能。

## <a name="usage"></a>使用方式

| 名稱                                             | 類型   | 必要 | 值                                                                    |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                    |
| [**輸入**](#input)                              | 字串 | 是      | 要安裝的 Windows 功能。 如需詳細資料，請參閱下列 [輸入](#input) 。   |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。         |

### <a name="input"></a>輸入

`input`屬性應該是 `name` `windows feature` 要安裝的。 您可以藉由執行 PowerShell cmd 來找到可用功能的清單 `Get-WindowsFeature` 。

### <a name="additional-options"></a>其他選項

無。

### <a name="default-behavior"></a>預設行為

此工具的預設行為 `windowsfeature-enable` 是「錯誤」（ `input` required）。

## <a name="example-usage"></a>使用方式範例

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs IIS.",
            "tool": "windowsfeature-enable",
            "input": "web-server",
        },
        {
            "comments": "Installs the .NET Framework 3.5.",
            "tool": "windowsfeature-enable",
            "input": "net-framework-features"
        },
        {
            "comments": "Installs the .NET Framework 4.5.",
            "tool": "windowsfeature-enable",
            "input": "net-framework-45-features"
        },
        {
            "comments": "Installs Windows Subsystem for Linux 2.0.",
            "tool": "windowsfeature-enable",
            "input": "Microsoft-Windows-Subsystem-Linux"
        }
    ]
}
```
