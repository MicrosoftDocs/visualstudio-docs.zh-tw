---
title: choco-install
description: devinit tool choco-安裝以安裝 Chocolatey 套件。
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
ms.openlocfilehash: 386b41dd7f1b19d223703570b0423de0855e983a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904804"
---
# <a name="choco-install"></a>choco-install

此 `choco-install` 工具可用於安裝和更新 [chocolatey](https://chocolatey.org/) 套件。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具不會執行任何動作。

| 名稱                                             | 類型   | 必要  | 值                                                                                                          |
|--------------------------------------------------|--------|-----------|----------------------------------------------------------------------------------------------------------------|
| **評論**                                     | 字串 | No        | 選擇性批註屬性。 未使用。                                                                          |
| [**輸入**](#input)                              | 字串 | 是       | 要取得安裝的封裝。 如需詳細資料，請參閱下列 [輸入](#input) 。                                                 |
| [**additionalOptions**](#additional-options)     | 字串 | No        | 傳遞至工具的其他選項。 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。       |

### <a name="input"></a>輸入

`input`屬性可用來指定要安裝的封裝名稱 (例如 ' mongodb ' ) 或下列格式的設定檔路徑 _packages.config_、 _. nuspec_ 和 _. nupkg_。 的值 `input` 將會附加至 `choco install` 命令 (例如 `choco install mongodb`) ，以及中特定的任何引數 [`additionalOptions`](#additional-options) ，以及下列) 所定義的內建 `choco` 選項 (。 [](#built-in-options) 封裝可在 [Chocolatey 套件庫](https://chocolatey.org/packages)中找到。 使用設定檔時，您可以傳入屬性中該檔案的路徑 `input` ，例如 `"input":"packages.config"` 。

### <a name="additional-options"></a>其他選項

您可以將其他設定選項傳入作為的值 `additionalOptions` 。 這些引數是直接傳遞給所使用的引數， [`choco install`](https://chocolatey.org/docs/commands-install) 而且是在 chocolatey 檔中定義。

#### <a name="adding-new-feeds-to-chocolatey"></a>將新的饋送新增至 Chocolatey
如果您想要將新的摘要新增至 Chocolatey，類似于 `choco source add` 命令，您可以傳入 `additionalOptions` 來進行。 [範例使用](#example-usage)方式是新增摘要。 如果您想要新增私人摘要，建議您在命令提示字元中執行此工具，因為它需要認證。 例如，、、、， `devinit run -t choco-install -i {package} -s "{feed link}" -u {user} -p {password}` `{package}` `{feed link}` `{user}` 以及 `{password}` 參考您的特定套件、摘要連結、使用者名稱和密碼。 如需詳細資訊，請參閱上述的 Chocolatey 檔。 

### <a name="built-in-options"></a>內建選項

此 `choco-install` 工具會設定一些 `choco` 命令列引數，以確保 `choco` 可執行無周邊。 以下列出這些引數，您可以在 [chocolatey 檔](https://chocolatey.org/docs/)中找到這些引數的相關檔。

| 名稱                  | 描述                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--是**             | 確認所有提示-選擇肯定答案而非提示。 意味 著 `--accept-license.` |
| **--沒有進度**     | 不要顯示進度-不會顯示進度百分比。                                         |
| **--skip-powershell** | 略過 PowerShell-chocolateyInstall.ps1 將不會執行。                                              |

### <a name="default-behavior"></a>預設行為

此工具的預設行為 `choco-install` 是因為需要屬性而發生錯誤 `input` 。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `choco-install` `.devinit.json` 。

#### <a name="devinitjson-that-will-install-packages-listed-in-packagesconfig"></a>.devinit.js，將會安裝 packages.config 中所列的套件：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "packages.config",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-mongodb"></a>將會安裝 MongoDB 的 .devinit.js：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "mongodb"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-mongodb"></a>.devinit.js將安裝特定版本的 MongoDB：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```

#### <a name="devinitjson-that-adds-a-new-feed-to-chocolatey"></a>.devinit.js，會將新的摘要新增至 Chocolatey：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "packages.config",
            "additionalOptions": "-s '{feed link}'"
        }
    ]
}
```