---
title: R 程式碼偵錯
description: Visual Studio 提供 R 的完整偵錯體驗，包括中斷點、附加、呼叫堆疊和檢查變數。
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: e3696cac00c726cffb76f29a1da2c503a15af2bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885816"
---
# <a name="debug-r-in-visual-studio"></a>在 Visual Studio 中偵錯 R

Visual Studio R 工具整合了完整的 Visual Studio 偵錯體驗 (請參閱 [Visual Studio 偵錯](../debugger/debugger-feature-tour.md)。 這項支援包括中斷點、附加至執行中處理序、檢查和監看變數，以及檢查呼叫堆疊。 本文接著會探索 R 和 RTVS 特有的偵錯功能。

啟動 r 專案中啟動 r 檔案的偵錯工具與其他專案類型相同：在偵錯工具工具列上使用 **debug**  >  **開始調試** 程式、 **F5** 鍵或 **來源啟動** 檔案：

![R 的偵錯工具 [開始] 按鈕](media/debugger-start-button.png)

若要變更啟動檔案，請在方案總管中以滑鼠右鍵按一下檔案，然後選取 [設定為啟動 R 指令碼]。

在所有情況下，啟動偵錯工具會在互動式視窗中「執行」檔案，這表示載入它並在那裡執行該檔案，如互動式視窗的輸出所示：

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

請注意，`rtvs::debug_source` 函式用來執行指令碼。 此函式是必要的，因為 RTVS 需要修改您的程式碼，以準備進行偵錯。 當使用任何 RTVS 執行命令，且已附加偵錯工具時，Visual Studio 會自動使用 `rtvs::debug_source`。

您也可以使用 **R 工具**  >  **會話**  >  **附加偵錯工具** 命令、 **Debug**  >  **attach to R 互動** 命令或互動式視窗工具列上的 [**附加偵錯工具**] 命令，直接從互動式視窗手動附加偵錯工具。 一旦您這麼做，您便必須負責執行您要偵錯的檔案。 如果您想要手動執行檔案，請確定您使用 `rtvs::debug_source`，而不是 R 中的一般 `source` 命令。

偵錯工具和互動式視窗之間的這項連接使您能夠更輕鬆地進行作業，例如使用不同的參數值來呼叫 (和偵錯) 函式。 例如，假設您在執行的檔案 (亦即它已載入至工作階段) 中有如下的函式︰

```R
add <- function(x, y) {
    return(x + y)
}
```

那麼您要在 `return` 陳述式上設定中斷點。 現在，在互動式視窗中，輸入 `add(4,5)` 會在中斷點上停止偵錯工具。

## <a name="environment-browser-in-the-interactive-window"></a>互動式視窗中的環境瀏覽器

當您在偵錯工具中停止時，您也會在[互動式視窗](interactive-repl-for-r-in-visual-studio.md)中的環境瀏覽器提示字元停止。 提示會顯示為 `Browse[n]>`，其中 n 為數字。

環境瀏覽器支援許多特殊命令︰

| 命令 | 描述 |
| --- | --- |
| n | 下一步︰執行程式碼檔案中的下一個陳述式 (與不進入函式相同)。 |
| s | 逐步執行︰執行程式碼檔案中的下一個陳述式，如果下一個陳述式是函式呼叫，則逐步執行函式範圍。 |
| f | 完成︰執行目前函式範圍的其餘部分，並傳回給呼叫端 (與跳離函式相同)。 |
| c、cont | 繼續︰執行程式直到下一個中斷點。 |
| Q | 結束：結束偵錯工作階段。 |
| 其中 | 顯示堆疊︰在互動式視窗中顯示呼叫堆疊。 |
| help | 顯示說明︰在互動式視窗中顯示可用的命令。 |
| &lt;expr&gt; | 評估 *expr* 中的運算式。 |

![互動式視窗中的環境瀏覽器](media/debugger-environment-browser.png)
