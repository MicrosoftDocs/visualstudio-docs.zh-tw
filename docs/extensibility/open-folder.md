---
title: Visual Studio 開啟資料夾擴充性總覽 |Microsoft Docs
ms.date: 02/21/2018
ms.topic: overview
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: d213a7add358c46f7088f504d8c54352cda44a1c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905969"
---
# <a name="open-folder-extensibility"></a>開啟資料夾擴充性

[[開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)] 功能可讓使用者在 Visual Studio 中開啟任何程式碼基底，而不需要專案或方案檔。 [開啟資料夾] 提供使用者 Visual Studio 預期的功能，例如：

* 方案總管整合和搜尋
* 編輯器顏色標示
* 前往導覽
* 檔案中尋找搜尋

與工作負載（例如 .NET 和 c + + 開發）搭配使用時，使用者也會取得：

* 豐富的 Intellisense
* 語言特定功能

使用 [開啟資料夾]，延伸模組作者可以針對任何語言建立豐富的功能。 有一些 Api 可支援在使用者程式碼基底中的任何檔案進行建立、偵測和符號搜尋。 目前的擴充項可以更新現有的 Visual Studio 功能，以瞭解程式碼，而不需要支援專案或解決方案。

## <a name="an-api-without-project-systems"></a>沒有專案系統的 API

在過去，Visual Studio 只會使用專案系統來瞭解方案及其專案中的檔案。 專案系統負責載入專案的功能和使用者互動。 它瞭解其專案包含哪些檔案、專案內容的視覺標記法、其他專案的相依性，以及修改基礎專案檔。 而是透過這些階層和功能，讓其他元件代表使用者執行工作。 並非所有的 codebase 都會在專案和方案結構中妥善呈現。 指令碼語言和以 c + + for Linux 撰寫的開放原始碼程式碼，都是很好的例子。 使用 [開啟資料夾]，Visual Studio 提供使用者與其原始程式碼互動的新方式。

「開啟資料夾 Api」位於 `Microsoft.VisualStudio.Workspace.*` 命名空間底下，可供擴充項用來產生和取用開啟資料夾內檔案的資料或動作。 延伸模組可以使用這些 Api 來提供許多領域的功能，包括：

- [工作區](workspaces.md)-開啟資料夾擴充性的起點是工作區和其 api。
- 檔案內容[和動作](workspace-file-contexts.md)-透過檔案內容提供的特定程式碼智慧檔案。
- [編制索引](workspace-indexing.md)-收集並保存開啟資料夾工作區的相關資料。
- [語言服務](workspace-language-services.md)-將語言服務整合到 [開啟資料夾] 工作區。
- 開啟資料夾工作區的[組建](workspace-build.md)-組建支援。

使用下列類型的功能將需要採用新的 Api 來支援開啟的資料夾：

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>意見反應、批註、問題

開啟資料夾和 `Microsoft.VisualStudio.Workspace.*` api 正在開發中。 如果您看到非預期的行為，請查看相關版本的已知問題。 [開發人員社區](https://developercommunity.visualstudio.com)是建議的投票和建立問題的位置。 針對每個意見反應，我們強烈建議您解決問題的詳細描述。 包含您正在開發的 Visual Studio 版本、您所使用的 Api （您所執行的應用程式和互動的目標）、預期的結果，以及實際的結果。 可能的話，請包含 devenv.exe 進程的傾印。 使用 GitHub 的問題追蹤來提供關於此和相關檔的意見反應。

## <a name="next-steps"></a>接下來的步驟

* [工作區](workspaces.md)-瞭解開啟資料夾工作區 API。