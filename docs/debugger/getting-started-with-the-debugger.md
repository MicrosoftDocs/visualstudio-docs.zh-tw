---
title: 了解如何使用 Visual Studio 偵錯工具進行偵錯
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: mvc
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d9cb4e6b69f88f0c3e61d17211ffe5ff464f1b17
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827554"
---
# <a name="tutorial-learn-to-debug-using-visual-studio"></a>教學課程： 了解如何使用 Visual Studio 進行偵錯

這篇文章介紹 Visual Studio 偵錯工具的逐步解說中的功能。 如果您想要偵錯工具功能的較高層級檢視，請參閱[偵錯工具功能導覽](../debugger/debugger-feature-tour.md)。 當您*偵錯您的應用程式*，通常表示您正在附加偵錯工具執行您的應用程式。 當您這樣做時，偵錯工具會提供許多方式來看看您的程式碼如何在執行。 您可以逐步執行程式碼，並查看儲存在變數中的值，您可以設定監看式變數以查看值的變更時，您可以檢查您的程式碼的執行路徑，查看程式碼分支是否正在執行，依此類推。 如果這是您嘗試偵錯程式碼的第一次，您可能想要閱讀[偵錯適用於徹底初學者](../debugger/debugging-absolute-beginners.md)之前，先透過這篇文章。

| | |
|---------|---------|
| ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片") | [觀看影片](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171)偵錯，會顯示類似的步驟。 |

雖然示範應用程式是 C# 和 c + + 的功能都適用於 Visual Basic、 JavaScript 和 Visual Studio （除了註明） 支援其他語言。 螢幕擷取畫面是在 C#。

在本教學課程中，您將進行下列作業：

> [!div class="checklist"]
> * 啟動偵錯工具，並叫用中斷點。
> * 了解逐步執行偵錯工具中的程式碼的命令
> * 檢查資料提示和偵錯工具視窗中的變數
> * 檢查呼叫堆疊

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 2017 並 **.NET 桌面開發**或是**使用 c + + 的桌面開發**工作負載。

    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)頁面免費進行安裝。

    如果您需要安裝工作負載，但已擁有 Visual Studio，請在 [新增專案] 對話方塊 (選取 [檔案] > [新增] > [專案]) 的左窗格中，按一下 [開啟 Visual Studio 安裝程式]。 Visual Studio 安裝程式即會啟動。 選擇。**NET 桌面開發**或是**使用 c + + 的桌面開發**工作負載，然後選擇**修改**。

## <a name="create-a-project"></a>建立專案

1. 在 Visual Studio 中，選擇 [檔案] > [新增專案]。

2. 底下**Visual C#** 或是**Visual c + +**，選擇**Windows 桌面**，然後在中間窗格選擇**主控台應用程式**(**Windows 主控台應用程式**c + + 中)。

    如果您沒有看到**主控台應用程式**專案範本，請按一下 [**開啟 Visual Studio 安裝程式**的左窗格中的連結**新專案**] 對話方塊。 Visual Studio 安裝程式即會啟動。 選擇 *.NET 桌面開發** 或**使用 c + + 的桌面開發**工作負載，然後選擇**修改**。

3. 輸入名稱，例如**get-啟動-偵錯**然後按一下**確定**。

    Visual Studio 會建立專案。

    > [!NOTE]
    > 若要切換的 C# 和 c + + 範例程式碼，在本文中，使用右上方的此頁面上的語言篩選條件。

