---
title: choco-install
description: devinit tool choco-安裝以安裝 Chocolatey 套件。
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
ms.openlocfilehash: e30db0eea924fcbc9587593266323d81c4ff1b40
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "91006047"
---
# <a name="choco-install"></a>choco-install

此 `choco-install` 工具可用於安裝和更新 [chocolatey](https://chocolatey.org/) 套件。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具不會執行任何動作。

| 名稱                                             | 類型   | 必要 | 值                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                                                          |
| [**輸入**](#input)                              | 字串 | No       | 要取得安裝的封裝。 如需詳細資料，請參閱下列 [輸入](#input) 。                                                 |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 傳遞至工具的其他選項。 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。       |

### <a name="input"></a>輸入

`input`屬性可用來指定要安裝的封裝名稱 (例如 ' mongodb ' ) 或下列格式的設定檔路徑_packages.config_、 _. nuspec_和 _. nupkg_。 的值 `input` 將會附加至 `choco install` 命令 (例如 `choco install mongodb`) ，以及中特定的任何引數 [`additionalOptions`](#additional-options) ，以及下列) 所定義的內建 `choco` 選項 (。 [below](#built-in-options) 您可以在 [Chocolatey 封裝資源庫](https://chocolatey.org/packages)中找到套件。 使用設定檔時，您可以傳入屬性中該檔案的路徑 `input` ，例如 `"input":"packages.config"` 。

### <a name="additional-options"></a>其他選項

您可以將其他設定選項傳入作為的值 `additionalOptions` 。 這些引數是直接傳遞給所使用的引數， [`choco install`](https://chocolatey.org/docs/commands-install) 而且是在 chocolatey 檔中定義。

### <a name="built-in-options"></a>內建選項

此 `choco-install` 工具會設定一些 `choco` 命令列引數，以確保 `choco` 可執行無周邊。 以下列出這些引數，您可以在 [chocolatey 檔](https://chocolatey.org/docs/)中找到這些引數的相關檔。

| Name                  | 描述                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--是**             | 確認所有提示-選擇肯定答案而非提示。 意味 著 `--accept-license.` |
| **--沒有進度**     | 不要顯示進度-不會顯示進度百分比。                                         |
| **--skip-powershell** | 略過 PowerShell-chocolateyInstall.ps1 將不會執行。                                              |

## <a name="example-usage"></a>使用方式範例

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing packages listed in a packages.config file.",
            "tool": "choco-install",
            "input": "packages.config",
        },
        {
            "comments": "Example that will install the package 'mongodb'.",
            "tool": "choco-install",
            "input": "mongodb"
        },
        {
            "comments": "Example that will install the '4.2.7' version of 'mongodb'.",
            "tool": "choco-install",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```
