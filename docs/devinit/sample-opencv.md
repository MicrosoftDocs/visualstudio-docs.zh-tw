---
title: OpenCV
description: 針對 opencv/opencv 存放庫使用 devinit 進行自訂的範例。
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
ms.openlocfilehash: dd8a17635b70d0f9f49852d09d8f1b9a6864e26e
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809094"
---
# <a name="opencv"></a>OpenCV

此範例說明 [OpenCV](https://github.com/opencv/opencv) 自動布建 [GitHub Codespaces] 所需的自訂 https://github.com/features/codespaces) 。

## <a name="devinitjson"></a>.devinit.js開啟

檔案 [_.devinit.js_](devinit-json.md) 的內容。 此檔案必須位於與 _.devcontainer.js_的相同資料夾中。

```json
{
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.js開啟

存放庫根目錄中檔案 _.devcontainer.js_ 的內容。

```json
{
  "postCreateCommand": "devinit init"
}
```