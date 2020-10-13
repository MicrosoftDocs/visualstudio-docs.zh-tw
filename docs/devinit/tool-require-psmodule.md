---
title: require-psmodule
description: devinit 工具需要-psmodule。
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
ms.openlocfilehash: b855d8f3e9827d7b88f6d95bdf426cfb470b2bda
ms.sourcegitcommit: 3e05bd4bfac6f0b8b3534d8c013388f67e288651
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91959783"
---
# <a name="require-psmodule"></a>require-psmodule

此 `require-psmodule` 工具可用來透過[安裝模組](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true)從[PowerShell 資源庫](https://www.powershellgallery.com/)安裝[powershell 模組](/powershell/scripting/developer/module/understanding-a-windows-powershell-module?view=powershell-7&preserve-view=true)，以便在 powershell 腳本中使用。

> [!TIP]
> 安裝模組之後，仍然需要使用 [import-module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true)將其匯入腳本。

## <a name="usage"></a>使用量

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                                   |
| [**輸入**](#input)                              | 字串 | 是      | 要安裝的套件 (s) 。 如需詳細資料，請參閱下列 [輸入](#input) 。                       |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 未使用。 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。              |

### <a name="input"></a>輸入

`input`屬性應該是 `Name` 要安裝之 PowerShell 模組的。 您可以藉由搜尋 [PowerShell 資源庫](https://www.powershellgallery.com/)，找到可用的 PowerShell 模組清單。

### <a name="additional-options"></a>其他選項

其他選項會直接傳遞至 [Install 模組](/powershell/module/powershellget/install-module?preserve-view=true&view=powershell-7) 命令，並記載于 [Microsoft Docs](/powershell/module/powershellget/install-module?preserve-view=true&view=powershell-7)上。

### <a name="default-behavior"></a>預設行為

工具的預設行為 `require-psmodule` 是在需要時發生錯誤 `input` 。

## <a name="builtin-options"></a>內建選項

此 `require-psmodule` 工具會設定一些 `Install-Module` 命令列引數，以確保 `Install-Module` 可執行無周邊。 以下列出這些引數，您可以在 [安裝模組](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true)中找到這些引數的相關檔。

| Name         | 描述                                                                                                                                                                                                                                                                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **-Force**   | 安裝模組並覆寫有關模組安裝衝突的警告訊息。 如果電腦上已有相同名稱的模組，則強制允許安裝多個版本。 如果存在具有相同名稱和版本的現有模組，將會覆寫模組。 Force 和 AllowClobber 可以在 Install-Module 命令中一起使用。 |
| **-WhatIf**  | -傳遞命令的試執行時，會新增 WhatIf 旗標 `devinit` 。                                                                                                                                                                                                                                                                                                       |
| **-Verbose** | -傳遞命令的詳細資訊時，會加入詳細資訊旗標 `devinit` 。                                                                                                                                                                                                                                                                                                      |


## <a name="example-usage"></a>使用方式範例

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs the PowerShellGet module.",
            "tool": "require-psmodule",
            "input": "PowerShellGet",
        },
        {
            "comments": "Installs the PowerShellGet module from a specific repository.",
            "tool": "require-psmodule",
            "input": "PowerShellGet",
            "additionalOptions": "-Repository PSGallery"
        }
    ]
}
```