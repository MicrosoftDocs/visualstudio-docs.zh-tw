---
title: 使用追蹤點的記錄資訊 |Microsoft Docs
description: 設定追蹤點以將資訊記錄到輸出，而不需要修改或停止您的程式碼。 只需在 [中斷點設定] 的 [動作] 核取方塊下指定輸出字串。
ms.custom: SEO-VS-2020
ms.date: 10/28/2019
ms.topic: how-to
helpviewer_keywords:
- tracepoints, about tracepoints
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 144f83b1be0c3a21aa5cb244f8498f61e3ef380a
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150089"
---
# <a name="log-info-to-the-output-window-using-tracepoints-in-visual-studio"></a>使用 Visual Studio 中的追蹤點將資訊記錄到輸出視窗

追蹤點可讓您在可設定的條件下將資訊記錄到輸出視窗，而不需要修改或停止您的程式碼。 這項功能支援兩種 managed 語言 (c #、Visual Basic、F # ) 和機器碼，以及 JavaScript 和 Python 等語言。

## <a name="let39s-take-an-example"></a>讓&#39;進行範例

下列範例程式是 `for` 具有計數器變數的簡單迴圈，每次迴圈執行另一次反覆運算時都會增加一個。

![計數器範例](../debugger/media/counterexample.png "計數器範例")

## <a name="set-tracepoints-in-source-code"></a>在原始程式碼中設定追蹤點

您可以在 [**中斷點設定**] 視窗中的 [**動作**] 核取方塊底下指定輸出字串，以設定追蹤點。

1. 若要初始化追蹤點，請先按一下您要設定追蹤點之行號左邊的裝訂邊。

   ![中斷點初始化](../debugger/media/breakpointinitialization.png "中斷點初始化")

2. 將滑鼠停留在紅色圓圈上方，然後按一下齒輪圖示。
3. 這會開啟 [ **中斷點設定** ] 視窗。

   ![中斷點視窗](../debugger/media/breakpointwindow.png "中斷點視窗")

4. 選取 [ **動作** ] 核取方塊。

   ![核取的動作方塊](../debugger/media/checkedactionsbox.png "核取的動作方塊")

   請注意紅色圓圈如何改變為菱形，表示您已從中斷點切換至追蹤點。

5. 在 [輸出視窗] 文字方塊中輸入您想要登入 [ **顯示訊息** ] 的訊息 (如需詳細資訊，請參閱本文稍後的章節) 。

   現在已設定您的追蹤點。 &quot; &quot; 如果您只想要將部分資訊記錄到輸出視窗，請按 [關閉] 按鈕。

6. 如果您想要新增條件來判斷是否顯示訊息，請選取 [ **條件** ] 核取方塊。

   ![核取條件方塊](../debugger/media/checkedconditionsbox.png "核取條件方塊")

   您有三個條件選項： **條件運算式**、 **篩選** 和 **計數**。

## <a name="actions-menu"></a>[動作] 功能表

此功能表可讓您將訊息記錄至 [輸出] 視窗。 將您想要輸出的字串輸入至訊息方塊， (不需要任何引號) 。 如果您想要顯示變數的值，請務必將它括在大括弧內。

例如，如果您想要 `counter` 在輸出主控台中顯示變數的值，請在 [訊息] 文字方塊中輸入 {counter}。

![計數器輸出訊息](../debugger/media/counteroutputmessage.png "計數器輸出訊息")

如果您按一下 [ **關閉** ]，然後將程式調試 (**F5**) ，您會在 [輸出] 視窗中看到下列輸出。

![輸出視窗中的動作訊息](../debugger/media/actionsmessageinoutputwindow.png "輸出視窗中的動作訊息")

您也可以使用特殊關鍵字來顯示更明確的資訊。 輸入完全如下所示的關鍵字 (在每個關鍵字前面使用 "$"，關鍵字本身的所有 caps) 。

| 關鍵字 | 顯示的內容 |
| --- | --- |
| $ADDRESS | 目前指令 |
| $CALLER | 呼叫函式名稱 |
| $CALLSTACK | 呼叫堆疊 |
| $FUNCTION | 目前的函式名稱 |
| $PID | 處理序識別碼 |
| $PNAME | 程序名稱 |
| $TID | 執行緒識別碼 |
| $TNAME   | 執行緒名稱 |
| $TICK | 從 Windows GetTickCount)  (的滴答計數 |

## <a name="conditions-menu"></a>條件功能表

條件可讓您篩選輸出訊息，因此它們只會在某些情況下顯示。 有三種主要的條件可供您使用。

### <a name="conditional-expression"></a>條件運算式
針對條件運算式，只有在符合特定條件時，才會顯示輸出訊息。

在條件運算式中，您可以設定追蹤點，在特定條件為 true 或變更時輸出訊息。 例如，如果您只想要在迴圈的反覆運算期間顯示計數器的值 `for` ，您可以選取 [ **為 true** ] 選項，然後 `i%2 == 0` 在 [訊息] 文字方塊中輸入。

![條件運算式為 True](../debugger/media/conditionalexpressionistrue.png "條件運算式為 True")

如果您想要在迴圈的反復專案變更時列印計數器的值 `for` ，請選取 [ **變更時** ] 選項，並 `i` 在 [訊息] 文字方塊中輸入。

![變更時的條件運算式](../debugger/media/conditionalexpressionwhenchanged.png "變更時的條件運算式")

當不同的程式設計語言時，[  **變更時**  ] 選項的行為會有所不同。

- 在機器碼中，偵錯工具不會將第一次評估條件視為變更，因此不會在第一次評估時叫用追蹤點。
- 針對 managed 程式碼，偵錯工具會在選取 [ **變更時**  ] 之後，于第一次評估時叫用追蹤點。

如需更完整的查看您在設定條件時可以使用的有效運算式，請參閱 [偵錯工具中的運算式](expressions-in-the-debugger.md)。

### <a name="hit-count"></a>點擊計數
計數條件可讓您只在設定追蹤點的程式程式碼執行指定的次數之後，才傳送輸出。

針對 [計數]，您可以選擇在設定追蹤點的程式程式碼執行的次數等於、為多個或大於或等於指定的計數值時，輸出訊息。 選擇最符合您需求的選項，並在欄位中輸入整數值 (例如，5) 代表感興趣的反復專案。

![條件運算式計數](../debugger/media/conditionalexpressionhitcount.png "條件運算式計數")

### <a name="filter"></a>篩選
針對篩選準則，指定要為其顯示哪些裝置、進程或執行緒輸出。

![條件運算式篩選](../debugger/media/conditionalexpressionfilter.png "條件運算式篩選")

篩選條件運算式的清單：

- MachineName = "名稱"
- ProcessId = 值
- ProcessName ="名稱"
- ThreadId = 值
- ThreadName = "名稱"

用雙引號括住字串 (例如名稱) 。 您可以輸入沒有引號的值。 您可以使用 `&` (`AND`) 、 `||` (`OR`) 、 `!` (`NOT`) 和括弧來合併子句。

## <a name="considerations"></a>考量

雖然追蹤點的目的是要讓偵錯工具更清楚、更順暢，但在使用時，您應該注意一些需要注意的事項。

有時候當您檢查物件的屬性或屬性時，它的值可能會變更。 如果值在檢查期間變更，則不是追蹤點功能本身所造成的錯誤。 不過，使用追蹤點來檢查物件，並不會避免這些意外的修改。

運算式在 **動作** 訊息方塊中的評估方式可能與您目前用來開發的語言不同。 例如，若要輸出字串，您不需要以引號括住訊息，即使您通常會在使用或時 `Debug.WriteLine()` 使用 `console.log()` 。 此外， () 輸出運算式的大括弧語法， `{ }` 也可能與在開發語言中輸出值的慣例不同。 不過 (不過，大括弧 () 中的內容 `{ }` 仍應使用開發語言的語法) 來撰寫。

如果您嘗試將即時應用程式進行偵測，並尋找類似的功能，請參閱快照偵錯工具中的記錄點功能。 快照偵錯工具是用來調查實際執行應用程式中問題的工具。 記錄點也可讓您將訊息傳送至輸出視窗，而不需要修改原始程式碼，也不會影響執行中的應用程式。 如需詳細資訊，請參閱 [即時 Azure 應用程式的偵錯工具](../debugger/debug-live-azure-applications.md)。

## <a name="see-also"></a>另請參閱

- [什麼是偵錯？](../debugger/what-is-debugging.md)
- [使用 Visual Studio 撰寫更好的 c # 程式碼](../debugger/write-better-code-with-visual-studio.md)
- [先查看調試](../debugger/debugger-feature-tour.md)
- [偵錯工具中的運算式](expressions-in-the-debugger.md)
- [使用中斷點](../debugger/using-breakpoints.md)
- [對即時 Azure 應用程式進行偵錯工具](../debugger/debug-live-azure-applications.md)
