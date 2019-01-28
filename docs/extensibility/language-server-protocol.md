---
title: 語言伺服器通訊協定概觀 |Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a41bccbec31f11a30d5e9ccf0e97806d3e7efb4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023453"
---
# <a name="language-server-protocol"></a>語言伺服器通訊協定

## <a name="what-is-the-language-server-protocol"></a>什麼是語言伺服器通訊協定？

支援豐富的編輯功能像來源的程式碼自動完成選項或**移至定義**編輯器或 IDE 中的程式語言是傳統上非常困難又耗時。 通常需要撰寫的編輯器或 IDE 的程式設計語言中的網域模型 （掃描器、 剖析器、 型別檢查、 產生器等等）。 例如，支援 C/c + + 在 Eclipse IDE 的 Eclipse CDT 外掛程式是以 Java 撰寫因為 Eclipse IDE 本身以 Java 撰寫。 此方法之後，它表示在 C# 中實作 C/c + + 中的網域模型 TypeScript for Visual Studio Code，以及一個個別的網域模型，適用於 Visual Studio。

建立語言特定的網域模型也是一種開發工具，可以重複使用現有的特定語言程式庫的更加容易。 不過，這些程式庫通常會實作在程式語言本身 （比方說，好 C/c + + 網域模型以 C/c + + 實作）。 C/c + + 程式庫整合以 TypeScript 撰寫編輯器技術上是可行的但不困難。

### <a name="language-servers"></a>語言伺服器

另一種方法是在自己的處理序中執行的程式庫，並使用處理序間通訊與它。 來回傳送的訊息會形成一種通訊協定。 語言伺服器通訊協定 (LSP) 是標準化的開發工具與語言伺服器處理序之間交換訊息的乘積。 使用語言伺服器或一個惡魔啊，不是新或新奇的主意。 編輯器，例如 Vim 和 Emacs 投入不少這段時間，以提供語意的自動完成支援。 LSP 的目標是要簡化這類的整合，並提供實用的架構來公開各種不同的工具的語言功能。

常見的通訊協定可讓程式設計到最少的複雜的開發工具的語言功能，重複使用現有的語言的領域模型實作的整合。 語言伺服器後端可以在 PHP、 Python 或 Java 撰寫並 LSP 可讓它輕易地整合到各種不同的工具。 通訊協定可以在一般的層級的抽象，使工具可以提供豐富的語言服務，而不需要完全了解基礎網域模型的特定細節。

## <a name="how-work-on-the-lsp-started"></a>如何在啟動 LSP 上運作

LSP 已發展一段時間，目前已在 3.0 版。 它啟動時的語言伺服器概念已收取 OmniSharp 適用於 C# 提供豐富的編輯功能。 一開始，OmniSharp 搭配 JSON 承載中的 HTTP 通訊協定和已整合至數個編輯器包括[Visual Studio Code](https://code.visualstudio.com)。

大約在同一時間，Microsoft 會開始運作的 TypeScript 語言伺服器上，其支援 TypeScript Emacs 和 Sublime Text 等編輯器中的概念。 在此實作中，編輯器會透過 stdin/stdout 與 TypeScript 伺服器處理序進行通訊，並使用要求和回應的 JSON 承載所 V8 偵錯工具通訊協定的。 TypeScript 伺服器已整合至 TypeScript Sublime 外掛程式，VS Code 的豐富的 TypeScript 編輯。

在之後需要整合兩個不同的語言伺服器，VS Code 小組已開始探索編輯器和 Ide 的常見語言伺服器通訊協定。 常見的通訊協定可讓您建立可供不同的 Ide 的單一語言伺服器的語言提供者。 Language server 取用者只會有一次實作的通訊協定的用戶端。 這會導致雙贏的情況下的語言提供者和語言取用者。

語言伺服器通訊協定開始使用 TypeScript 伺服器中，展開與靈感來自於 VS Code 語言 API 的更多語言功能所使用的通訊協定。 通訊協定支援 JSON rpc 遠端引動過程，由於其簡易性和現有的程式庫。

在 VS 程式碼的小組原型的通訊協定，藉由實作數個 linter 語言伺服器回應要求到 lint （掃描） 檔案，並傳回一組的偵測到的警告和錯誤。 目標是要 lint 的檔案做為文件，這表示編輯器工作階段期間將會多 linting 要求中的使用者編輯。 它不二人選讓註冊的伺服器和執行，因此不需要為每個使用者編輯啟動新的 lint 處理程序。 已實作數個 linter 伺服器，包括 VS 程式碼的 ESLint 和 TSLint 延伸模組。 這兩部 linter 伺服器同時實作 TypeScript/javascript 撰寫並在 Node.js 上執行。 它們會共用程式庫實作之通訊協定的用戶端和伺服器的一部分。

