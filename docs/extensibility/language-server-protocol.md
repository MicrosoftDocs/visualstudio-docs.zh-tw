---
title: 語言伺服器協定概述 |微軟文件
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3bd5dce3cfb7022a8abb6397dc87b418144cbe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703107"
---
# <a name="language-server-protocol"></a>語言伺服器通訊協定

## <a name="what-is-the-language-server-protocol"></a>什麼是語言伺服器協定?

支援豐富的編輯功能,如原始碼自動完成或**進入定義**程式設計語言在編輯器或IDE傳統上是非常具有挑戰性的和耗時的。 通常,它需要用編輯器或 IDE 的程式設計語言編寫域模型(掃描器、解析器、類型檢查器、生成器等)。 例如,Eclipse CDT 外掛程式(在 Eclipse IDE 中支援 C/C++)是用 JAVA 編寫的,因為 Eclipse IDE 本身是用 JAVA 編寫的。 按照此方法,這意味著在 Visual Studio 代碼的 TypeScript 中實現 C/C++ 網域模型,在 Visual Studio 的 C# 中實現單獨的網域模型。

如果開發工具可以重用現有的特定於語言的庫,則創建特定於語言的域模型也容易得多。 但是,這些庫通常在程式設計語言本身中實現(例如,好的 C/C++域模型在 C/C++中實現)。 將 C/C++ 庫整合到用 TypeScript 編寫的編輯器中,在技術上是可能的,但很難做到。

### <a name="language-servers"></a>語言伺服器

另一種方法是在自己的進程中運行庫,並使用進程間通信與它通信。 來回發送的消息形成協定。 語言伺服器協定 (LSP) 是標準化開發工具和語言伺服器進程之間交換的消息的標準。 使用語言伺服器或惡魔並不是一個新的或新穎的想法。 像 Vim 和 Emacs 這樣的編輯器已經這樣做了一段時間,以提供語義自動完成支援。 LSP 的目標是簡化這些類型的集成,並為將語言功能公開為各種工具提供了一個有用的框架。

擁有通用協定可以重用語言域模型的現有實現,以最小的大驚小怪將程式設計語言功能整合到開發工具中。 語言伺服器後端介面可以用PHP、Python或JAVA編寫,LSP可以輕鬆地將其整合到各種工具中。 該協定在通用抽象級別工作,以便工具可以提供豐富的語言服務,而無需完全理解特定於底層域模型的細微差別。

## <a name="how-work-on-the-lsp-started"></a>LSP 工作如何開始

LSP 隨著時間的推移而演變,而今天它位於版本 3.0。 它開始於 OmniSharp 拾取語言伺服器的概念,為 C# 提供豐富的編輯功能。 最初,OmniSharp 使用帶有 JSON 有效負載的 HTTP 協定,並已整合到包括[Visual Studio 代碼](https://code.visualstudio.com)在內的多個編輯器中。

大約在同一時間,Microsoft 開始在 TypeScript 語言伺服器上工作,其理念是在 Emacs 和 Sublime Text 等編輯器中支援 TypeScript。 在此實現中,編輯器通過stdin/stdout與TypeScript伺服器進程進行通訊,並使用受V8調試器協定啟發的JSON負載來訪問請求和回應。 TypeScript 伺服器已整合到 TypeScript 崇高外掛程式和 VS 代碼中,以便進行豐富的 TypeScript 編輯。

集成了兩個不同的語言伺服器后,VS Code 團隊開始探索編輯器和 IDE 的通用語言伺服器協定。 公共協定使語言提供程式能夠創建可由不同 IDE 使用的單個語言伺服器。 語言伺服器消費者只需實現協定的用戶端一次。 這會導致語言提供者和語言消費者的雙贏。

語言伺服器協定從 TypeScript 伺服器使用的協議開始,透過更多受 VS Code 語言 API 啟發的語言功能擴展它。 該協定具有 JSON-RPC 的支援,用於遠端調用,由於其簡單性和現有庫。

VS Code 團隊通過實現多個 linter 語言伺服器對協定進行了原型設計,這些伺服器回應對檔進行(掃描)的請求,並返回一組檢測到的警告和錯誤。 目標是在使用者在文檔中編輯時對文件進行點皮,這意味著在編輯器會話期間將有許多林點請求。 保持伺服器正常運行是有意義的,這樣不需要為每個使用者編輯啟動新的林點進程。 實現了多個 linter 伺服器,包括 VS 代碼的 ESLint 和 TSLint 擴展。 這兩個 linter 伺服器都在 TypeScript/JavaScript 中實現,並在 Node.js 上運行。 它們共用一個庫,用於實現協定的用戶端和伺服器部分。

