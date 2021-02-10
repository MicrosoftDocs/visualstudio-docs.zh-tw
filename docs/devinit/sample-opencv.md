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
ms.openlocfilehash: 6524cec090f20c475724f1ae8615c5dd24cfa2d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943502"
---
# <a name="opencv"></a>OpenCV

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
