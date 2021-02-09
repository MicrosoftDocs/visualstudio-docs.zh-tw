---
title: 教學課程
description: Devinit 的教學課程。
ms.date: 11/18/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 32d407c4803c2b50276145a2c9a66c2c501f05ab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874417"
---
# <a name="tutorial"></a>教學課程

在本教學課程中，我們將探索如何使用 devinit 和 Codespaces 來設定 [eShopOnWeb 存放庫](https://github.com/andysterland/eShopOnWeb) 。 本教學課程假設 devinit 已可供使用，如 [開始使用] [頁面](getting-started-with-devinit.md)中所述。

## <a name="step-1-determining-setup-steps"></a>步驟1：決定安裝步驟

如 [開始使用] [頁面](getting-started-with-devinit.md)中所述，第一步是決定您的專案所擁有的相依性和設定步驟。 這會根據特定專案而有所不同，但有幾個問題需要考慮：

- 您的專案相依于哪些執行時間或 Sdk？
- 您的專案是否需要任何套件 (例如，從 Chocolatey) ？
- 您的安裝程式是否需要採取任何動作 (例如) 執行腳本？
- 您的專案是否相依于隨 Visual Studio 一起安裝的任何專案？
  - 如果是的話，最好也將這些包含在 devinit 設定中。 如此一來，您就可以避免結合 Visual Studio 安裝。

判斷這項資訊的最佳方式之一，就是探索您目前為存放庫所擁有的手動設定步驟。 針對 eShopOnWeb，有幾件事需要處理：

- 安裝最新版本的 .NET Core SDK
- 安裝最新版的 .NET Entity Framework Core Tools CLI
- 安裝 SQL Server 2019 Express
- 使用 .NET Entity Framework CLI 將本機資料庫更新至最新的遷移

接下來，我們將探討如何在 devinit 的內容中完成這一切。

## <a name="step-2-the-devinitjson"></a>步驟2： .devinit.js開啟

首先，我們會想要建立檔案的 [.devinit.js](devinit-json.md) ，並將它放在存放庫的根目錄中。 此檔案將包含一系列的步驟，這些步驟將在稍後作為命令的一部分執行 `devinit init` 。 若要判斷檔案中應包含的內容 `.devinit.json` ，我們可以取得安裝步驟清單，並與 [devinit 工具](devinit-tool-list.md)清單進行比較。 現在就來看看上述的設定步驟。

| 步驟                                                              | Devinit 可以為我們處理這種情況嗎？                                                                        |
| :---------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------  |
| 安裝最新的 .NET Core SDK                                      | **是**！ 我們可以使用此[ `require-dotnetcoresdk` 工具](tool-require-dotnetcoresdk.md)                  |
| 安裝 .NET Entity Framework Core Tools CLI                      | **是**！ 我們可以使用此[ `dotnet-toolinstall` 工具](tool-dotnet-toolinstall.md)                        |
| 安裝 SQL Server 2019 Express                                   | **是**！ 我們可以使用此[ `choco-install` 工具](tool-choco-install.md)                                  |
| 使用 .NET Entity Framework 更新本機資料庫                 | **否**，但我們還是藉由結合 devinit 與腳本來完成這項操作！                               |

現在我們已經知道了，讓我們從基本的著手 `.devinit.json` 。 我們會包含[ `.devinit.json` 架構](https://json.schemastore.org/devinit.schema-2.0)的參考和空白 `run` 區段：

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": []
}
```

現在讓我們加入一些工具！

首先，我們要加入 [`require-dotnetcoresdk`](tool-require-dotnetcoresdk.md) 。 從該工具的檔中，我們可以看到預設行為是安裝最新的 SDK 版本。 這正是我們想要的，所以我們將它新增至 `.devinit.json` ：

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    }
  ]
}
```

其次，我們要加入 [`dotnet-toolinstall`](tool-dotnet-toolinstall.md) 全域安裝此 `dotnet-ef` 工具。 在檔中，我們看到可以使用 `input` 欄位指定工具名稱，並使用 `additionalOptions` 欄位來指定全域範圍：

```json
{
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    },
    {
      "comments": "Install latest version of the .NET Entity Framework Core Tools CLI.",
      "tool": "dotnet-toolinstall",
      "input": "dotnet-ef",
      "additionalOptions": "--global"
    }
  ]
}
```

最後，我們將新增 [`choco-install`](tool-choco-install.md) 以安裝 `sql-server-express` 套件。

```json
{
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    },
    {
      "comments": "Install latest version of the .NET Entity Framework Core Tools CLI.",
      "tool": "dotnet-toolinstall",
      "input": "dotnet-ef",
      "additionalOptions": "--global"
    },
    {
      "comments": "Install SQL Server 2019 Express",
      "tool": "choco-install",
      "input": "sql-server-express"
    }
  ]
}
```

現在我們 `.devinit.json` 已經完成了，我們可以處理一個設定腳本，負責執行 devinit 和更新本機資料庫。

## <a name="step-3-the-setup-script"></a>步驟3：設定腳本

為了處理執行中的 devinit 和更新本機資料庫，我們將建立腳本來執行所需的命令。 讓我們在存放庫根目錄中建立空的 PowerShell 腳本，名為 `PostCloneSetup.ps1` 。 首先，我們會新增 `devinit init` 下列呼叫：

```powershell
devinit init
```

執行時， `devinit init` 將會執行在的一節中定義的所有工具 `run` `.devinit.json` 。

最後，我們想要叫用 `dotnet ef database update` 以更新本機資料庫：

```powershell
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

既然我們的設定腳本已完成，我們需要新增一個檔案， `.devcontainer.json` 在 codespace 安裝期間執行它。

## <a name="step-4-the-devcontainerjson"></a>步驟4： .devcontainer.js開啟

為了確保我們的設定腳本會在 codespace 建立期間執行，我們會使用檔案 `.devcontainer.json` 。 同樣地，這應該放在存放庫根目錄中。

在檔案中 `.devcontainer.json` ，我們只需要在中呼叫我們的設定腳本 `postCreateCommand` 。 這將會在 codespace 建立過程中執行：

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```

這樣就大功告成了！

## <a name="step-5-trying-it-out"></a>步驟5：試用

現在我們已準備好設定步驟，讓我們使用 [真正](https://github.com/andysterland/eShopOnWeb)的存放庫在即時 codespace 中試試看。

首先，我們將使用 Visual Studio 建立 codespace：

:::image type="content" source="media/eshoponweb-github-codespaces-prompt.png" alt-text="建立 codespace":::

開始 codespace 建立之後，我們可以在中觀看安裝程式的進度 `C:\.vsonline\.vsoshared\vmTerminal.dat` ：

:::image type="content" source="media/eshoponweb-watching-progress.png" alt-text="觀賞設定進度":::

完成之後，讓我們透過執行應用程式， `Web.csproj` 以確定一切都能正常運作：

:::image type="content" source="media/eshoponweb-csproj.png" alt-text="執行專案":::

在應用程式建立並啟動之後，我們可以在網頁瀏覽器中看到該商店：

:::image type="content" source="media/eshoponweb-live.png" alt-text="觀看網站":::

如此一來，我們的安裝程式就能正常運作，而且現在已準備好在 eShopOnWeb 專案中進行開發！