## <a name="how-the-lsp-works"></a>LSP 的運作方式

語言伺服器執行自己的處理序中，並透過 JSON RPC 使用的語言通訊協定與伺服器通訊的工具，例如 Visual Studio 或 VS Code。 語言伺服器作業系統專用的處理序中的另一個優點是可避免單一處理序模型相關的效能問題。 實際的傳輸通道可以 stdio、 通訊端、 具名的管道或節點 ipc 如果用戶端和伺服器以 Node.js 撰寫。

以下的範例工具和語言伺服器通訊期間常式的方式編輯工作階段：

![lsp 流程圖](media/lsp-flow-diagram.png)

* **使用者在工具中開啟檔案 （稱為文件）**:此工具會告知語言伺服器已開啟的文件 (' textDocument/didOpen ')。 從現在起，文件內容的真相不再位於檔案系統，但保留在記憶體中的工具。

* **使用者可編輯**:此工具會通知伺服器與變更相關的文件 (' textDocument/didChange ') 和程式的語意資訊會由語言伺服器更新。 發生這種情況，語言伺服器會分析這項資訊，並通知使用偵測到的錯誤和警告 (' textDocument/publishDiagnostics ') 的工具。

* **如果使用者在執行 移至定義 」 編輯器中的符號**:此工具會傳送兩個參數的 'textDocument/定義' 要求：（1） 的文件 URI，其中 移至定義要求已起始到伺服器 （2） 的文字位置。 伺服器會回應文件 URI 和內文件的符號定義的位置。

* **在使用者關閉文件 （檔案）**:從工具，通知文件是現在不再記憶體，且目前的內容是現在最新的檔案系統上的語言伺服器會傳送 'textDocument/didClose' 通知。

此範例說明通訊協定與層級的編輯器功能，例如 [移至定義]，[尋找所有參考] 的語言伺服器通訊的方式。 通訊協定所使用的資料類型是編輯器或 IDE '資料類型' 目前開啟的文字文件等資料指標的位置。 資料類型不是層級的程式設計語言領域模型通常提供抽象語法樹狀結構和編譯器符號 （例如，解析型別，命名空間，...）。這可大幅簡化的通訊協定。

現在讓我們看看 'textDocument/定義' 要求在更多詳細資料。 以下是用戶端工具和 c + + 文件中的 移至定義 」 要求的語言伺服器之間的裝載。

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

回顧以往，描述在編輯器的層級，而非程式設計的語言模型的層級的資料類型是其中一個語言伺服器通訊協定成功的原因。 就簡單多了標準化文字文件 URI 或資料指標位置，相較於標準化不同的程式設計語言中的抽象語法樹狀結構和編譯器的符號。

當使用者正在使用不同的語言時，VS 程式碼通常會啟動每一種程式設計語言的語言伺服器。 下列範例會顯示發生於 Java 和 SASS 檔案使用者工作階段。

![java 和 sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>功能

並非所有語言伺服器可以都支援的通訊協定所定義的所有功能。 因此，用戶端和伺服器就會宣告其支援的功能集，透過 [功能]。 例如，伺服器會宣告，它可以處理 textDocument/定義 '的要求，但它可能會處理' 工作區/symbol ' 要求。 同樣地，用戶端可以宣布他們就能夠提供 ' 將儲存為' 通知之前儲存的文件，以便在伺服器可以計算要編輯的文件時自動格式化的文字編輯。

## <a name="integrating-a-language-server"></a>Language server 整合

語言伺服器實際整合到特定的工具不由語言伺服器通訊協定定義，且保留為工具實作者。 某些工具整合語言伺服器以一般方式有了延伸模組，可以啟動，並與任何一種語言伺服器通訊。 其他項目，例如 VS Code 中，建立每個語言伺服器的自訂延伸模組，以便延伸模組是仍然能夠提供一些自訂的語言功能。

若要簡化語言伺服器和用戶端實作，有程式庫或 Sdk 用戶端和伺服器組件。 這些程式庫可供不同的語言。 比方說，沒有[語言用戶端 npm 模組](https://www.npmjs.com/package/vscode-languageclient)以便與 VS Code 延伸模組，而另一個語言伺服器的整合[language server npm 模組](https://www.npmjs.com/package/vscode-languageserver)撰寫與使用 Node.js 語言伺服器通訊。 這是目前[清單](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations)支援程式庫。

## <a name="using-the-language-server-protocol-in-visual-studio"></a>使用 Visual Studio 中的語言伺服器通訊協定

* [新增語言伺服器通訊協定延伸模組](adding-an-lsp-extension.md)-了解如何整合到 Visual Studio 的語言伺服器。
