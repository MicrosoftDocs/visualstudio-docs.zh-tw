---
title: 即時運算視窗
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3947c2f16be4e5c0d8054e48a46981aa22475423
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931945"
---
# <a name="immediate-window"></a>即時運算視窗

[即時運算] 視窗用來偵錯和評估運算式、執行陳述式、列印變數值等等。 它可讓您在偵錯期間，輸入開發語言要評估或執行的運算式。

若要顯示 [即時運算] 視窗，請開啟專案進行編輯，然後選擇 [偵錯] > [視窗] > [即時運算]，或按 **Ctrl**+**Alt**+**I**。 您也可以在 [命令] 視窗中輸入 **Debug.Immediate**。

您可以使用 [即時運算] 視窗發出個別的 Visual Studio 命令。 可用的命令包括 `EvaluateStatement`，它可用來指派值給變數。 [即時運算] 視窗也支援 IntelliSense。

## <a name="display-the-values-of-variables"></a>顯示變數的值

在對應用程式進行偵錯時，[即時運算] 視窗特別好用。 例如，若要檢查 `varA` 變數的值，您可以使用 [Print 命令](../../ide/reference/print-command.md)：

```cmd
>Debug.Print varA
```

問號 (?) 是 `Debug.Print` 的別名，因此，此命令也可以撰寫為：

```cmd
>? varA
```

此命令的兩個版本都會傳回都會傳回變數 `varA` 的值。

> [!TIP]
> 若要在 [即時運算] 視窗中發出 Visual Studio 命令，就必須在命令前面加上大於符號 (>)。 若要輸入多個命令，請切換到 [命令] 視窗。

## <a name="design-time-expression-evaluation"></a>設計階段運算式評估

您可以在設計階段使用 [即時運算] 視窗來執行函式或副程式。

### <a name="execute-a-function-at-design-time"></a>在設計階段執行函式

1. 將下列程式碼複製到 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 主控台應用程式中：

   ```vb
   Module Module1

       Sub Main()
           MyFunction(5)
       End Sub

       Function MyFunction(ByVal input as Integer) As Integer
           Return input * 2
       End Function

   End Module
   ```

2. 在 [偵錯] 功能表上，按一下 [視窗]，然後按一下 [即時運算]。

3. 在 [即時運算] 視窗中鍵入 `?MyFunction(2)`，然後按 **Enter**。

    [即時運算] 視窗會執行 `MyFunction`，並顯示 `4`。

如果函式或副程式含有中斷點，Visual Studio 會在適當的點中斷執行。 然後，您就可以使用偵錯工具視窗來檢查程式狀態。 如需詳細資訊，請參閱[逐步解說：在設計階段進行偵錯](../../debugger/walkthrough-debugging-at-design-time.md)。

您無法在必須啟動執行環境的專案類型中使用設計階段運算式評估，這些專案類型包括 [!INCLUDE[trprVSTOshort](../../ide/reference/includes/trprvstoshort_md.md)] 專案、Web 專案、智慧型裝置專案和 SQL 專案。

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>在多專案的解決方案中評估設計階段運算式

在建立設計階段運算式評估的內容時，Visual Studio 會參考方案總管中目前選取的專案。 若未在方案總管中選取任何專案，Visual Studio 會嘗試對啟動專案評估函式。 如果無法在目前內容中評估函式，就會收到錯誤訊息。 如果您試圖評估的函式不是在方案的啟始專案中，而且發生錯誤，請嘗試在方案總管中選取專案，然後重新評估一次。

## <a name="enter-commands"></a>輸入命令

在 [即時運算] 視窗中發出 Visual Studio 命令時，必須輸入大於符號 (>)。 使用**向上鍵**和**向下鍵**捲動先前發出的命令。

|工作|方案|範例|
|----------|--------------|-------------|
|評估運算式。|在運算式前面加上問號 (?)。|`? a+b`|
|在即時模式中時，暫時進入命令模式 (以執行單一命令)。|輸入命令，並在前面加上大於符號 (>)。|`>alias`|
|切換到 [命令] 視窗。|將 `cmd` 輸入到視窗，並在前面加上大於符號 (>)。|`>cmd`|
|切換回 [即時運算] 視窗。|將 `immed` 輸入到視窗，但沒有大於符號 (>)。|`immed`|

## <a name="mark-mode"></a>標記模式

當您在 [即時運算] 視窗中按一下之前任一行時，會自動切換至 [標記] 模式。 這可讓您像在任何文字編輯器中一樣地選取、編輯和複製先前命令的文字，並將它們貼入目前行。

## <a name="the-equals-sign-"></a>等號 (=)

用來輸入 `EvaluateStatement` 命令的視窗可判斷是否將等號 (=) 解譯為比較運算子或指派運算子。

在 [即時運算] 視窗中，等號 (=) 會解譯為指派運算子。 因此；例如，命令

```cmd
>Debug.EvaluateStatement(varA=varB)
```

會將變數 `varB` 的值指派給變數 `varA`。

相較之下，在 [命令] 視窗中，等號 (=) 會解譯為比較運算子。 您不能在 [命令] 視窗中使用指派運算。 因此；例如，如果 `varA` 和 `varB` 變數的值不同，則命令

```cmd
>Debug.EvaluateStatement(varA=varB)
```

會傳回 `False` 值。

## <a name="first-chance-exception-notifications"></a>初次發生例外狀況通知

在某些設定組態中，發生第一個例外狀況的通知會顯示在 [即時運算] 視窗中。

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>在 [即時運算] 視窗中切換初次發生例外狀況的通知

1. 在 [檢視] 功能表上，按一下 [其他視窗]，然後按一下 [輸出]。

2. 以滑鼠右鍵按一下 [輸出] 視窗的文字區域，然後選取或取消選取 [例外狀況訊息]。

## <a name="see-also"></a>另請參閱

- [使用偵錯工具巡覽程式碼](../../debugger/navigating-through-code-with-the-debugger.md)
- [命令視窗](../../ide/reference/command-window.md)
- [偵錯工具簡介](../../debugger/debugger-feature-tour.md)
- [逐步解說：在設計階段進行偵錯](../../debugger/walkthrough-debugging-at-design-time.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
- [在 Visual Studio 中使用規則運算式](../../ide/using-regular-expressions-in-visual-studio.md)
