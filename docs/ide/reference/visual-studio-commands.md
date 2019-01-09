---
title: 命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7d4b2c4a3f7995fd00b9997e68a6bd7f64114d4a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909758"
---
# <a name="visual-studio-commands"></a>Visual Studio 命令

Visual Studio 的命令可讓您透過 [命令]  視窗、[即時運算]  視窗，或 [尋找/命令]  方塊來叫用命令。 在每種情況下，大於符號 (`>`) 都用來表示應執行命令，而不是搜尋或偵錯作業。

您可以在 [Keyboard, Environment Options] (鍵盤、環境選項)  對話方塊中找到命令和其語法的完整清單。

Visual Studio 命令的逸出字元是插入號 (^) 字元，這表示緊接著的字元會解譯為常值字元，而不是控制字元。 這可用來在參數或參數的值中嵌入一般引號 (")、空格、前置斜線、插入號或任何其他常值字元，但參數名稱除外。 例如，套用至物件的

```
>Edit.Find ^^t /regex
```

無論插入號位於引號內部或外部，功能都相同。 如果插入號是該程式行的最後一個字元，則會將其忽略。

在當地語系化版本的 IDE 中，您可以使用 IDE 的原生語言或英文輸入命令名稱。 例如，您可以在法文 IDE 中輸入 `File.NewFile` 或 `Fichier.NouveauFichier` 以執行相同的命令。

許多命令具有別名。 如需命令別名的清單，請參閱 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)。

下列命令需要引數和/或參數。

| 命令名稱： | 說明 |
| - | - |
| [加入現有項目](../../ide/reference/add-existing-item-command.md) | 將現有檔案新增至目前的方案，並開啟它。 |
| [加入現有專案](../../ide/reference/add-existing-project-command.md) | 將現有專案新增至目前的方案。 |
| [加入新項目](../../ide/reference/add-new-item-command.md) | 將新的方案項目，例如 .htm、.css、.txt 或框架組新增至目前的方案，並開啟它。 |
| [Alias](../../ide/reference/alias-command.md) | 針對完整命令、完整的命令和引數，或甚至是其他別名，建立新的別名。 |
| [評估陳述式](../../ide/reference/evaluate-statement-command.md) | 評估並顯示指定的陳述式。 |
| [Find](../../ide/reference/find-command.md) | 使用 [尋找和取代]  控制項提供的選項子集，搜尋檔案。 |
| [檔案中尋找](../../ide/reference/find-in-files-command.md) | 使用 [尋找和取代] [檔案中尋找](../../ide/find-in-files.md)。 |
| [到](../../ide/reference/go-to-command.md) | 將游標移至指定的程式行。 |
| [列出呼叫堆疊](../../ide/reference/list-call-stack-command.md) | 顯示目前的呼叫堆疊。 |
| [列出反組譯碼](../../ide/reference/list-disassembly-command.md) | 開始偵錯處理序，並可讓您指定處理錯誤的方式。 |
| [列出記憶體](../../ide/reference/list-memory-command.md) | 顯示指定的記憶體範圍的內容。 |
| [列出模組](../../ide/reference/list-modules-command.md) | 列出目前處理序的模組。 |
| [列出暫存器](../../ide/reference/list-registers-command.md) | 顯示暫存器的清單。 |
| [列出原始碼](../../ide/reference/list-source-command.md) | 顯示指定的原始程式碼程式行。 |
| [列出執行緒](../../ide/reference/list-threads-command.md) | 顯示目前程式中的執行緒清單。 |
| [記錄命令視窗輸出](../../ide/reference/log-command-window-output-command.md) | 將來自 [命令] 視窗的所有輸入和輸出複製到檔案中。 |
| [新增檔案](../../ide/reference/new-file-command.md) | 建立新的檔案，並將它新增至目前選取的專案。 |
| [開啟檔案](../../ide/reference/open-file-command.md) | 開啟現有的檔案，並可讓您指定編輯器。 |
| [開啟專案](../../ide/reference/open-project-command.md) | 開啟現有的專案，並可讓您將專案新增至目前的方案。 |
| [列印](../../ide/reference/print-command.md) | 評估運算式，並顯示結果或指定的文字。 |
| [快速監看式命令](../../ide/reference/quick-watch-command.md) | 顯示 [快速監看式]  對話方塊的 [運算式]  欄位中所選取或指定的文字。 |
| [取代](../../ide/reference/replace-command.md) | 使用 [尋找和取代]  控制項提供的選項子集，取代檔案中的文字。 |
| [檔案中取代](../../ide/reference/replace-in-files-command.md) | 使用 [檔案中取代](../../ide/replace-in-files.md)。 |
| [設定目前堆疊框架](../../ide/reference/set-current-stack-frame-command.md) | 可讓您檢視特定的堆疊框架。 |
| [設定目前執行緒](../../ide/reference/set-current-thread-command.md) | 可讓您檢視特定的執行緒。 |
| [設定基數](../../ide/reference/set-radix-command.md) | 判斷要檢視的位元組數目。 |
| [Shell](../../ide/reference/shell-command.md) | 如同在命令提示字元執行命令一般，從 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 內啟動程式。 |
| [ShowWebBrowser 命令](../../ide/reference/showwebbrowser-command.md) | 顯示您在網頁瀏覽器視窗內指定的 URL (不論是在整合式開發環境 (IDE) 內或 IDE 外部)。 |
| [啟動](../../ide/reference/start-command.md) | 開始偵錯處理序，並可讓您指定處理錯誤的方式。 |
| [路徑](../../ide/reference/symbol-path-command.md) | 設定目錄清單，以讓偵錯工具搜尋符號。 |
| [切換中斷點](../../ide/reference/toggle-breakpoint-command.md) | 根據中斷點目前的狀態以及在檔案中的目前位置，將其開啟或關閉。 |
| [監看式命令](../../ide/reference/watch-command.md) | 建立並開啟 [監看式]  視窗的指定執行個體。 |

## <a name="see-also"></a>請參閱

- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)