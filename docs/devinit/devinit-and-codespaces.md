---
title: devinit 與 GitHub Codespace
description: 瞭解如何使用 devinit 自訂 Visual Studio 的 codespace。
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
ms.openlocfilehash: c98c00e0b62d3a2a755790b07621d717abcb41c1
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672218"
---
# <a name="devinit-and-github-codespaces"></a>devinit 與 GitHub Codespace

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

devinit 是 [GitHub Codespaces](https://github.com/features/codespaces) 的絕佳協助工具，devinit 可用來取得 codespace 設定，讓參與者可以立即建立、執行和立即進行偵錯工具。

> [!IMPORTANT]
> 將 devinit 與您的 codespace 整合之前，您必須先確定您有定義相依性的檔案 `.devinit.json` 。 如需有關如何建立的詳細資訊 `.devinit.json` ，請參閱使用者 [入門檔](getting-started-with-devinit.md)。

在 GitHub Codespace 內，您的應用程式是在雲端中建立並執行。 在雲端中，表示您的應用程式無法存取您電腦上的本機資源。 這些工具組括您已在本機安裝的工具或程式。 如果您的應用程式需要安裝或設定任何系統範圍的相依性，則必須在每個 codespace 上進行。 要達到這個目的，最簡單的方式就是使用檔案 `.devinit.json` 。

若要確定 codespace 是使用應用程式所需的相依性所建立，則必須在 `devinit` 建立 codespace 時執行。 這可以藉由 `devinit init` 從 `postCreateCommand` `.devcontainer.json` 存放庫根目錄中的檔案所定義的來呼叫。 在 codespace 中複製存放庫 `postCreateCommand` 之後，會在預設的 shell 中執行) 的字串 (。 您可以 `postCreateCommand` 在 GitHub Codespaces [自訂檔](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project)中閱讀更多相關資訊。 若要加入 `devinit` 命令，您可以將加入 `devinit init` 至， `postCreateCommand` 如下列範例所示。

您也可以在 `devinit init -f <path to .devinit.json>` 連線到 codespace 之後，從 Visual Studio 整合式終端機執行。

## <a name="examples"></a>範例

在下列兩個範例中， `.devinit.json` 都是在存放庫根目錄中 `.devcontainer.json` 。

### <a name="with-a-devcontainerjson-file"></a>使用檔案 .devcontainer.js

在此範例中， `.devcontainer.json` 下列檔案會放在存放庫根目錄和檔案的旁邊 `.devinit.json` 。 檔案也可以放在 `.devcontainer` 目錄中。

```json
{
  "postCreateCommand": "devinit init"
}
```

當 `.devinit.json` 位於另一個目錄時，可以使用-f 旗標。

```json
{
  "postCreateCommand": "devinit init -f path\\to\\.devinit.json"
}

```

```json
{
  "postCreateCommand": ["<some other command>", "devinit init"]
}
```

您可以在我們的 [檔](sample-all-tool.md) 和 GitHub 上的 [.net Core 範例](https://github.com/microsoft/devinit-example-dotnet-core) 中找到更多使用 devinit 的範例，並 [Node.js 範例](https://github.com/microsoft/devinit-example-nodejs) 存放庫。

### <a name="as-commands"></a>As 命令

在此範例中， `.devcontainer.json` 下列檔案會放在存放庫根目錄中，並 `devinit run` 直接從命令列呼叫以執行個別的工具。  

```json
{
  "postCreateCommand": ["devinit run –t require-dotnetcoresdk"]
}
```

### <a name="from-a-terminal-prompt"></a>從終端機提示字元

當目前的工作目錄包含檔案時 `.devinit.json` 。

```console
devinit init
```

當位於 `.devinit.json` 另一個目錄時。

```console
devinit init -f path/to/.devinit.json
```
