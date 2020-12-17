---
title: 語言伺服器通訊協定總覽 |Microsoft Docs
description: 瞭解語言伺服器通訊協定如何提供實用的架構，以將語言功能公開給各種不同的工具。
ms.custom: SEO-VS-2020
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d642d1168cbd2a8bd7abadbcdbd7c1e2851b00e
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616126"
---
# <a name="language-server-protocol"></a>語言伺服器通訊協定

## <a name="what-is-the-language-server-protocol"></a>什麼是語言伺服器通訊協定？

在編輯器或 IDE 中支援豐富的編輯功能，例如原始程式碼自動完成或 **移至** 程式設計語言的定義，通常非常具挑戰性且耗時。 通常需要使用編輯器或 IDE 的程式設計語言， (掃描器、剖析器、型別檢查器、產生器和其他) 來撰寫領域模型。 例如，eclipse CDT 外掛程式在 Eclipse IDE 中提供 C/c + + 的支援是以 JAVA 撰寫，因為 Eclipse IDE 本身是以 JAVA 撰寫。 採用這種方法時，它會表示在 TypeScript for Visual Studio 程式碼中執行 C/c + + 領域模型，以及在 c # 中使用不同的領域模型來進行 Visual Studio。

如果開發工具可以重複使用現有的語言特定程式庫，則建立語言特定的領域模型也會變得更容易。 不過，這些程式庫通常是以程式設計語言本身來執行 (例如，C/c + + 的良好 C/c + + 領域模型是在 C/c + +) 中執行。 將 C/c + + 程式庫整合到以 TypeScript 撰寫的編輯器中，在技術上是可行的，但很難處理。

### <a name="language-servers"></a>語言伺服器

另一種方法是在其本身的進程中執行程式庫，並使用處理序間通訊來與其交談。 來回傳送的訊息會形成一種通訊協定。 Language server protocol (LSP) 是將開發工具與語言伺服器進程之間交換的訊息標準化的產品。 使用語言伺服器或 demons 並非新的或新穎的概念。 Vim 和 Emacs 這類的編輯程式已有一段時間可提供語義自動完成支援。 LSP 的目標是要簡化這類的整合，並提供實用的架構來將語言功能公開給各種不同的工具。

具有通用的通訊協定，可讓程式設計語言功能整合到具有最少量條理的開發工具中，方法是重複使用現有的語言領域模型執行。 語言伺服器後端可以使用 PHP、Python 或 JAVA 來撰寫，而 LSP 可讓您輕鬆地將其整合至各種不同的工具。 此通訊協定適用于通用的抽象層級，因此工具可以提供豐富的語言服務，而不需要完全瞭解基礎領域模型的特定細微程度。

## <a name="how-work-on-the-lsp-started"></a>如何開始使用 LSP

LSP 經過一段時間後，現在是3.0 版。 它會在 OmniSharp 所挑選的語言伺服器概念，以提供適用于 c # 的豐富編輯功能時開始。 一開始，OmniSharp 使用 HTTP 通訊協定與 JSON 承載，並已整合至數個編輯器，包括 [Visual Studio Code](https://code.visualstudio.com)。

在此同時，Microsoft 也開始處理 TypeScript 語言伺服器，並瞭解如何在編輯器（例如 Emacs 和 Sublime 文字）中支援 TypeScript。 在這個執行中，編輯器會透過 TypeScript 伺服器進程與 stdin/stdout 進行通訊，並使用 V8 偵錯工具通訊協定針對要求和回應所啟發的 JSON 承載。 TypeScript 伺服器已整合至 TypeScript Sublime 外掛程式，並 VS Code 用於豐富的 TypeScript 編輯。

將兩個不同的語言伺服器整合之後，VS Code 團隊開始探索編輯器和 Ide 的通用語言伺服器通訊協定。 常見的通訊協定可讓語言提供者建立可供不同 Ide 使用的單一語言伺服器。 語言伺服器取用者只需要執行一次通訊協定的用戶端。 這會導致語言提供者和語言取用者都能贏得勝利。

語言伺服器通訊協定是以 TypeScript 伺服器所使用的通訊協定來啟動，並以 VS Code 語言 API 所啟發的更多語言功能來擴展它。 由於其簡易性和現有的程式庫，此通訊協定支援使用 JSON-RPC 進行遠端調用。

VS Code 團隊藉由執行數個 linter 語言伺服器來建立通訊協定的原型，這些伺服器會回應不起毛的 (scan) 檔案，並傳回一組偵測到的警告和錯誤。 其目標是要在使用者于檔中編輯時不起毛檔案，這表示在編輯器會話期間會有許多 linting 要求。 讓伺服器保持啟動並執行是合理的，如此一來，就不需要針對每個使用者編輯啟動新的 linting 進程。 已實行數個 linter 伺服器，包括 VS Code 的 ESLint 和 TSLint 擴充功能。 這兩部 linter 伺服器都實作為 TypeScript/JavaScript，並在 Node.js 上執行。 它們共用的程式庫會執行通訊協定的用戶端和伺服器部分。