## <a name="how-the-lsp-works"></a>LSP 的工作原理

語言伺服器在其自己的進程中運行,Visual Studio 或 VS 代碼等工具通過 JSON-RPC 使用語言協定與伺服器通訊。 在專用進程中運行的語言伺服器的另一個優點是避免了與單個進程模型相關的性能問題。 如果用戶端和伺服器都寫入 Node.js,則實際傳輸通道可以是 stdio、套接字、命名管道或節點 ipc。

下面是工具和語言伺服器在常規編輯工作階段期間如何通訊的範例:

![lsp 流程圖](media/lsp-flow-diagram.png)

* **使用者在工具中打開檔(稱為文檔):** 該工具通知語言伺服器文件已打開("文字文檔/已打開"。)。 從現在起,文檔內容的真相不再在文件系統上,而由工具保存在記憶體中。

* **使用者進行編輯**:該工具通知伺服器文檔更改("文本文檔/didChange"),並且程式的語義資訊由語言伺服器更新。 發生這種情況時,語言伺服器會分析此資訊,並將檢測到的錯誤和警告("文本文檔/發佈診斷")通知工具。

* **使用者對編輯器中的符號執行「轉到定義」:** 該工具發送包含兩個參數的「文本文檔/定義」請求:(1) 文件 URI 和 (2) 從「轉到定義」請求啟動到伺服器的文本位置。 伺服器使用文檔URI和符號定義在文檔中的位置進行回應。

* **使用者關閉文件(檔案):** 從該工具發送"文本文檔/didClose"通知,通知語言伺服器文件現在不再記憶體,並且檔案系統上的當前內容是最新的。

此示例說明了協定如何在編輯器功能(如"轉到定義"、"尋找所有引用")級別與語言伺服器通訊。 協定使用的數據類型是編輯器或 IDE"數據類型",如當前打開的文本文檔和游標的位置。 數據類型不在通常提供抽象語法樹和編譯器符號(例如,解析類型、命名空間等)的程式設計語言域模型的級別。這大大簡化了協定。

現在,讓我們更詳細地查看"文本文檔/定義"請求。 下面是用戶端工具和C++文檔中"轉到定義"請求的語言伺服器之間的有效負載。

這是要求:

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

這是回應:

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

回顧過去,在編輯器級別而不是程式設計語言模型級別描述數據類型是語言伺服器協定成功的原因之一。 與標準化不同程式設計語言的抽象語法樹和編譯器符號相比,標準化文本文檔 URI 或游標位置要簡單得多。

當使用者使用不同的語言時,VS 代碼通常會為每個程式設計語言啟動一個語言伺服器。 下面的範例顯示了使用者在 JAVA 和 SASS 檔上工作的工作階段。

![賈瓦和薩斯](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>功能

並非所有語言伺服器都可以支援協議定義的所有功能。 因此,用戶端和伺服器通過"功能"宣佈其支援的功能集。 例如,伺服器宣佈可以處理"文本文檔/定義"請求,但可能無法處理"工作區/符號"請求。 同樣,用戶端可以宣佈,在保存文檔之前,他們可以提供"即將儲存"的通知,以便伺服器可以計算文本編輯以自動格式化編輯的文檔。

## <a name="integrating-a-language-server"></a>整合語言伺服器

語言伺服器實際整合到特定工具時,語言伺服器協定不定義,並留給工具實現者。 某些工具通過具有可以啟動和與任何類型的語言伺服器對話的擴展來一般地集成語言伺服器。 其他擴展(如 VS 代碼)則創建每個語言伺服器的自定義擴展,以便擴展仍然能夠提供一些自定義語言功能。

為了簡化語言伺服器和用戶端的實現,用戶端和伺服器部件有庫或 SDK。 這些庫提供不同的語言。 例如,有一種語言[用戶端 npm 模組](https://www.npmjs.com/package/vscode-languageclient),用於簡化語言伺服器與 VS 程式碼擴展的整合,另一種語言伺服器[npm 模組](https://www.npmjs.com/package/vscode-languageserver)使用 Node.js 編寫語言伺服器。 這是支援函式庫的目前[清單](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations)。

## <a name="using-the-language-server-protocol-in-visual-studio"></a>在視覺化工作室中使用語言伺服器協定

* [添加語言伺服器協定擴展](adding-an-lsp-extension.md)- 瞭解如何將語言伺服器集成到可視化工作室中。
