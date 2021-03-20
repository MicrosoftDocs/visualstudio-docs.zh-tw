---
title: wsl-install
description: devinit tool wsl-安裝。
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
ms.openlocfilehash: 4dff121d7866918d5c30986dc9bd4c3cab039ac5
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672422"
---
# <a name="wsl-install"></a>wsl-install

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

此 `wsl-install` 工具可用來安裝適用于 [WINDOWS 子系統 LINUX 版](/windows/wsl/) (WSL) 的 Linux 散發版本。

> [!IMPORTANT]
> 此 `wsl-install` 工具需要在 Windows 上啟用 WSL 2。 如果基於某些原因而未啟用 WSL 2，您可以遵循 [WSL 安裝檔](https://docs.microsoft.com/windows/wsl/install-win10)。 您也可以使用啟用的 [ [啟用](tool-windowsfeature-enable.md) ] 工具來啟用任何所需的 Windows 功能。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                             |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                             |
| [**輸入**](#input)                              | 字串 | Yes      | 要安裝的發行版本。 如需詳細資料，請參閱下列 [輸入](#input) 。     |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。  |

### <a name="input"></a>輸入

AppX 應用程式散發封裝的 URI (`.appx`) 包含要部署的發行版本。 URI 必須指向 `.appx` 保存 `install.tar.gz` 在封存根或內部封存內的單一封存 `.appx` 。 支援的散發版本範例包括：

| 發行版本                          | Uri                                                           |
|---------------------------------|---------------------------------------------------------------|
| Ubuntu 20.04                    | https://aka.ms/wslubuntu2004                                  |
| Ubuntu 18.04                    | https://aka.ms/wsl-ubuntu-1804                                |
| Ubuntu 16.04                    | https://aka.ms/wsl-ubuntu-1604                                |
| Debian GNU/Linux                | https://aka.ms/wsl-debian-gnulinux                            |
| Kali Linux                      | https://aka.ms/wsl-kali-linux-new                             |
| OpenSUSE Leap 42                | https://aka.ms/wsl-opensuse-42                                |
| SUSE Linux Enterprise Server 12 | https://aka.ms/wsl-sles-12                                    |

> [!NOTE]
> GitHub Codespaces 目前不支援 ARM Linux 散發版本。

### <a name="additional-options"></a>其他選項

支援多個其他選項：

| 名稱                      | 類型      | 必要 | 值                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --wsl-版本             | 字串    | No       | 要使用的 WSL 版本。 預設值為 2。                                                                                                                                  |
| --建立後-命令     | 字串    | No       | 完成安裝之後，要在 Linux 發行版本內執行的命令。 命令應格式化為單一單字，或以引號括住。 預設值為 no command。  |

### <a name="default-behavior"></a>預設行為

工具的預設行為 `wsl-install` 是因為 `input` 屬性（必須要安裝的發行版本）而發生錯誤。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `wsl-install` `.devinit.json` 。

#### <a name="devinitjson-that-will-install-ubuntu-2004"></a>.devinit.js將安裝 Ubuntu 20.04：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-ubuntu-2004-and-perform-a-post-create-command"></a>.devinit.js將會安裝 Ubuntu 20.04 並執行 post create 命令：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'echo Hello from Ubuntu!'"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-ubuntu-2004-and-perform-a-post-create-command-that-configures-the-packages-listed"></a>.devinit.js將會安裝 Ubuntu 20.04，並執行可設定所列出套件的 post create 命令：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```
