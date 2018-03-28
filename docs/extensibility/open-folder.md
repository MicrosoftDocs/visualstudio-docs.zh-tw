---
title: Visual Studio 開啟資料夾 extensibility 概觀 |Microsoft 文件
ms.custom: ''
ms.date: 02/21/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 1bbe9638777bc672a0cec494498a38f4bd8ce1f4
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="open-folder-extensibility"></a>開啟資料夾的擴充性

[開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)功能可讓使用者開啟任何程式碼基底 Visual Studio 中，而不需要專案或方案檔。 開啟資料夾提供功能的使用者預期可從 Visual Studio 這類：

* 方案總管整合和搜尋
* 編輯器顏色標示
* 移至巡覽
* 在搜尋檔案中尋找

例如.NET 和 c + + 開發的工作負載搭配使用時，使用者也會取得：

* 豐富的 Intellisense
* 語言特有的功能

延伸模組作者可以使用開啟的資料夾，來建立豐富的功能，針對任何語言。 沒有應用程式開發介面以支援建置、 偵錯，以及符號搜尋中使用者的任何檔案的程式碼庫。 目前的 extender 可以更新其現有的 Visual Studio 功能，以了解程式碼的專案或方案的支援。

## <a name="an-api-without-project-systems"></a>沒有專案系統 API

在過去，Visual Studio 只會了解方案和專案使用專案系統中的檔案。 專案系統會負責載入專案的功能和使用者互動。 其了解哪些檔案的專案包含專案內容]、 [其他專案的相依性的視覺表示法，修改基礎專案檔案。 它是透過這些階層和其他元件代表使用者運作的功能。 並非所有程式碼基底中的專案和方案結構也表示。 指令碼語言與以 c + + 撰寫適用於 Linux 的開放原始碼程式碼是很好的範例。 開啟資料夾時，Visual Studio 可讓使用者原始程式碼與互動的新方式。

開啟資料夾 Api 受到`Microsoft.VisualStudio.Workspace.*`命名空間以及可用的擴充項，可以產生和使用資料或周圍開啟資料夾中檔案的動作。 擴充功能可以使用這些 Api 提供的許多部分，包括的功能：

- [工作區](workspaces.md)-從開始開啟資料夾點擴充性是工作空間和其應用程式開發介面。
- [檔案內容和動作](workspace-file-contexts.md)-檔案提供透過檔案內容的特定程式碼智慧。
- [索引](workspace-indexing.md)-收集並保存開啟資料夾的工作區的詳細資料。
- [語言服務](workspace-language-services.md)-語言服務整合的工作區開啟資料夾。
- [建置](workspace-build.md)-建置開啟資料夾的工作區的支援。

使用下列類型的功能需要採用新的 Api 可支援開啟資料夾：

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>意見反應，註解的問題

開啟資料夾和`Microsoft.VisualStudio.Workspace.*`Api 是真的開發。 如果您看到非預期的行為，然後查看感興趣的版本的已知的問題。 開發人員社群是投票，並建立任何問題的建議的位置。 如需每個意見反應，我們強烈建議您問題的詳細的說明。 包括您正在開發的 Visual Studio 版本、 您使用 （您已實作和您正與互動） 的 Api，獲得預期的結果，以及實際的結果。 可能的話，包含 devenv.exe 程序的傾印。 使用追蹤上提供意見反應的 GitHub 的問題和相關文件。

## <a name="next-steps"></a>後續步驟

* [工作區](workspaces.md)-了解應用程式開發介面的 [開啟資料夾] 工作區。