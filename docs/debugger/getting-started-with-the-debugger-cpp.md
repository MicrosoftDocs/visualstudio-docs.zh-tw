---
title: 了解如何使用 Visual Studio 偵錯工具對 C++ 進行偵錯
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: debug-experiment
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- C++
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56ef97401a87f39e9c3bfd3138ee3a26646064c6
ms.sourcegitcommit: d7f232a7596420e40ff8051d42cdf90203af4a74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2018
ms.locfileid: "52825902"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>教學課程：了解如何使用 Visual Studio 對 C++ 程式碼進行偵錯

本文以逐步解說介紹 Visual Studio 偵錯工具的功能。 如果您想要偵錯工具功能的較高層級檢視，請參閱[偵錯工具功能導覽](../debugger/debugger-feature-tour.md)。 當您「偵錯您的應用程式」，通常表示您正在執行附加偵錯工具的應用程式。 執行此作業時，偵錯工具會提供許多方式來查看您程式碼所執行的功能。 您可以逐步執行程式碼並查看儲存在變數中的值、可以設定變數的監看式以查看值變更、可以檢查程式碼的執行路徑，查看是否正在執行程式碼的分支，依此類推。 如果這是您第一次嘗試偵錯程式碼，您可能需要先閱讀[適用於徹底初學者偵錯](../debugger/debugging-absolute-beginners.md)，再瀏覽本文。

| | |
|---------|---------|
| ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片") | [觀看影片](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171)以了解偵錯，其中會顯示類似的步驟。 |

在本教學課程中，您將進行下列作業：