## <a name="how-the-lsp-works"></a>LSP 的運作方式

語言伺服器會在自己的進程中執行，而 Visual Studio 或 VS Code 之類的工具會使用語言通訊協定透過 JSON-RPC 與伺服器通訊。 語言伺服器在專用程式中運作的另一個優點是，可避免與單一進程模型相關的效能問題。 如果用戶端和伺服器都是以 Node.js 寫入，則實際的傳輸通道可以是 stdio.h、通訊端、具名管道或節點 ipc。

以下是在例行編輯會話期間，工具和語言伺服器如何進行通訊的範例：

![lsp 流程圖表](media/lsp-flow-diagram.png)

* **使用者會在工具中開啟 (稱為檔)** 的檔案：此工具會通知語言伺服器 ( ' TextDocument/didOpen ' ) 的檔已開啟。 從現在開始，檔內容的真實事實已不再位於檔案系統上，而是由工具保留在記憶體中。

* **使用者進行編輯**：此工具會通知伺服器有關檔變更 ( ' TextDocument/didChange ' ) ，而語言伺服器會更新程式的語義資訊。 發生這種情況時，語言伺服器會分析此資訊，並使用偵測到的錯誤和警告來通知工具 ( ' textDocument/publishDiagnostics ' ) 。

* **使用者在編輯器中的符號上執行 [移至定義]**：此工具會傳送具有兩個參數的 ' textDocument/definition ' 要求： (1) 檔 URI，而 (2) 起始移至定義要求至伺服器的文字位置。 伺服器會回應檔 URI，以及檔內符號的定義位置。

* **使用者關閉檔 (檔)**：系統會從工具傳送「TextDocument/didClose」通知，通知語言伺服器該檔已不再存在於記憶體中，而且目前的內容現在已在檔案系統上保持最新狀態。

此範例說明如何在編輯器功能層級（例如「移至定義」、「尋找所有參考」）中，將通訊協定與語言伺服器通訊。 通訊協定所使用的資料類型為編輯器或 IDE 「資料類型」，例如目前開啟的文字檔和游標的位置。 資料類型不是程式設計語言領域模型的層級，通常會提供抽象語法樹狀結構和編譯器符號 (例如，已解析的類型、命名空間、... ) 。這可大幅簡化通訊協定。

現在讓我們更詳細地查看「textDocument/definition」要求。 以下是在 c + + 檔中「移至定義」要求的用戶端工具和語言伺服器之間的承載。

這是要求：

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

這是回應：

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

在 retrospect 中，描述編輯器層級的資料類型，而不是程式設計語言模型的層級，是語言伺服器通訊協定成功的原因之一。 相較于跨不同的程式設計語言標準化抽象語法樹狀結構和編譯器符號，將文字檔 URI 或資料指標位置標準化更為簡單。

當使用者使用不同的語言時，VS Code 通常會針對每種程式設計語言啟動語言伺服器。 下列範例顯示使用者在 JAVA 和 SASS 檔案上運作的會話。

![java 和 sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>功能

並非所有語言伺服器都可以支援此通訊協定所定義的所有功能。 因此，用戶端和伺服器會透過「功能」宣佈其支援的功能集。 例如，伺服器宣佈它可以處理 ' textDocument/definition ' 要求，但它可能不會處理 ' workspace/symbol ' 要求。 同樣地，用戶端可以宣佈在儲存檔之前，能夠提供「即將儲存」通知，讓伺服器可以計算文字編輯以自動格式化編輯的檔。

## <a name="integrating-a-language-server"></a>整合語言伺服器

語言伺服器與特定工具的實際整合並非由語言伺服器通訊協定所定義，而且會保留在工具實作者中。 有些工具會藉由具有可啟動並與任何類型的語言伺服器通訊的延伸模組，以一般方式整合語言伺服器。 其他（例如 VS Code）會在每個語言伺服器上建立自訂擴充功能，讓擴充功能仍然能夠提供一些自訂語言功能。

為了簡化語言伺服器和用戶端的執行，有用戶端和伺服器元件的程式庫或 Sdk。 這些程式庫會針對不同的語言提供。 例如，有一種 [語言用戶端 npm 模組](https://www.npmjs.com/package/vscode-languageclient) 可簡化語言伺服器與 VS Code 延伸模組的整合，以及使用 Node.js 撰寫語言伺服器的另一種 [語言伺服器 npm 模組](https://www.npmjs.com/package/vscode-languageserver) 。 這是目前的支援程式庫 [清單](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) 。

## <a name="using-the-language-server-protocol-in-visual-studio"></a>在 Visual Studio 中使用語言伺服器通訊協定

* [新增語言伺服器通訊協定延伸](adding-an-lsp-extension.md) 模組-瞭解如何將語言伺服器整合至 Visual Studio。