4. 在  *Program.cs* (C#) 或*取得啟動 debugging.cpp* （c + +），取代下列程式碼

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;

    namespace get_started_debugging
    {
        class Program
        {
            static void Main(string[] args)
            {
            }
        }
    }
    ```

    ```c++
    int main()
    {
        return 0;
    }
    ```

    取代為此程式碼：

    ```csharp
    using System;
    using System.Collections.Generic;

    public class Shape
    {
        // A few example members
        public int X { get; private set; }
        public int Y { get; private set; }
        public int Height { get; set; }
        public int Width { get; set; }
   
        // Virtual method
        public virtual void Draw()
        {
            Console.WriteLine("Performing base class drawing tasks");
        }
    }

    class Circle : Shape
    {
        public override void Draw()
        {
            // Code to draw a circle...
            Console.WriteLine("Drawing a circle");
            base.Draw();
        }
    }

    class Rectangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle");
            base.Draw();
        }
    }

    class Triangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a triangle...
            Console.WriteLine("Drawing a trangle");
            base.Draw();
        }
    }

    class Program
    {
        static void Main(string[] args)
        {

            var shapes = new List<Shape>
            {
                new Rectangle(),
                new Triangle(),
                new Circle()
            };

            foreach (var shape in shapes)
            {
                shape.Draw();
            }

            // Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
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

## <a name="start-the-debugger"></a>開始偵錯工具 ！

1. 按下**F5** (**偵錯 > 啟動偵錯**) 或**開始偵錯**按鈕![開始偵錯](../debugger/media/dbg-tour-start-debugging.png "開始偵錯")偵錯 工具列中。

     **F5**啟動應用程式與偵錯工具附加至應用程式處理，但現在我們還沒有做任何特別動作來檢查程式碼，以滑鼠右鍵。 因此應用程式只會載入，您會看到主控台輸出。

    ```
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     在本教學課程中，我們會仔細看看此應用程式使用偵錯工具，並取得了解偵錯工具功能。

2. 停止偵錯工具，藉由按下的紅色的停駐![停止偵錯](../debugger/media/dbg-tour-stop-debugging.png "停止偵錯") 按鈕。

## <a name="set-a-breakpoint-and-start-the-debugger"></a>設定中斷點並開始偵錯工具

1. 在 `foreach`迴圈`Main`函式 (`for` c + + 中的迴圈`main`函式)，下列程式碼行的左邊的界，即可設定中斷點：

    `shape.Draw()` (或者， `shape->Draw()` c + +)

    紅色圓圈會出現您用來設定中斷點。

    中斷點是可靠偵錯最基本也最重要的功能。 中斷點會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數的值或記憶體的行為，或查看程式碼分支是否正在執行。 

6. 按下**F5**或**開始偵錯**按鈕，應用程式會啟動並偵錯工具執行的程式碼行，您在其中設定中斷點。

    ![設定和叫用中斷點](../debugger/media/get-started-set-breakpoint.gif)

    黃色箭號表示陳述式的偵錯工具暫停時，這也會在相同的點 （此陳述式尚未執行） 的暫停應用程式執行。

     如果尚未執行的應用程式， **F5**啟動偵錯工具，在第一個中斷點停止。 否則，請**F5**會繼續執行應用程式到下一個中斷點。

    當您知道程式碼行或您想要詳細檢查的程式碼的區段時，中斷點會是很有用的功能。

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>使用逐步執行命令的偵錯工具中巡覽程式碼

大部分，我們會使用的鍵盤快速鍵在這裡，因為它是一個好的方法，以取得快速在偵錯工具 （對等命令例如功能表命令會顯示在括號內） 中執行您的應用程式。

1. 在暫停期間`shape.Draw`方法呼叫中`Main`方法 (`shape->Draw` c + + 中)，按下**F11** (或選擇**偵錯 > 逐步執行**) 前進至程式碼的`Rectangle`類別。

     ![使用 F11 來逐步執行程式碼](../debugger/media/get-started-f11.png "F11 逐步執行")

     是 F11**逐步執行**命令，並往前推進應用程式執行一個陳述式一次。 F11 是檢查大部分的詳細資料中的執行流程的好方法。 （若要更快速移動，透過程式碼，我們將示範一些其他選項也。）根據預設，偵錯工具會略過非使用者程式碼 (如果您想要更多詳細資料，請參閱[Just My Code](../debugger/just-my-code.md))。

2. 按下**F10** (或選擇**偵錯 > 不進入函式**) 多次，直到偵錯工具停止於`base.Draw`方法呼叫 (`Shape::Draw` c + + 中)，然後按**F10**一次。

     ![使用 F10 不進入函式程式碼](../debugger/media/get-started-step-over.png "F10 不進入函式")

     請注意這次，偵錯工具不會不涉及`Draw`基底類別的方法 (`Shape`)。 **F10**前進偵錯工具，而不需要逐步執行函式或應用程式程式碼 （仍執行的程式碼） 的方法。 按下 F10 `base.Draw` (或`Shape::Draw`) 方法呼叫 (而非**F11**)，我們跳過之實作程式碼`base.Draw`（我們不關心的立即的可能）。

## <a name="navigate-code-using-run-to-click"></a>瀏覽使用 執行至所按的程式碼

5. 在程式碼編輯器中，向下捲動並停留`Console.WriteLine`方法 (`std::cout` c + + 中) 中`Triangle`直到綠色類別**執行至點選處**按鈕![執行至點選處](../debugger/media/dbg-tour-run-to-click.png "RunToClick")出現在左邊。

     ![使用 執行至點選功能](../debugger/media/get-started-run-to-click.png "執行至點選處")

   > [!NOTE]
   > **執行至點選處** 按鈕的新[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。 如果您沒有看到綠色箭號按鈕，使用**F11**在此範例中改為偵錯工具前往正確的位置。

6. 按一下 [**執行至點選處**] 按鈕![執行至點選處](../debugger/media/dbg-tour-run-to-click.png "RunToClick")。

    使用此按鈕，類似於設定暫時中斷點的。 **執行至點選處**便於快速瀏覽應用程式程式碼 （您可以按一下任何開啟的檔案中） 的可見區域內。

    偵錯工具將會前往`Console.WriteLine`方法實作`Triangle`類別 (`std::cout` c + + 中)。

    當暫停時，您會發現打錯字 ！ 「 繪製 trangle"的輸出拼字錯誤。 我們可以修正它這裡時偵錯工具中執行的應用程式。

## <a name="edit-code-and-continue-debugging"></a>編輯程式碼並繼續偵錯

1. 按一下以進入 「 繪製 trangle"，然後輸入更正，將 「 trangle"變更為"triangle"。

1. 按下**F11**一次，而且您看到 偵錯工具一次前進。

    > [!NOTE]
    > 根據偵錯工具中編輯的程式碼，您可能會看到一則警告訊息。 在某些情況下，程式碼必須重新編譯才能繼續。

## <a name="step-out"></a>跳離函式

假設您已完成檢查`Draw`方法中的`Triangle`類別，而您想要利用函式，並且保留在偵錯工具。 您可以使用**跳離函式**命令。

1. 按下**Shift** + **F11** (或**偵錯 > 跳離函式**)。

     此命令會繼續應用程式執行 （並往前推進偵錯工具） 直到目前的函式傳回。

     您應該會回到`foreach`迴圈`Main`方法 (`for` c + + 中的迴圈)。

## <a name="restart-your-app-quickly"></a>快速重新啟動您的應用程式

按一下 [**重新啟動**![重新啟動應用程式](../debugger/media/dbg-tour-restart.png "RestartApp")中偵錯] 工具列按鈕 (**Ctrl** + **Shift**  +  **F5**)。

當您按下**重新啟動**，節省時間與停止應用程式，並重新啟動偵錯工具。 偵錯工具會在叫用時執行程式碼的第一個中斷點暫停。

偵錯工具停在您設定的中斷點，在`shape.Draw()`方法 (`shape->Draw()` c + + 中)。

## <a name="inspect-variables-with-data-tips"></a>檢查資料提示中使用的變數

功能可讓您檢查變數是其中一個最實用的功能，在偵錯工具，而且有不同的方式來進行。 通常，當您嘗試偵錯問題時，會嘗試找出是否變數會儲存您希望他們能夠在特定時間的值。

1. 在暫停期間`shape.Draw()`方法 (`shape->Draw()` c + + 中)，將滑鼠停留`shapes`物件，而且您會看到預設屬性值，`Count`屬性。

1. 依序展開`shapes`物件，以檢視所有內容，例如陣列的第一個索引`[0]`，其具有值為`Rectangle`(C#) 或記憶體位址 （c + +）。

     ![檢視資料提示](../debugger/media/get-started-data-tip.gif "檢視資料提示方塊")

    您可以進一步展開物件，若要檢視其屬性，例如`Height`矩形的屬性。

    通常，偵錯時，您希望能很快地檢查屬性值的物件，而且資料提示很適合用來執行它。

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>檢查變數與 [自動變數] 和 [區域變數] 視窗

1. 看看**自動變數**底部的程式碼編輯器 視窗。

     ![檢查 [自動變數] 視窗中的變數](../debugger/media/get-started-autos-window.png "自動變數視窗")

    在 [**自動變數**] 視窗中，您會看到變數和其目前的值。 **自動變數**視窗會顯示目前這一行或上述列上使用的所有變數 （c + + 中，視窗會都顯示變數前面的三行程式碼中。 檢查特定語言行為的文件）。

    > [!NOTE]
    > 在 JavaScript 中，**區域變數**但不是支援 視窗**自動變數**視窗。

2. 接下來，看看**區域變數**視窗中的，在索引標籤旁**自動變數**視窗。

    **區域變數** 視窗會顯示在目前的變數[範圍](https://www.wikipedia.org/wiki/Scope_(computer_science))。

## <a name="set-a-watch"></a>設定監看式

1. 在主要程式碼編輯器 視窗中，以滑鼠右鍵按一下`shapes`物件，並選擇**新增監看式**。

    **監看式**底部的程式碼編輯器的視窗隨即開啟。 您可以使用**監看式**視窗上，指定變數 （或運算式），您要留意。

    現在，您可以監看式上設定`shapes`物件，而您可以看到當您瀏覽偵錯工具變更其值。 不同於其他變數視窗中，**監看式**視窗一律會顯示變數，您所監看 （它們呈現灰色時超出範圍）。

## <a name="examine-the-call-stack"></a>檢查呼叫堆疊

1. 在暫停期間`foreach`迴圈 (`for` c + + 中的迴圈)，按一下**呼叫堆疊**視窗中，預設在右下方的窗格中開啟。

2. 按一下  **F11**幾次，直到您看到 偵錯工具中暫停`Circle.Draw`程式碼編輯器中的方法。 看看**呼叫堆疊**視窗。

    ![檢查呼叫堆疊](../debugger/media/get-started-call-stack.png "ExamineCallStack")

    **呼叫堆疊**視窗會顯示方法和函式會取得呼叫的順序。 第一行會顯示目前的函式 (`Circle.Draw`或`Circle::Draw`此應用程式中的方法)。 第二行顯示`Circle.Draw`已從呼叫`Main`方法 (`main` c + + 中)，依此類推。

   > [!NOTE]
   > **呼叫堆疊**視窗是類似於偵錯觀點來看一些像是 Eclipse Ide 中。

    呼叫堆疊會檢查並了解應用程式的執行流程的好方法。

    您可以按兩下去看看該來源的程式碼的程式碼行，即，也會變更目前正在檢查偵錯工具的範圍。 此動作不前移偵錯工具。

    您也可以使用滑鼠右鍵功能表，從**呼叫堆疊**視窗來進行其他動作。 比方說，您可以在其中插入指定的函式的中斷點，讓偵錯工具使用**執行至游標處**，並移檢查原始程式碼。 如需詳細資訊，請參閱 <<c0> [ 如何： 檢查 呼叫堆疊](../debugger/how-to-use-the-call-stack-window.md)。

## <a name="change-the-execution-flow"></a>變更執行流程

1. 偵錯工具中暫停`Circle.Draw`方法呼叫中，按下**F11**幾次，直到偵錯工具會在暫停`base.Draw`方法呼叫 (`Shape::Draw` c + + 中)。

1. 使用滑鼠抓取左側的黃色箭號 （執行指標），然後移動到一行的黃色箭頭`Console.WriteLine`(`std::cout` c + +) 方法呼叫。

1. 按下**F11**一次。

    偵錯工具重新執行`Console.WriteLine`方法 (`std::cout` c + + 中)。

    藉由變更執行流程，您可以執行一些作業，例如測試不同的程式碼執行路徑，或重新執行程式碼，不需要重新啟動偵錯工具。

    > [!WARNING]
    > 您通常需要謹慎使用這項功能，以及您會看到工具提示中的警告。 您可能會太看到其他警告。 將指標移無法還原成先前的應用程式狀態的應用程式。

1. 按下**F5**繼續執行應用程式。

    恭喜您完成此教學課程！

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何啟動偵錯工具，逐步執行程式碼，並檢查變數。 若要高階查看偵錯工具功能，以及其他更多資訊的連結。

> [!div class="nextstepaction"]
> [偵錯工具祕訣與技巧](../debugger/debugger-tips-and-tricks.md)
