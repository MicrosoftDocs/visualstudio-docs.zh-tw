---
title: "語言伺服器通訊協定概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 269c19410207e47f233eadfa984a84a7c8445743
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2018
---
# <a name="language-server-protocol"></a>語言伺服器通訊協定

## <a name="what-is-the-language-server-protocol"></a>什麼是語言伺服器通訊協定？

支援豐富的編輯功能類似來源的程式碼自動完成或**移至定義**編輯器或 IDE 中的程式語言為傳統上非常具挑戰性，而耗用的時間。 通常需要撰寫編輯器或 IDE 的程式設計語言中的網域模型 （掃描器、 剖析器、 型別檢查、 產生器等等）。 例如，Eclipse CDT 外掛程式，可提供支援 C/c + + Eclipse IDE 中採用 Java，因為 Eclipse IDE 本身以 Java 撰寫。 在這種方式，則表示在 C# 中實作 C/c + + 中的網域模型 TypeScript for Visual Studio 程式碼，以及不同的網域模型，適用於 Visual Studio。

建立語言特定的網域模型也是開發工具可重複使用現有的語言特有程式庫的更加容易。 不過，這些程式庫通常會實作的程式語言本身 （比方說，好 C/c + + 網域模型會在 C/c + + 中實作）。 C/c + + 程式庫整合寫入 typescript 編輯器技術上來說是可行的但不困難。

### <a name="language-servers"></a>伺服器語言

另一個方法是在自己的處理序中執行的程式庫和用來與它溝通的處理序間通訊。 來回傳送的訊息會形成一種通訊協定。 語言伺服器通訊協定 (LSP) 是產品的標準化開發工具和語言伺服器處理序之間交換的訊息。 使用語言伺服器或砍殺並不是新的或嶄新的做法。 編輯器 Vim 等 Emacs 進行這段時間，以提供支援語意的自動完成。 LSP 的目標是簡化這類的整合，提供有用的架構來公開各種不同工具的語言功能。

常見的通訊協定可讓程式設計到最少複雜的開發工具的語言功能，重複使用現有的語言的網域模型實作的整合。 無法以 PHP、 Python 或 Java 撰寫語言伺服器端和 LSP 可讓它易於整合到各種不同的工具。 在常見的抽象層級的通訊協定運作，如此工具可提供豐富的語言服務，而不必完全了解基礎網域模型的特定細節。

## <a name="how-work-on-the-lsp-started"></a>如何啟動 LSP

隨著時間不斷演進 LSP，現在它從 3.0 版。 它啟動時的語言伺服器概念已由 OmniSharp 提供豐富的編輯功能的 C# 來收取。 一開始，OmniSharp JSON 承載搭配使用 HTTP 通訊協定和已整合至數個編輯器包括[Visual Studio Code](https://code.visualstudio.com)。

大約在同一時間，Microsoft 會啟動具有支援 TypeScript 像 Emacs 和適的文字編輯器中的想法的 TypeScript 語言伺服器上運作。 在此實作中，編輯器通訊透過 stdin/stdout 與 TypeScript 伺服器處理序，並要求和回應使用 JSON 裝載 V8 偵錯工具通訊協定所啟發。 TypeScript 伺服器已經整合的 TypeScript 適外掛程式和 VS Code 的豐富的 TypeScript 編輯。

之後整合兩個不同的語言伺服器之後，VS Code 小組來開始探索一般的語言伺服器通訊協定的編輯器和 Ide。 常見的通訊協定可讓您建立可由不同的 Ide 使用單一語言伺服器語言提供者。 語言 server 取用者只需要實作通訊協定的用戶端一次。 這會導致 win win 情況語言提供者和語言取用者。

語言伺服器通訊協定啟動 TypeScript 伺服器，展開與啟發 VS Code 語言應用程式開發介面的更多語言功能所使用的通訊協定。 由於其簡易性和現有的程式庫的遠端叫用的通訊協定支援 JSON rpc。

在 VS 程式碼的小組原型 lint （掃描） 要求的通訊協定，藉由實作數個 linter 語言伺服器回應檔案，並傳回一組的偵測到的警告和錯誤。 目標是為了 lint 檔案做為使用者編輯文件，這表示編輯器工作階段期間將會多 linting 要求中。 它沒有任何意義，讓註冊的伺服器和執行，讓新的 linting 程序不需要啟動的每個使用者編輯。 實作數個 linter 伺服器，包括 VS Code ESLint 和 TSLint 延伸模組。 這兩部 linter 伺服器會同時實作 TypeScript/javascript 和 Node.js 上執行。 它們共用實作通訊協定的用戶端和伺服器部分的程式庫。

