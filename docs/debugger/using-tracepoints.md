---
title: 在偵錯工具中使用追蹤點 |Microsoft Docs
ms.date: 9/17/2019
ms.topic: conceptual
helpviewer_keywords:
- tracepoints, about tracepoints
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 263657213f1720eaca7a0462bb31585adaacf9bb
ms.sourcegitcommit: 6244689e742e551e7b6933959bd42df56928ece3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72516401"
---
# <a name="use-tracepoints-in-the-visual-studio-debugger"></a>在 Visual Studio 偵錯工具中使用追蹤點

追蹤點可讓您將資訊記錄到 [可設定的條件] 下的 [輸出] 視窗，而不必修改或停止您的 這項功能支援 managed 和機器碼，以及數種語言，例如 JavaScript 和C#。

## <a name="let39s-take-an-example"></a>讓&#39;我們來看一個範例

下列範例程式是一個簡單的 `for` 迴圈，其中包含一個 counter 變數，每次迴圈執行另一個反復專案時，都會增加一個。

![計數器範例](../debugger/media/counterexample.png "計數器範例")

## <a name="set-tracepoints-in-source-code"></a>在原始程式碼中設定追蹤點

您可以在 [**中斷點設定**] 視窗中的 [**動作**] 核取方塊底下指定輸出字串，以設定追蹤點。

1. 若要初始化追蹤點，請先按一下您要設定追蹤點之行號左側的裝訂邊。

   ![中斷點初始化](../debugger/media/breakpointinitialization.png "中斷點初始化")

2. 將滑鼠停留在紅色圓形上，然後按一下齒輪圖示。
3. 這會開啟 [**中斷點設定**] 視窗。

   ![中斷點視窗](../debugger/media/breakpointwindow.png "中斷點視窗")

4. 選取 [**動作**] 核取方塊。

   ![[已檢查的動作] 方塊](../debugger/media/checkedactionsbox.png "[已檢查的動作] 方塊")

   請注意紅色圓形如何變更為菱形，表示您已從中斷點切換到追蹤點。

5. 在 [**輸出視窗**] 文字方塊中輸入您想要登入的訊息（如需詳細資訊，請參閱本文稍後的章節）。

   現在已設定您的追蹤點。 如果您只想要將一些資訊記錄到輸出視窗，請按 [&quot;Close &quot;] 按鈕。

6. 如果您想要新增條件來判斷是否顯示您的訊息，請選取 [**條件**] 核取方塊。

   ![核取的條件方塊](../debugger/media/checkedconditionsbox.png "核取的條件方塊")

   您有三個條件選擇： [**條件運算式**]、[**篩選**] 和 [**計數**]。

## <a name="actions-menu"></a>動作功能表

此功能表可讓您將訊息記錄至 [輸出] 視窗。 在訊息方塊中輸入您要輸出的字串（不需要引號）。 如果您想要顯示變數的值，請務必將其括在大括弧內。

例如，如果您想要在輸出主控台中顯示 `counter` 變數的值，請在 [訊息] 文字方塊中輸入 {counter}。

![計數器輸出訊息](../debugger/media/counteroutputmessage.png "計數器輸出訊息")

如果您按一下 [**關閉**]，然後再 debug 程式（**F5**），您會在 [輸出] 視窗中看到下列輸出。

![輸出視窗中的動作訊息](../debugger/media/actionsmessageinoutputwindow.png "輸出視窗中的動作訊息")

您也可以使用特殊關鍵字來顯示更具體的資訊。 輸入完全如下所示的關鍵字（在每個關鍵字前面使用 "$"，並將所有的大寫用於關鍵字本身）。

| 關鍵字 | 顯示的內容 |
| --- | --- |
| $ADDRESS | 目前指令 |
| $CALLER | 呼叫函式名稱 |
| $CALLSTACK | 呼叫堆疊 |
| $FUNCTION | 目前的函式名稱 |
| $PID | 處理序 ID |
| $PNAME | 處理序名稱 |
| $TID | 執行緒 ID |
| $TNAME   | 執行緒名稱 |
| $TICK | 滴答計數（來自 Windows GetTickCount） |

## <a name="conditions-menu"></a>條件功能表

條件可讓您篩選輸出訊息，因此它們只會在特定情況下顯示。 有三種主要的條件可供您使用。

