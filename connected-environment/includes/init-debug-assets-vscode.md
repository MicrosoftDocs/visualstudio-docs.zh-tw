---
ms.topic: include
ms.openlocfilehash: dbf7482acb02c6347c9c0d0765ef962cfb43a050
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
## <a name="initialize-debug-assets-with-the-vs-code-extension"></a>使用 VS Code 延伸模組初始化偵錯資產
我們首先需要設定程式碼專案，讓 VS Code 與我們在 Azure 中的開發環境通訊。 已連線環境的 VS Code 延伸模組會提供協助程式命令來設定偵錯組態。 

開啟 [命令選擇區] (使用 [檢視] | [命令選擇區] 功能表)，並使用自動完成鍵入，並選取這個命令：`Connected Environment: Create configuration files for connected development`。 

這會在 `.vscode` 資料夾下新增已連線環境的偵錯組態。

![](../media/vsce-command-palette.png)

> [!Note]
> **重要**：因為一個 Bug，請先關閉再重新開啟 VS Code，然後繼續作業。