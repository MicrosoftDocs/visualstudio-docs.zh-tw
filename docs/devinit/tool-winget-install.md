---
title: winget-安裝
description: 適用于 winget 的 devinit 工具。
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 3c236e63686d3882ed199c122fed9ebddfa8fa20
ms.sourcegitcommit: e262f4c2a147c3fa2d27de666aae3a0497317867
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2021
ms.locfileid: "100012356"
---
# <a name="winget-install"></a>winget-安裝

此 `winget-install` 工具是用來安裝 [winget 套件](https://docs.microsoft.com/windows/package-manager/winget/)。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具會輸出錯誤。

| 名稱                                         | 類型   | 必要 | 值                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **評論**                                 | 字串 | No       | 選擇性批註屬性。 未使用。                                             |
| [**輸入**](#input)                          | 字串 | No       | 要取得安裝的封裝。 如需詳細資料，請參閱下列 [輸入](#input) 。                    |
| [**additionalOptions**](#additional-options) | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。                  |

### <a name="input"></a>輸入

輸入屬性是用來指定 `Id` `Name` 要安裝的封裝或封裝的或 (例如 ' MongoDB. 伺服器 ' ) 。 輸入的值將會附加至 `winget install` 命令 (例如 `winget install MongoDB.Server`) 。 如果封裝名稱不是唯一的，而且符合其他封裝，您可以指定封裝的， `Id` 並將 `--exact` 旗標加入 `additionalOptions` 至，以確保封裝身分識別完全相符。 您 `Id` 可以執行 `winget search` 命令並使用封裝的參數，找到封裝的 `Id` 。  

### <a name="additional-options"></a>其他選項

您可以將其他設定選項傳入作為 additionalOptions 的值。 這些引數會直接傳遞至所使用的引數 `winget install` ，並在 `winget install` [檔](https://docs.microsoft.com/windows/package-manager/winget/install)中定義。

#### <a name="manifests"></a>資訊清單

另一個支援的選擇性 `winget` 是能夠提供 [資訊清單](https://docs.microsoft.com/windows/package-manager/winget/install#local-install) 檔，以詳細說明要安裝的封裝。 若要將此功能與 devinit 搭配使用， `input` 參數應該是空的，而且 `additionalOptions` 屬性應該包含 `--manifest` 後面接著資訊清單路徑的選項 (例如 `--manifest path.to.manifest.yml`) 。

### <a name="built-in-options"></a>內建選項

Winget 安裝工具會設定數個 winget 命令列引數，以確保 winget 可以執行無周邊。 以下列出這些引數，您可以在檔中找到這些引數的相關檔 `winget install` [ ](https://docs.microsoft.com/windows/package-manager/winget/install)。

| 名稱     | 描述                                                                                                                       |
|----------|-----------------------------------------------------------------------------------------------------------------------------------|
| --無訊息 | 以無訊息模式執行安裝程式。 這會隱藏所有 UI。 預設體驗會顯示安裝程式的進度。                       | 

## <a name="example-usage"></a>使用方式範例

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-6.0",
    "run": [
        {
            "comments": "Installs Microsoft PowerToys.",
            "tool": "winget-install",
            "input": "Microsoft.PowerToys",
            "additionalOptions": "--version 0.15.2",
        },
        {
            "comments": "Installs PostgreSQL.",
            "tool": "winget-install",
            "input": "PostgreSQL.PostgreSQL",
            "additionalOptions": "--exact"
        },
        {
            "comments": "Installs the package defined in winget-manifest.yml.",
            "tool": "winget-install",
            "additionalOptions": "--manifest winget-manifest.yml"
        }
    ]
}
```
