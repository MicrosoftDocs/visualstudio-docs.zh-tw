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
ms.openlocfilehash: 964b360806f6f834aa57c475d2117c124f2cf8af
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668634"
---
# <a name="open-folder-extensibility"></a>開啟資料夾擴充性

[ [開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) ] 功能可讓使用者在 Visual Studio 中開啟任何程式碼基底，而不需要專案或方案檔。 開啟資料夾提供使用者預期的 Visual Studio 功能，例如：

* 方案總管整合和搜尋
* 編輯器顏色標示
* 移至導覽
* 在檔案搜尋中尋找

與工作負載（例如 .NET 和 c + + 開發）搭配使用時，使用者也會取得：

* 豐富的 Intellisense
* 特定語言功能

使用「開啟資料夾」時，延伸模組作者可以為任何語言建立豐富的功能。 有 Api 可支援在使用者程式碼基底中的任何檔案進行建立、偵測和符號搜尋。 目前的擴充項可以更新現有的 Visual Studio 功能，以瞭解程式碼，而不需要支援專案或方案。

## <a name="an-api-without-project-systems"></a>沒有專案系統的 API

在過去，Visual Studio 只會使用專案系統，來瞭解方案及其專案中的檔案。 專案系統負責載入專案的功能和使用者互動。 它瞭解專案包含哪些檔案、專案內容的視覺標記法、其他專案的相依性，以及修改基礎專案檔。 它會透過這些階層和功能，讓其他元件代表使用者運作。 並非所有的代碼基底都能在專案和方案結構中正確呈現。 指令碼語言和以 c + + for Linux 撰寫的開放原始碼程式碼都是很好的範例。 使用 [開啟資料夾]，Visual Studio 可讓使用者以新的方式與其原始程式碼互動。

開啟資料夾 Api 位於 `Microsoft.VisualStudio.Workspace.*` 命名空間底下，可供擴充項用來產生和取用開啟資料夾內檔案的資料或動作。 延伸模組可以使用這些 Api 來提供許多方面的功能，包括：

- [工作區](workspaces.md) -開啟資料夾擴充性的起點是工作區和其 api。
- 檔案內容[和動作](workspace-file-contexts.md)-透過檔案內容提供的特定程式碼智慧。
- [編制索引](workspace-indexing.md) -收集和保存開啟資料夾工作區的相關資料。
- [語言服務](workspace-language-services.md) -將語言服務整合到開啟資料夾工作區。
- 開啟資料夾工作區的[組建](workspace-build.md)組建支援。

使用下列類型的功能將需要採用新的 Api 來支援開啟資料夾：

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>意見反應、留言、問題

開啟資料夾與 `Microsoft.VisualStudio.Workspace.*` api 正在進行開發。 如果您看到非預期的行為，請查看您感興趣之發行的已知問題。 [開發人員社群](https://aka.ms/feedback/suggest?space=8) 是投票和建立任何問題的建議位置。 針對每個意見反應，我們強烈建議您解決問題的詳細描述。 包含您要開發的 Visual Studio 版本、您所使用的 Api (您所執行的工作，以及您與) 、預期的結果和實際結果之間的互動。 可能的話，請包含 devenv.exe 進程的傾印。 使用 GitHub 的問題追蹤，以提供有關此和相關檔的意見反應。

## <a name="next-steps"></a>後續步驟

* [工作區](workspaces.md) -瞭解開啟資料夾工作區 API。