---
title: 偵錯 ASP.NET
description: 使用 Visual Studio 偵錯工具來偵錯 ASP.NET
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 74671401b3e3eaeae5840110dfc37c926266f98a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636983"
---
# <a name="quickstart-debug-aspnet-with-the-visual-studio-debugger"></a>快速入門：使用 Visual Studio 偵錯工具來偵錯 ASP.NET

Visual Studio 偵錯工具提供許多強大的功能，可協助您偵錯應用程式。 本主題提供了解一些基本功能的快速方法。

## <a name="create-a-new-project"></a>建立新專案 

1. 在 Visual Studio 中，選擇 [檔案] > [新增專案]。

1. 在 [Visual C#] 下方，選擇 [Web]，然後在中間窗格中選擇 [ASP.NET Core Web 應用程式]。

1. 鍵入 **MyDbgApp** 這類名稱，然後按一下 [確定]。

1. 在出現的對話方塊中，選擇中間窗格中的 [Web 應用程式]，然後按一下 [確定]。

     如果您沒有看到 [Web 應用程式] 專案範本，請在 [新增專案] 對話方塊的左窗格中，按一下 [開啟 Visual Studio 安裝程式] 連結。 Visual Studio 安裝程式即會啟動。 選擇 [ASP.NET 與網頁程式開發] 工作負載，然後選擇 [修改]。

    ![選擇 Web 應用程式](../debugger/media/dbg-qs-aspnet-choose-web-app.png)

    Visual Studio 會建立專案。

1. 在 [方案總管] 中，開啟 About.cshtml.cs (在 Pages/About.cshtml 之下)，並取代下列程式碼

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    取代為此程式碼：

    ```csharp
    public void OnGet()
    {
        LinkedList<int> result = doWork();
        Message = "Result of work: " + result.First.Value + ", " + result.First.Value;
    }

    private static LinkedList<int> doWork()
    {
        LinkedList<int> c1 = new LinkedList<int>();

        c1.AddLast(10);
        c1.AddLast(20);

        LinkedList<int> c2 = new LinkedList<int>(c1);

        return c2;

    }
    ```

## <a name="set-a-breakpoint"></a>設定中斷點

「中斷點」是一種標記，會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數值或記憶體行為，或查看程式碼分支是否正在執行。 它是偵錯中最基本的功能。

1. 若要設定中斷點，請按一下 `doWork` 函式左側的裝訂邊 (或選取該行程式碼並按 **F9** 鍵)。

    ![設定中斷點](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    中斷點設定在左大括弧 (`{`) 的左側。

1. 現在按下 **F5** 鍵 (或選擇 [偵錯] > [開始偵錯])。

1. 當網頁載入時，請按一下網頁頂端的 [關於] 連結。

    偵錯工具會在您設定中斷點的地方暫停。 暫停偵錯工具和應用程式執行所在的陳述式會以黃色箭號指示。 在 `doWork` 函式宣告之後具有左大括弧 (`{`) 的該程式碼行尚未執行。

    ![叫用中斷點](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > 如果在迴圈或遞迴中有中斷點，或是您有很多經常逐步執行的中斷點，請使用[條件中斷點](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)，以確保程式碼只在符合特定條件時暫停。 這可節省時間，也可以讓您更輕鬆地偵錯難以重現的問題。

## <a name="navigate-code"></a>巡覽程式碼

您可以透過不同的命令來指示偵錯工具繼續。 我們將顯示 Visual Studio 2017 中新增的實用程式碼導覽命令。

在中斷點處暫停時，將滑鼠游標移至陳述式 `return c2` 上方，直到出現綠色的 [執行至點選處] 按鈕 ![執行至點選處](../debugger/media/dbg-tour-run-to-click.png)，然後按 [執行至點選處] 按鈕。

![執行至點選處](../debugger/media/dbg-qs-run-to-click-aspnet.png)

應用程式會繼續執行，並在您按下按鈕所在的程式碼行暫停。

用來逐步執行程式碼的常用鍵盤命令包括 **F10** 和 **F11**。 如需更深入的指示，請參閱[初學者指南](../debugger/getting-started-with-the-debugger.md)。

## <a name="inspect-variables-in-a-datatip"></a>在資料提示中檢查變數

1. 在目前這一行程式碼中 (以黃色執行指標標示)，使用滑鼠將滑鼠游標移至 `c2` 物件上方以顯示資料提示。

    ![檢視資料提示](../debugger/media/dbg-qs-data-tip-aspnet.png)

    資料提示顯示 `c2` 變數的目前值，並可讓您檢查其屬性。 偵錯時，如果您看到非預期的值，則前面的數行程式碼或呼叫的數行程式碼可能有 Bug。 

2. 展開資料提示以查看 `c2` 物件的目前屬性值。

3. 如果您想要釘選資料提示，以便在執行程式碼時繼續查看 `c2` 的值，請按一下釘選小圖示 (您可以將所釘選資料提示移至方便存取的位置)。

## <a name="edit-code-and-continue-debugging"></a>編輯程式碼並繼續偵錯

如果您在偵錯工作階段期間，於程式碼中找到要測試的變更，您也可以這麼做。

1. 在 `OnGet` 方法中，按一下 `result.First.Value` 的第二個執行個體，並將 `result.First.Value` 變更為 `result.Last.Value`。

1. 按 **F10** 鍵 (或 [偵錯] > [不進入函式]) 幾次，以繼續進行偵錯工具並執行編輯的程式碼。

    ![編輯後繼續](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "編輯後繼續")

    **F10** 鍵可讓偵錯工具一次前進一個陳述式，但不進入函式，藉此取代逐步執行 (您略過的程式碼仍會執行)。

如需使用編輯後繼續和功能限制的詳細資訊，請參閱[編輯後繼續](../debugger/edit-and-continue.md)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何啟動偵錯工具、逐步執行程式碼，以及檢查變數。 建議您進一步查看偵錯工具功能，以及詳細資訊的連結。

> [!div class="nextstepaction"]
> [偵錯工具功能導覽](../debugger/debugger-feature-tour.md)
