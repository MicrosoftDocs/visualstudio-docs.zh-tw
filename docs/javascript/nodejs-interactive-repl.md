---
title: 使用 Node.js REPL
description: Visual Studio 提供與 Node.js 執行階段互動的支援
ms.date: 12/04/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 9f13128bc552ffdb31b3f4a9315a3f9aa3543b0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962687"
---
# <a name="work-with-the-nodejs-interactive-window"></a>使用 Node.js 互動式視窗

適用於 Visual Studio 的 Node.js 工具包含用於已安裝 Node.js 執行階段的互動式視窗。 此視窗可讓您輸入 JavaScript 程式碼並立即查看結果並執行 npm 命令，以與目前的專案互動。 互動式視窗也稱為 REPL (**R** ead/**E** valuate/**P** rint **L** oop)。

## <a name="open-the-interactive-window"></a>開啟互動式視窗

若要開啟互動式視窗，請以滑鼠右鍵按一下 [方案總管] 中的 Node.js 專案節點，然後選取 [開啟 Node.js 互動式視窗]。

![專案操作功能表中的 Node.js 互動式視窗](../javascript/media/interactivewindow-open-from-project.png)

開啟 Node.js 互動式視窗的預設短暫按鍵是 **[CTRL] + K、N**。或者，您可以選擇 [ **View**  >  **Windows**  >  **Node.js Interactive window]**，從工具列開啟視窗。

## <a name="use-the-repl"></a>使用 REPL

開啟後，即可以輸入命令。

![Node.js 互動式視窗](../javascript/media/interactivewindow.png)

互動式視窗具有數個內建命令，以點前置詞開頭以便與您宣告的任何 JavaScript 函式區別。 支援的命令如下：

**.cls、.clear** 清除編輯視窗的內容，但不變更歷程記錄和執行內容。

**.help** 顯示指定命令的說明，如未指定，則顯示所有可用的命令和索引鍵繫結。

**.info** 顯示目前使用的 Node.js 可執行檔相關資訊。

**.npm** 執行 npm 命令。 如果方案包含多個專案，請使用 `.npm [projectname] <npm arguments>` 指定目標專案。

**.reset** 將執行環境重設為初始狀態，但保留歷程記錄。

**.save** 將目前的 REPL 工作階段儲存至檔案。