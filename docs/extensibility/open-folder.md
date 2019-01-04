---
title: Visual Studio 開啟資料夾擴充性概觀 |Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2bb74703f639848d643f536edf620e30b1836310
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986007"
---
# <a name="open-folder-extensibility"></a>開啟資料夾擴充性

[開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)功能可讓使用者可以開啟任何程式碼基底在 Visual Studio 中而不需要專案或方案檔。 開啟資料夾可提供功能的使用者預期從 Visual Studio 這類：

* 方案總管整合和搜尋
* 編輯器的顏色標示
* 移至導覽
* 在檔案搜尋中尋找

例如，基於.NET 和 c + + 開發的工作負載搭配使用時，使用者也會得到：

* 豐富的 Intellisense
* 語言特有的功能

開啟資料夾時，延伸模組作者可以建立豐富的功能，適用於任何語言。 有支援建置、 偵錯，以及符號搜尋中使用者的任何檔案的程式碼基底的 Api。 目前的擴充項可以更新其現有的 Visual Studio 功能，以了解程式碼，而不需要專案或方案的支援。

## <a name="an-api-without-project-systems"></a>沒有專案系統的 API

在過去，Visual Studio 只了解方案和其使用專案系統的專案中的檔案。 專案系統負責載入專案的功能和使用者互動。 它了解有何檔案及其專案包含專案內容]、 [等其他專案的相依性的視覺表示方式，修改基礎專案檔案。 它是透過這些階層和其他元件運作代表使用者的功能。 並非所有程式碼基底都也會出現在 專案和方案的結構。 指令碼語言和 c + + 中撰寫適用於 Linux 的開放原始碼程式碼是很好的範例。 開啟資料夾時，Visual Studio 可讓使用者與他們的原始程式碼互動的新方式。

開啟資料夾 Api 受到`Microsoft.VisualStudio.Workspace.*`命名空間並可供擴充項，可以產生和取用資料或周圍開啟的資料夾中檔案的動作。 延伸模組可以使用這些 Api，來為許多領域，包括提供的功能：

- [工作區](workspaces.md)-從開始的 端點開啟資料夾擴充性是工作區和其 Api。
- [檔案內容和動作](workspace-file-contexts.md)-檔案提供透過檔案內容的特定程式碼情報。
- [編製索引](workspace-indexing.md)-收集並保存開啟資料夾的工作區的詳細資料。
- [語言服務](workspace-language-services.md)-語言服務整合至 開啟資料夾的工作區。
- [建置](workspace-build.md)-建置開啟資料夾的工作區的支援。

使用下列類型的功能將需要採用新的 Api，以支援開啟資料夾：

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>意見反應，註解的問題

開啟資料夾和`Microsoft.VisualStudio.Workspace.*`Api 正在使用中的開發。 如果您看到非預期的行為，然後查看感興趣的發行版本的已知的問題。 [開發人員社群](https://developercommunity.visualstudio.com)是投票，並建立任何問題的建議的位置。 如需每個意見反應，我們強烈建議您問題的詳細的描述。 包含您正在開發的 Visual Studio 版本、 您使用 （您已實作和與正在進行的互動） 的 Api、 預期的結果和實際的結果。 可能的話，包含 devenv.exe 處理序的傾印。 使用 GitHub 的問題提供意見反應，這個追蹤和相關文件。

## <a name="next-steps"></a>後續步驟

* [工作區](workspaces.md)-了解 [開啟資料夾] 工作區 API。