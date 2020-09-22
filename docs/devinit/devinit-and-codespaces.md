---
title: devinit 與 GitHub Codespace
description: 瞭解如何使用 devinit 自訂 Visual Studio 的 codespace。
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
ms.openlocfilehash: 5697237c1bce719a4658e84435db0426f363f746
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005535"
---
# <a name="devinit-and-github-codespaces"></a>devinit 與 GitHub Codespace

devinit 是 [GitHub Codespaces](https://github.com/features/codespaces) 的絕佳補充，devinit 可以用來取得 codespace 設定，讓參與者可以立即建立、執行和立即進行偵錯工具。

若要與 GitHub Codespaces 整合， `devinit` 必須從 `postCreateCommand` `.devcontainer.json` 放置於存放庫根目錄的檔案中所定義的來呼叫。 在 codespace 中複製存放庫 `postCreateCommand` 之後，會在預設的 shell 中執行) 的字串 (。 您可以 `postCreateCommand` 在 GitHub Codespaces [自訂檔](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project)中閱讀更多相關資訊。 若要加入 `devinit` 命令，您可以將加入 `devinit init` 至， `postCreateCommand` 如下列範例所示。

您也可以在 `devinit init -f <path to .devinit.json>` 連線到 codespace 之後，從 Visual Studio 整合式終端機執行。

## <a name="examples"></a>範例

### <a name="with-a-devinitjson-file"></a>使用檔案 .devinit.js
在此範例中，下列檔案 _ 上的.devcontainer.js_ 會放在存放庫根目錄中，並放在檔案的 _.devinit.js_ 旁。 檔案也可以放在 _devcontainer_ 目錄中。

```json
{
  "postCreateCommand": "devinit init"
}
```

```json
{
  "postCreateCommand": ["<some other command>", "devinit init"]
}
```

### <a name="as-commands"></a>As 命令
在此範例中，下列檔案 _.devcontainer.js_ 放在存放庫根目錄中，並以 `devinit run` 程式設計方式呼叫以執行工具  

```json
{
  "postCreateCommand": ["devinit run –t require-dotnetcoresdk"]
}
```

### <a name="from-a-terminal-prompt"></a>從終端機提示字元

當目前工作目錄包含檔案 _ 上的.devinit.js_ 時。

```console
> devinit init
```

當 _.devinit.js在_ 另一個目錄中時。

```console
> devinit init -f path/to/.devinit.json
```