### <a name="conditional-expression"></a>條件運算式
針對條件運算式，只有在符合特定條件時，才會顯示輸出訊息。

針對條件運算式，您可以設定追蹤點，以便在特定條件為 true 或變更時輸出訊息。 例如，如果您只想要在 `for` 迴圈的反復專案中顯示計數器的值，您可以選取 [**為 true** ] 選項，然後在 [消息] 文字方塊中輸入 `i%2 == 0`。

![條件運算式為 True](../debugger/media/conditionalexpressionistrue.png "條件運算式為 True")

如果您想要在 `for` 迴圈的反復專案變更時列印計數器的值，請選取 [**變更時**] 選項，並在 [訊息] 文字方塊中輸入 `i`。

![變更時的條件運算式](../debugger/media/conditionalexpressionwhenchanged.png "變更時的條件運算式")

針對不同的程式設計語言，[**變更時**] 選項的行為不同。

- 針對機器碼，偵錯工具不會將條件的第一個評估視為變更，因此不會在第一次評估時叫用追蹤點。
- 對於 managed 程式碼，偵錯工具會在選取 [**變更時**] 之後的第一次評估時叫用追蹤點。

如需更完整的查看您可以在設定條件時使用的有效運算式，請參閱[偵錯工具中的運算式](expressions-in-the-debugger.md)。

### <a name="hit-count"></a>計數
計數條件可讓您只在設定了追蹤點的程式程式碼執行指定的次數之後，才傳送輸出。

針對 [計數]，您可以選擇在設定追蹤點的程式程式碼執行的次數等於、為的倍數，或大於或等於指定的 [計數] 值時，輸出訊息。 選擇最符合您需求的選項，並在代表該反復專案的欄位中輸入整數值（例如5）。

![條件運算式計數](../debugger/media/conditionalexpressionhitcount.png "條件運算式計數")

### <a name="filter"></a>篩選
針對篩選準則，指定顯示的裝置、進程或執行緒輸出。

![條件運算式篩選](../debugger/media/conditionalexpressionfilter.png "條件運算式篩選")

篩選條件運算式的清單：

- MachineName = "名稱"
- ProcessId = 值
- ProcessName ="名稱"
- ThreadId = 值
- ThreadName = "名稱"

以雙引號括住字串（例如名稱）。 可以輸入沒有引號的值。 您可以使用 `&` （`AND`）、`||` （`OR`）、`!` （`NOT`）和括弧來結合子句。

## <a name="considerations"></a>考量

雖然追蹤點的目的是要讓您以更簡潔且更流暢的經驗進行偵錯工具，但在使用這些功能時，您應該注意一些考慮。

有時候當您檢查物件的屬性或屬性時，其值可能會變更。 這不是追蹤點功能本身所造成的 bug，但值得一提的是，使用追蹤點來檢查物件並不會避免這些意外的修改。

在 [**動作**] 訊息方塊中評估運算式的方式，可能與您目前用來開發的語言不同。 例如，若要輸出字串，您不需要以引號括住訊息，即使您通常會在使用 `Debug.WriteLine()` 或 `console.log()` 時也一樣。 此外，對輸出運算式的大括弧語法（`{ }`）也可能與在開發語言中輸出值的慣例不同。 （不過，大括弧（`{ }`）內的內容仍應使用您的開發語言語法來撰寫）。

如果您想要檢查即時應用程式並尋找類似的功能，請查看快照偵錯工具中的記錄點功能。 快照偵錯工具是用來調查生產應用程式中問題的工具。 記錄點也可讓您將訊息傳送至輸出視窗，而不需要修改原始程式碼，也不會影響執行中的應用程式。 如需詳細資訊，請參閱[即時 Azure 應用程式](../debugger/debug-live-azure-applications.md)。

## <a name="see-also"></a>請參閱

- [什麼是偵錯？](../debugger/what-is-debugging.md)
- [使用 Visual Studio C#撰寫更好的程式碼](../debugger/write-better-code-with-visual-studio.md)
- [第一次查看調試](../debugger/debugger-feature-tour.md)
- [偵錯工具中的運算式](expressions-in-the-debugger.md)
- [使用中斷點](../debugger/using-breakpoints.md)
- [即時調試 Azure 應用程式](../debugger/debug-live-azure-applications.md)
