---
title: OpenCV
description: 使用 devinit 針對 OpenCV 存放庫以 Linux 和 Windows 為目標的自訂範例。
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 319f560e4661f12acbef941692e5fd2c257c25ee
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672464"
---
# <a name="opencv"></a>OpenCV

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

此範例說明如何自訂 [GitHub Codespaces](https://github.com/features/codespaces) ，以便使用多平臺專案（例如 [opencv/opencv](https://github.com/opencv/opencv)）進行開發。

下列自訂已套用至派生的 [microsoft/OpenCV](https://github.com/microsoft/opencv) ，並允許以 Windows 和 Ubuntu 為目標。

## <a name="customization-with-devcontainerjson-and-devinitjson"></a>使用 devcontainer.js開啟和 devinit.js自訂

`.devcontainer`目錄必須包含下列檔案：

* devcontainer.json
* devinit.js開啟

### <a name="devcontainerjson"></a>devcontainer.json

以下是檔案 _devcontainer.js_ 的內容。

```json
{
  "postCreateCommand": "devinit init"
}
```

會 `postCreateCommand` 啟動  [devinit](devinit-and-codespaces.md) 工具，此工具會使用 _devinit.json_。

### <a name="devinitjson"></a>devinit.js開啟

以下是檔案 [_devinit.js_](devinit-json.md) 的內容。

```json
{
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages useful for C++ development.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```

_上的devinit.js_ 是 [devinit](devinit-and-codespaces.md)工具所使用的檔案，而且它必須在 _devcontainer.js_ 的相同目錄中。

在此範例中， [wsl 安裝](tool-wsl-install.md) 工具是用來建立執行 Ubuntu 20.04 的 wsl 實例，並使用基本的 c + + 開發工具進行布建。
## <a name="targeting-windows-or-linux"></a>以 Windows 或 Linux 為目標

以 Windows 為目標的預設組建設定一律會建立為 `x64-Debug` 。

藉由新增上述檔案，在建立 Codespace 實例時，Visual Studio 會在 [連線管理員](/cpp/linux/connect-to-your-remote-linux-computer)中布建新的 SSH 連線，並在設定選擇器中建立新的設定，並透過 SSH 連線以 Ubuntu 實例為目標。

![以 Ubuntu 為目標的設定](media/wsl-ssh-linux-configuration.png).

藉由選取以 WSL 為目標的醒目提示設定，就可以建立和偵測 OpenCV 的組建目標。