> [!div class="checklist"]
> * 啟動偵錯工具，並叫用中斷點。
> * 了解命令以在偵錯工具中逐步執行程式碼
> * 檢查資料提示和偵錯工具視窗中的變數
> * 檢查呼叫堆疊

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 2017 和**使用 C++ 的桌面開發**工作負載。

    如果您尚未安裝 Visual Studio，請前往  [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 頁面免費進行安裝。

    如果您需要安裝工作負載，但已擁有 Visual Studio，請在 [新增專案] 對話方塊 (選取 [檔案] > [新增] > [專案]) 的左窗格中，按一下 [開啟 Visual Studio 安裝程式]。 Visual Studio 安裝程式即會啟動。 選擇 [使用 C++ 的桌面開發] 工作負載，然後選擇 [修改] 按鈕。

## <a name="create-a-project"></a>建立專案

1. 在 Visual Studio 中，選擇 [檔案] > [新增專案]。

2. 在 [Visual C++] 下方，選擇 [Windows 桌面]，然後在中間窗格中選擇 [Windows 主控台應用程式]。

    如果您沒有看到 [Windows 主控台應用程式] 專案範本，請在 [新增專案] 對話方塊的左窗格中，按一下 [開啟 Visual Studio 安裝程式] 連結。 Visual Studio 安裝程式即會啟動。 選擇 [使用 C++ 的桌面開發] 工作負載，然後選擇 [修改] 按鈕。

3. 鍵入 **get-started-debugging** 之類的名稱，並按一下 [確定]。

    Visual Studio 會建立專案。

4. 在 *get-started-debugging.cpp* 中，取代下列程式碼

    ```c++
    int main()
    {
        return 0;
    }
    ```

    取代為此程式碼：

    ```c++
    #include "pch.h"

    #include <string>
    #include <vector>
    #include <iostream>

    class Shape
    {
        int privateX = 0;
        int privateY = 0;
        int privateHeight = 0;
        int privateWidth = 0;

        int getX() const { return privateX; }
        void setX(int value) { privateX = value; }

        int getY() const { return privateY; }
        void setY(int value) { privateY = value; }

        int getHeight() const { return privateHeight; }
        void setHeight(int value) { privateHeight = value; }

        int getWidth() const { return privateWidth; }
        void setWidth(int value) { privateWidth = value; }

        public:
        // Virtual method
        virtual void Draw()
        {
            std::wcout << L"Performing base class drawing tasks" << std::endl;
        }
    };

    class Circle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a circle...
        std::wcout << L"Drawing a circle" << std::endl;
        Shape::Draw();
        }
    };

    class Rectangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a rectangle...
        std::wcout << L"Drawing a rectangle" << std::endl;
        Shape::Draw();
        }
    };

    class Triangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a triangle...
        std::wcout << L"Drawing a trangle" << std::endl;
        Shape::Draw();
        }
    };

    int main(std::vector<std::wstring> &args)
    {
        auto shapes = std::vector<Shape*>
        {
            new Rectangle(),
            new Triangle(),
            new Circle()
        };

        for (auto shape : shapes)
        {
            shape->Draw();
        }
    }

    /* Output:
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    */
    ```

## <a name="start-the-debugger"></a>啟動偵錯工具！

1. 按下 **F5** 鍵 ([偵錯] > [開始偵錯]) 或在偵錯工具列中按下 [開始偵錯] 按鈕 ![開始偵錯](../debugger/media/dbg-tour-start-debugging.png "開始偵錯")。

     **F5** 鍵會啟動應用程式並將偵錯工具附加至應用程式處理序，但目前我們還沒有做任何特別動作來檢查程式碼。 因此應用程式只會載入，且您會看到主控台輸出。

    ```
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     在本教學課程中，我們將使用偵錯工具仔細查看這個應用程式，並了解偵錯工具功能。

2. 按下紅色的停止 ![停止偵錯](../debugger/media/dbg-tour-stop-debugging.png "停止偵錯") 按鈕來停止偵錯工具。

## <a name="set-a-breakpoint-and-start-the-debugger"></a>設定中斷點，並啟動偵錯工具

1. 在 `main` 函式的 `for` 迴圈中，按一下下列程式碼行的左邊界來設定中斷點：

    `shape->Draw()`

    您設定中斷點的位置會出現紅色圓圈。

    中斷點是可靠偵錯最基本也最重要的功能。 中斷點會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數的值或記憶體的行為，或查看程式碼分支是否正在執行。 

2. 按下 **F5** 鍵或 [開始偵錯] 按鈕 ![開始偵錯](../debugger/media/dbg-tour-start-debugging.png 「開始偵錯」，應用程式會啟動，而偵錯工具會執行到您設定中斷點的程式碼行。

    ![設定並叫用中斷點](../debugger/media/get-started-set-breakpoint-cpp.gif)

    黃色箭號表示偵錯工具暫停時的陳述式，這也表示會在相同的點暫停執行應用程式 (尚未執行此陳述式)。

     如果尚未執行應用程式，則 **F5** 鍵會啟動偵錯工具並在第一個中斷點停止。 否則，**F5** 鍵會繼續執行應用程式到下一個中斷點。

    如果您知道要詳細檢查的程式碼行或程式碼區段，則中斷點是一個很有用的功能。

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>使用逐步執行命令在偵錯工具中巡覽程式碼

在大部分情況下，我們會在這裡使用鍵盤快速鍵，因為這是在偵錯工具中快速執行應用程式的好方法 (功能表命令等對等命令會顯示在括弧內)。

1. 在 `main` 函式的 `shape->Draw` 方法呼叫中暫停時，請按下 **F11** 鍵 (或選擇 [偵錯] > [逐步執行]) 推進到 `Rectangle` 類別的程式碼。

     ![使用 F11 鍵來逐步執行程式碼](../debugger/media/get-started-f11-cpp.png "F11 鍵逐步執行")

     F11 鍵是**逐步執行**命令，可將應用程式執行一次往前推進一個陳述式。 F11 鍵是以最詳細的方式檢查執行流程的好方法。 (若要更快速地在程式碼中移動，我們也會示範一些其他選項。)根據預設，偵錯工具會略過非使用者程式碼 (如果您想要更多的詳細資料，請參閱 [Just My Code](../debugger/just-my-code.md))。

2. 按幾次 **F10** 鍵 (或選擇 [偵錯] > [不進入函式])，直到偵錯工具在 `Shape::Draw` 方法呼叫上停止為止，然後再次按下 **F10** 鍵。

     ![使用 F10 鍵不進入程式碼](../debugger/media/get-started-step-over-cpp.png "F10 鍵不進入函式")

     請注意，這次偵錯工具不會逐步執行基底類別 (`Shape`) 的 `Draw` 方法。 **F10** 鍵會推進偵錯工具，而不需要逐步執行應用程式程式碼中的函式或方法 (此程式碼仍會執行)。 藉由在 `Shape::Draw` 方法呼叫上按下 F10 鍵 (而非 **F11** 鍵)，我們略過了根類別中 `Draw` 的實作程式碼 (現在對我們可能不太重要)。

## <a name="navigate-code-using-run-to-click"></a>使用 [執行至點選處] 來巡覽程式碼

1. 在程式碼編輯器中，向下捲動並停留在 `Triangle` 類別的 `std::cout`上，直到綠色的 [執行至點選處] 按鈕 ![執行至點選處](../debugger/media/dbg-tour-run-to-click.png "RunToClick") 出現在左側為止。

     ![使用 [執行至點選處] 功能](../debugger/media/get-started-run-to-click-cpp.png "執行至點選處")

   > [!NOTE]
   > [執行至點選處] 按鈕是 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 的新功能。 如果您沒有看到綠色箭號按鈕，請在此範例中改用 **F11** 鍵，將偵錯工具推進到正確的位置。

2. 按一下 [執行至點選處] 按鈕 ![執行至點選處](../debugger/media/dbg-tour-run-to-click.png "RunToClick")。

    使用此按鈕類似於設定暫時中斷點。 [執行至點選處] 方便您在應用程式程式碼的可見區域內快速瀏覽 (您可以按一下任何開啟的檔案)。

    偵錯工具將會推進到 `Triangle` 類別的 `std::cout` 方法實作。

    當暫停時，您會發現有錯字！ "Drawing a trangle" 輸出的拼字錯誤。 在偵錯工具中執行應用程式時，我們可以於此處加以修正。

## <a name="edit-code-and-continue-debugging"></a>編輯程式碼並繼續偵錯

1. 按一下以進入 "Drawing a trangle"，然後鍵入更正內容，將 "trangle" 變更為 "triangle"。

1. 按下 **F11** 一次，您會看到一則訊息顯示程式碼正在進行重新編譯，接著偵錯工具會再次推進。

    > [!NOTE]
    > 根據您在偵錯工具中編輯的程式碼類型，您可能會看到一則警告訊息。 在某些情況下，程式碼必須重新編譯，您才能繼續執行。

## <a name="step-out"></a>跳離函式

假設您已完成檢查 `Triangle` 類別中的 `Draw` 方法，而您想要離開該函式，但保留在偵錯工具中。 您可以使用 [跳離函式] 命令完成這項動作。

1. 按下 **Shift** + **F11** (或 [偵錯] > [跳離函式])。

     此命令會繼續執行應用程式 (並往前推進偵錯工具)，直到目前的函式傳回為止。

     您應該會回到 `main` 方法的 `for` 迴圈。

## <a name="restart-your-app-quickly"></a>快速重新啟動您的應用程式

按一下偵錯工具列中的 [重新啟動] ![重新啟動應用程式](../debugger/media/dbg-tour-restart.png "RestartApp") 按鈕 (**Ctrl** + **Shift** + **F5**)。

相對於停止應用程式並重新啟動偵錯工具，按下 [重新啟動] 可讓您節省時間。 偵錯工具會在執行程式碼叫用的第一個中斷點處暫停。

在 `shape->Draw()` 方法上，偵錯工具會在您設定的中斷點處再次停止。

## <a name="inspect-variables-with-data-tips"></a>使用資料提示來檢查變數

可讓您檢查變數的功能是偵錯工具最實用功能之一，而且有不同的方法來完成此作業。 通常當您嘗試偵錯問題時，您會嘗試確定變數是否會儲存您希望其在特定時間具有的值。

1. 在 `shape->Draw()` 方法上暫停時，將滑鼠停留在 `shapes` 容器 (向量物件) 上方，您就會看到其預設屬性值 `size` 屬性，顯示 `size=3`。

1. 展開 `shapes` 物件，查看其所有屬性，例如陣列 `[0]` 的第一個索引，其具有記憶體位址。

    您可以進一步展開物件以檢視其屬性。

1. 展開第一個索引 `[0]`，查看矩形的 `privateHeight` 屬性。

     ![檢視資料提示](../debugger/media/get-started-data-tip-cpp.png "檢視資料提示")

     通常在偵錯時，您希望能夠快速地檢查物件的屬性值，而資料提示很適合用來執行此作業。

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>使用 [自動變數] 和 [區域變數] 視窗來檢查變數

1. 查看程式碼編輯器底部的 [自動變數] 視窗。

     ![檢查 [自動變數] 視窗中的變數](../debugger/media/get-started-autos-window-cpp.png "[自動變數] 視窗")

    在 [自動變數] 視窗中，您會看到變數及其目前的值。 針對 C++，[自動變數] 視窗會顯示上述三行程式碼中的變數。

2. 接下來，在 [自動變數] 視窗旁的索引標籤中查看 [區域變數] 視窗。

    [區域變數] 視窗會顯示位在目前[範圍](https://www.wikipedia.org/wiki/Scope_(computer_science))中的變數，即為目前程式碼執行內容。

## <a name="set-a-watch"></a>設定監看式

1. 在主要程式碼編輯器視窗中，以滑鼠右鍵按一下 `shapes` 物件，並選擇 [新增監看式]。

    [監看式] 視窗隨即在程式碼編輯器底部開啟。 您可以使用 [監看式] 視窗來指定您要留意的變數 (或運算式)。

    現在，您已於 `shapes` 物件上設定監看式，當您在偵錯工具中移動時，就可以看到其值的變更。 不同於其他變數視窗，[監看式] 視窗一律會顯示所監看的變數 (它們在超出範圍時會呈現灰色)。

## <a name="examine-the-call-stack"></a>檢查呼叫堆疊

1. 在 `for` 迴圈中暫停時，請按一下 [呼叫堆疊] 視窗，此視窗預設會在右下方的窗格中開啟。

2. 按幾下 **F11** 鍵，直到您看到偵錯工具在程式碼編輯器中 `Rectangle` 類別的 `Shape::Draw` 方法中暫停為止。 查看 [呼叫堆疊] 視窗。

    ![檢查呼叫堆疊](../debugger/media/get-started-call-stack-cpp.png "ExamineCallStack")

    [呼叫堆疊] 視窗會顯示方法和函式的呼叫順序。 第一行會顯示目前的函式 (此範例中的 `Rectangle::Draw` 方法)。 第二行會顯示已從 `main` 函式呼叫 `Rectangle::Draw`，依此類推。

   > [!NOTE]
   > [呼叫堆疊] 視窗類似於某些 IDE (例如 Eclipse) 中的 [偵錯] 檢視方塊。

    呼叫堆疊是檢查並了解應用程式執行流程的好方法。

    您可以按兩下某一行的程式碼來查看其原始程式碼，這也會變更偵錯工具所檢查的目前範圍。 此動作不會讓偵錯工具往前推進。

    您也可以從 [呼叫堆疊] 視窗使用滑鼠右鍵功能表來執行其他動作。 例如，您可以在指定的函式中插入中斷點，使用 [執行至游標處] 讓偵錯工具往前推進，並檢查原始程式碼。 如需詳細資訊，請參閱[如何：檢查呼叫堆疊](../debugger/how-to-use-the-call-stack-window.md)。

## <a name="change-the-execution-flow"></a>變更執行流程

1. 偵錯工具在 `Shape::Draw` 方法呼叫中暫停後，使用滑鼠抓取左側的黃色箭號 (執行指標)，然後將黃色箭頭上移一行到 `std::cout` 方法呼叫。

1. 按下 **F11**。

    偵錯工具會重新執行 `std::cout` 方法 (您會在主控台視窗輸出中看到)。

    藉由變更執行流程，您可以執行一些作業，例如測試不同的程式碼執行路徑，或重新執行程式碼而不重新啟動偵錯工具。

    > [!WARNING]
    > 您通常需要謹慎使用這項功能，您會在工具提示中看到一則警告。 也可能會看到其他警告。 移動指標無法將應用程式還原成先前的應用程式狀態。

1. 按 **F5** 鍵繼續執行應用程式。

    恭喜您完成此教學課程！

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何啟動偵錯工具、逐步執行程式碼，以及檢查變數。 建議您進一步查看偵錯工具功能，以及詳細資訊的連結。

> [!div class="nextstepaction"]
> [偵錯工具簡介](../debugger/debugger-feature-tour.md)
