---
title: 開始使用 R 教學課程
description: 在 Visual Studio 中使用 R 的逐步解說，包括專案建立、互動式視窗、程式碼編輯和偵錯。
ms.date: 06/29/2017
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 80e09a9c6b86d37e3069e3694bea289ac37282af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873693"
---
# <a name="get-started-with-r-tools-for-visual-studio"></a>Visual Studio R 工具使用者入門

一旦安裝了 Visual Studio R 工具 (RTVS) (請參閱[安裝](installing-r-tools-for-visual-studio.md))，便可以快速體驗一下這些工具提供的體驗。

## <a name="create-an-r-project"></a>建立 R 專案

1. 開啟 Visual Studio。
1. 選擇 **[** 檔案  >  **新增**  >  **專案**] (**Ctrl** + **Shift** + **N**) 
1. 從 **範本** R 下選取 [r 專案]  >  ****，為專案提供名稱和位置，然後選取 **[確定]**：

   ![Visual Studio R (在 VS2017 中為 RTVS) 的 [新增專案] 對話方塊](media/getting-started-01-new-project.png)

1. 建立專案之後，您會看到下列視窗︰

    - 右邊為 Visual Studio 方案總管，您會在此看到專案，位於包含的「解決方案」內。 (解決方案可以包含任意數目且不同類型的專案，如需詳細資料，請參閱[專案](r-projects-in-visual-studio.md)。
    - 左上方是新的 R 檔案 (`script.R`)，您可以在其中使用 Visual Studio 所有的編輯功能來編輯原始程式碼。
    - 左下方是 [R 互動] 視窗，您可以在其中以互動方式開發及測試程式碼。

> [!Note]
> 您可以使用 [R 互動] 視窗而不開啟任何專案，甚至是在載入不同的專案類型時。 只要隨時選取 [ **R 工具**  >  **Windows**  >  **R 互動**] 即可。

## <a name="explore-the-interactive-window-and-intellisense"></a>瀏覽 Interactive 視窗和 IntelliSense

1. 藉由鍵入 `3 + 4` 然後按 **Enter** 鍵查看結果，測試互動式視窗是否在運作中︰

    ![Visual Studio 2017 (VS2017) 中的 R 互動視窗](media/getting-started-02-interactive1.png)

1. 輸入稍微複雜的內容 `ds <- c(1.5, 6.7, 8.9) * 1:12`，然後輸入 `ds` 查看結果︰

    ![Visual Studio R 的其他互動式範例](media/getting-started-03-interactive2.png)

1. 輸入 `mean(ds)`，但請注意，只要您輸入 `m` 或 `me`，Visual Studio IntelliSense 就會提供自動完成的選項。 在清單中選取您想要的完成時，按 **Tab** 鍵插入。您可以使用方向鍵或滑鼠變更選取範圍。

    ![您輸入程式碼時會顯示 IntelliSense](media/getting-started-04-intellisense1.png)

1. 完成 `mean` 之後，輸入左括弧 `(`，並注意 IntelliSense 如何提供您函式的內嵌說明︰

    ![IntelliSense 顯示函式的說明](media/getting-started-05-intellisense2.png)

1. 完成 `mean(ds)` 一行並按 Enter 查看結果 (`[1] 39.51667`)。

1. Interactive 視窗已和說明整合，因此輸入 `?mean` 會在 Visual Studio 的 [R 說明] 視窗中顯示該函式的說明。 如需詳細資訊，請參閱 [Visual Studio R 工具中的說明](getting-started-help.md)。

    ![Visual Studio 的 [R 說明] 視窗](media/getting-started-06-help.png)

1. 一些命令，例如 `plot(1:100)`，會在無法直接於 Interactive 視窗中顯示輸出時，在 Visual Studio 中開啟新視窗：

    ![Visual Studio R 繪圖視窗的螢幕擷取畫面，其中顯示圖形函式繪圖 (1:100) 的輸出。](media/getting-started-07-plot-window.png)

互動式視窗也可讓您檢閱您的歷程記錄、載入和儲存工作區、附加至偵錯工具，並與原始程式碼檔案互動，而不使用複製貼上。 如需詳細資料，請參閱[使用 R 互動視窗](interactive-repl-for-r-in-visual-studio.md)。

## <a name="experience-code-editing-features"></a>體驗程式碼編輯功能

簡短地使用互動式視窗，示範了也適用於程式碼編輯器的基本編輯功能，例如 IntelliSense。 如果您如同之前一樣輸入相同的程式碼，您會看到相同的自動完成和 IntelliSense 提示，但輸出不會相同。

在 *.R* 檔案中撰寫程式碼可讓您一次看到所有程式碼，並且能較輕鬆地進行細微變更，然後快速在互動式視窗中執行程式碼，以查看結果。 您也可以在專案中有任意數目的檔案。 當程式碼在檔案中時，您也可以在偵錯工具中逐步執行它 (本文稍後討論的) 。 當您開發計算演算法並撰寫程式碼來管理一或多個資料集時，尤其是當您想要檢查所有中繼結果時，這些功能很有幫助。

舉例來說，下列步驟會建立一些程式碼來探索 [Central Limit Theorem](https://en.wikipedia.org/wiki/Central_limit_theorem) (中央限制理論) (Wikipedia)。 (這個範例取自於 Paul Teetor 的 *R Cookbook*。)

1. 在 `script.R` 編輯器中，輸入下列程式碼：

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. 若要快速查看結果，請選取所有程式碼 (**Ctrl** + **A**) ，然後按下 **ctrl** + **enter** 或按一下滑鼠右鍵，然後選取 [**以互動方式執行**]。 所有選取的程式碼會在互動式視窗中執行，就彷彿您直接鍵入一樣，並在繪圖視窗中顯示結果︰

    ![顯示人口密度圖形之 Visual Studio R 繪圖視窗的螢幕擷取畫面。](media/getting-started-08-plot1.png)

1. 只要按下 Ctrl 鍵，就 + 可以在互動式視窗中執行該行。

> [!Tip]
> 瞭解進行編輯的模式，然後按下 **ctrl** + **鍵** (或使用 ctrl **** A 選取所有專案 +  ，然後按下 **ctrl** 鍵 + ) ，以快速執行程式碼。 這樣做會比使用滑鼠進行相同的作業更有效率。
>
> 此外，您可以將繪圖視窗從 Visual Studio 框架拖曳出來，放在顯示畫面上您想要的其他任何地方。 您可以輕鬆地將繪圖視窗調整成您想要的尺寸，然後將它儲存成影像或 PDF 檔案。

1. 新增幾行程式碼，包含第二個繪圖︰

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    lines(density(samp.means))
    ```

1. 按下 **ctrl** 鍵， + 然後按 + **enter** 鍵以執行程式碼，產生下列結果：

    ![Visual Studio 中的更新雙重繪圖](media/getting-started-09-plot2.png)

1. 問題是，第一個繪圖決定了垂直的比例，因此第二個繪圖 (與 `lines`) 不符。 若要修正此問題，我們必須在 `plot` 呼叫上設定 `ylim` 參數，但要正確地這麼做，我們需要新增程式碼來計算垂直的最大值。 在互動式視窗中逐行這麼做不太方便，因為我們需要重新排列程式碼，在呼叫 `plot` 之前先使用 `samp.means`。 不過在程式碼檔案中，我們可以輕鬆地進行適當的編輯︰

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)

    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    max.samp.means <- max(density(samp.means)$y)

    plot(density(pop), main = "Population Density",
        ylim = c(0, max.samp.means),
        xlab = "X", ylab = "")
    lines(density(samp.means))
    ```

1. **Ctrl** +**A** 和 **Ctrl +** + **Enter** ，以查看結果：

    ![Visual Studio 中的更新雙重繪圖，比例正確](media/getting-started-10-plot3.png)

您在編輯器中還可以做其他事。 如需詳細資料，請參閱[編輯 R 程式碼](editing-r-code-in-visual-studio.md)、[IntelliSense](r-intellisense.md) 和[程式碼片段](code-snippets-for-r.md)。

## <a name="debug-your-code"></a>偵錯程式碼

Visual Studio 的其中一項主要優點是其偵錯 UI。 RTVS 建置在這項強固的基礎上，並新增創新的 UI，例如[變數總管](variable-explorer.md)。 在這裡，我們只是初探一下偵錯。

1. 若要開始，請重設目前的工作區，以使用 **R 工具**  >  **會話**  >  **重設** 功能表命令來清除您到目前為止所做的一切。 根據預設，您在互動式視窗中所做的一切都會累算到目前工作階段，然後也會由偵錯工具使用。 藉由重設工作階段，您可以確保偵錯工作階段開始時沒有任何預先存在的資料。 不過 [重設] 並不會影響您的 *script.R* 來源檔案，因為它是在工作區之外管理和儲存。

1. 使用上一節中所建立的 *script.R* 檔案，在開頭為 `pop <-` 的行上設定中斷點，方法是將插入號放在該行上然後按 **F9** 鍵，或選取 [偵錯] > [切換中斷點] 功能表命令。 或者，您也可按一下左邊界 (，或在顯示紅色中斷點點的那一行的裝訂邊) ：

    ![在編輯器中設定中斷點](media/getting-started-11-debug1.png)

1. 使用 *script.R* 中的程式碼啟動偵錯工具，方法是選取工具列上的 [執行啟動檔案] 按鈕、選取 [偵錯] > [執行啟動檔案] 功能表項目，或按 **F5** 鍵。 Visual Studio 會進入偵錯模式，並開始執行程式碼。 不過，它會停在您設定中斷點的行上︰

    ![在 Visual Studio 偵錯工具的中斷點上停止](media/getting-started-12-debug2.png)

1. 在偵錯期間，Visual Studio 提供逐步執行逐行程式碼行的能力。 您也可以逐步執行函式、不進入函式，或跳離函式到呼叫的內容。 這些功能，以及其他功能，可以在 [偵錯] 功能表、編輯器的快顯內容功能表，和 [偵錯] 工具列中找到︰

    ![Visual Studio 中的 [偵錯] 工具列](media/getting-started-13-debug3.png)

1. 在中斷點停止時，您可以檢查變數的值。 在 Visual Studio 中找到 [自動變數] 視窗，在底部選取名為 [區域變數] 的索引標籤。 [區域變數] 視窗會顯示程式目前位置的區域變數。 如果您停在稍早設定的中斷點上，則會看到尚未定義 `pop` 變數。 現在使用 **Debug**  >  **Step Over** 命令 (**F10**) ，您會看到顯示的值 `pop` ：

    ![Visual Studio 中的 [區域變數] 視窗](media/getting-started-14-debug4.png)

1. 若要檢查不同範圍中的變數，包括全域範圍和套件範圍，則是使用[變數總管](variable-explorer.md)。 變數總管也讓您能夠切換到具有可排序資料行的表格式檢視，以及將資料匯出至 CSV 檔案。

    ![變數總管的展開檢視](media/variable-explorer-expanded-results.png)

1. 您可以繼續逐步執行程式行，或選取 [繼續] (**F5**) 來執行到完成 (或下一個中斷點)。

若要深入資訊，請參閱[偵錯](debugging-r-in-visual-studio.md)和[變數總管](variable-explorer.md)。

## <a name="next-steps"></a>下一步

在此逐步解說中，您已了解 R 專案的基本概念、使用互動式視窗、程式碼編輯，以及在 Visual Studio 中偵錯。 若要繼續探索更多的功能，請參閱下列文章和目錄中顯示的文章：

- [範例專案](getting-started-samples.md)
- [編輯程式碼](editing-r-code-in-visual-studio.md)
- [偵錯](debugging-r-in-visual-studio.md)
- [工作區](r-workspaces-in-visual-studio.md)
- [視覺化資料](visualizing-data-with-r-in-visual-studio.md)