## <a name="how-the-lsp-works"></a>LSP 的運作方式

以自己的處理序執行語言伺服器和工具，例如 Visual Studio 或 VS 程式碼與使用的語言通訊協定透過 JSON RPC 伺服器通訊。 語言伺服器作業系統專用的處理序中的另一個好處是可以避免與單一處理序模型相關的效能問題。 實際的傳輸通道可以是如果用戶端和伺服器以 Node.js stdio、 通訊端、 具名的管道或節點 ipc。

以下範例工具和語言伺服器如何通訊期間常式編輯工作階段：

![lsp 流程圖](media/lsp-flow-diagram.png)

* **使用者在工具中開啟檔案 （稱為文件）**： 此工具會通知語言伺服器已開啟的文件 (' textDocument/didOpen ')。 從現在起，文件內容的真相不再位於檔案系統，但保留記憶體中的工具。

* **使用者可編輯**： 此工具會通知伺服器與變更相關的文件 (' textDocument/didChange ')，並由語言 server 更新程式的語意資訊。 發生這種情況，因為語言伺服器會分析此資訊，並通知偵測到的錯誤和警告 (' textDocument/publishDiagnostics ') 的工具。

* **使用者在編輯器中的符號上執行 移至定義 」**： 此工具會傳送具有兩個參數 'textDocument/定義' 要求: (1) 的文件 URI 和 （2） 從 移至定義要求起始伺服器所在的文字位置。 伺服器會回應內文件的符號定義的位置與文件 URI。

* **使用者關閉文件 （檔案）**: 'textDocument/didClose' 通知從工具，通知的語言伺服器文件現在不再記憶體，且目前的內容現在是檔案系統上最新狀態。

此範例說明如何與語言伺服器層級的編輯器功能，例如 「 移至定義]，[尋找所有參考 」 通訊的通訊協定。 通訊協定所使用的資料類型為編輯器或 IDE '資料類型' 像是目前開啟的文字文件和游標的位置。 資料型別並非在程式設計的語言網域模型通常會提供抽象語法樹狀目錄和編譯器符號 （例如，解決類型、 命名空間，...） 層級。這樣可大幅簡化通訊協定。

現在讓我們看看 textDocument/定義 ' 中的要求更多詳細資料。 以下是用戶端工具和 c + + 文件中的 移至定義 」 要求的語言伺服器之間的裝載。

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

回顧以往，描述在編輯器的層級，而不是在程式設計語言模型的層級的資料型別是語言伺服器通訊協定成功的原因之一。 就簡單多了標準化文字文件 URI 或與抽象語法樹狀目錄和編譯器符號標準化不同的程式設計語言比較，資料指標位置。

當使用者正在使用不同的語言時，VS 程式碼通常會啟動每一種程式設計語言的語言伺服器。 下列範例顯示在工作階段，其中使用者可以用於 Java 和 SASS 檔案上。

![java 和 sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>功能

並非每個語言伺服器可以支援的通訊協定所定義的所有功能。 因此，用戶端和伺服器會宣告其支援的功能集，透過 [功能]。 例如，伺服器會宣告，它可以處理 'textDocument/定義' 的要求，但它可能無法處理 '工作區/symbol' 要求。 同樣地，用戶端才能宣告歡迎畫面是能夠提供 ' 將儲存為' 通知之前儲存的文件，如此伺服器就可以計算自動格式設定的已編輯的文件的文字編輯內容。

## <a name="integrating-a-language-server"></a>整合伺服器語言

語言伺服器實際整合到特定的工具不由語言伺服器通訊協定定義，並會保留給工具實作項。 某些工具整合語言伺服器一般有可以啟動並與任何一種語言伺服器溝通的延伸模組。 其他人，像是 VS 程式碼，建立每個語言伺服器的自訂延伸模組，讓擴充功能就仍然可以提供某些自訂語言功能。

若要簡化語言伺服器和用戶端實作，沒有文件庫或 Sdk 用戶端和伺服器組件。 這些程式庫會提供不同的語言。 例如，沒有[語言用戶端 npm 模組](https://www.npmjs.com/package/vscode-languageclient)語言伺服器整合到 VS Code 擴充功能，而另一個，以便[語言伺服器 npm 模組](https://www.npmjs.com/package/vscode-languageserver)撰寫使用 Node.js 語言伺服器。 這是目前[清單](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations)支援程式庫。

## <a name="using-the-language-server-protocol-in-visual-studio"></a>使用 Visual Studio 中的語言伺服器通訊協定

* [加入語言伺服器通訊協定的延伸](adding-an-lsp-extension.md)-了解 Visual Studio 中的語言伺服器整合。
