---
title: 了解如何偵錯多執行緒應用程式
description: 使用 平行堆疊 和 平行監看式的視窗，在 Visual Studio 中偵錯
ms.custom: ''
ms.date: 11/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5535228f8e070128cfa2479d8017d3a88dc0915c
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58790247"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>開始偵錯多執行緒應用程式 (C#，Visual Basic 中， C++)

Visual Studio 提供數個工具和可協助您偵錯多執行緒應用程式的使用者介面項目。 本教學課程示範如何使用執行緒標記**平行堆疊** 視窗中，**平行監看式**視窗、 條件式中斷點和篩選中斷點。 完成本教學課程將讓您熟悉 Visual Studio 進行偵錯多執行緒應用程式的功能。

下列兩個主題提供有關使用其他的多執行緒偵錯工具的其他資訊：

- 若要使用**偵錯位置**工具列並**執行緒**視窗中，請參閱[逐步解說：偵錯多執行緒應用程式](../debugger/how-to-use-the-threads-window.md)。

- 如需範例，會使用<xref:System.Threading.Tasks.Task>(managed 程式碼) 和並行執行階段 (C++)，請參閱[逐步解說：偵錯平行應用程式](../debugger/walkthrough-debugging-a-parallel-application.md)。 如需適用於最多執行緒應用程式類型的一般偵錯秘訣，閱讀該主題，並如下。

您必須先在多執行緒應用程式專案。 範例如下。

## <a name="create-a-multithreaded-app-project"></a>建立多執行緒應用程式專案

1. 開啟 Visual Studio 並建立新專案。

    ::: moniker range=">=vs-2019"
    按 **Esc** 來關閉開始視窗。 型別**Ctrl + Q**來開啟 [搜尋] 方塊中，輸入**主控台**(或**c + +**)，選擇**範本**，然後：

    - 針對C#或 Visual Basic 中，選擇**建立新的主控台應用程式 (.NET Framework) 專案**或C#或 Visual Basic。 在出現的對話方塊中選擇 [建立]。
    - 針對C++，選擇**建立新的主控台應用程式專案**的C++。 在出現的對話方塊中選擇 [建立]。

    然後，輸入名稱，例如**MyThreadWalkthroughApp**然後按一下**建立**。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。 在左窗格中**新的專案**對話方塊方塊中，選擇下列：

    - 針對C#應用程式底下**視覺化C#** ，選擇**Windows 桌面**，然後在中間窗格選擇 **主控台應用程式 (.NET Framework)**。
    - Visual Basic 應用程式中，在**Visual Basic**，選擇**Windows 桌面**，然後在中間窗格選擇 **主控台應用程式 (.NET Framework)**。
    - 針對C++應用程式底下**視覺化C++** ，選擇**Windows Desktop**、，然後選擇  **Windows 主控台應用程式**。

    然後，輸入名稱，例如**MyThreadWalkthroughApp**然後按一下**確定**。
    ::: moniker-end

    如果您未看到 [主控台應用程式] 專案範本，請前往 [工具] > [取得工具與功能...]，以開啟 Visual Studio 安裝程式。 選擇 [NET 桌面開發] 或 [使用 C++ 的桌面開發] 工作負載，然後選擇 [修改] 按鈕。

1. 選取 [確定]。

    新的主控台專案隨即出現。 在建立專案之後，便會出現原始程式檔。 根據您所選擇的語言，可能呼叫的原始程式檔*Program.cs*， *MyThreadWalkthroughApp.cpp*，或*Module1.vb*。

1. 刪除出現在原始程式檔中的程式碼，並在下方列出的適當範例程式碼取代它。

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "pch.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::cout << "The function called by the worker thread has ended." << std::endl;
    }

    int main() {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doSomeWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
    }

    for (auto& thread : threads) {
        thread.join();
    }

    return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```

1. 在 [檔案] 功能表中，選取 [全部儲存]。

1. (僅限 Visual Basic)在 方案總管 （右窗格），以滑鼠右鍵按一下專案節點，選擇**屬性**。 底下**應用程式**索引標籤中變更**啟始物件**來**簡單**。

## <a name="debug-the-multithreaded-app"></a>偵錯多執行緒應用程式

1. 在原始碼程式碼編輯器中，尋找下列程式碼片段的其中一個：

    ```csharp
    Thread.Sleep(3000);
    Console.WriteLine();
    ```

    ```C++
    std::this_thread::sleep_for(std::chrono::seconds(3));
    std::cout << "The function called by the worker thread has ended." << std::endl;
    ```

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```

1. 以滑鼠左鍵按一下中的左側裝訂邊上`Thread.Sleep`或`std::this_thread::sleep_for`陳述式來插入新的中斷點。

    在裝訂邊上，紅色圓圈會指示此位置已設定中斷點。

2. 在 **偵錯**功能表上，選取**開始偵錯**(**F5**)。

    Visual Studio 會建置方案，應用程式啟動偵錯工具附加，以執行，然後應用程式停止於中斷點。

3. 在原始碼程式碼編輯器中，找出包含中斷點的那一行。

### <a name="ShowThreadsInSource"></a>尋找執行緒標記  

1.  在 [偵錯] 工具列中，選取**在來源中顯示執行緒** 按鈕![在來源中顯示執行緒](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")。

2. 按下**F11**前進一行程式碼偵錯工具一次。

3.  查看來源視窗左邊的裝訂邊。 在這一行，您會看到*執行緒標記*圖示![執行緒標記](../debugger/media/dbg-thread-marker.png "ThreadMarker") ，類似於扭曲的兩個執行緒。 執行緒標記表示執行緒會停在這個位置上。

    執行緒標記可能會部分隱藏在中斷點。

4.  將指標移到執行緒標記上。 資料提示方塊會出現告訴您每個已停止的執行緒的名稱和執行緒 ID 編號。 名稱在此情況下，可能是`<noname>`。

5.  選取的執行緒標記，以查看可用的捷徑功能表上的選項。

### <a name="ParallelStacks"></a>檢視執行緒位置

在 **平行堆疊** 視窗中，您可以在切換執行緒 檢視之間，並 （適用於以工作為基礎的程式設計） 工作 檢視中，而且您可以檢視每個執行緒的呼叫堆疊資訊。 在此應用程式中，我們可以使用 [執行緒] 檢視。

1. 開啟**平行堆疊**視窗中的選擇**偵錯** > **Windows** > **平行堆疊**。 您應該會看到類似下面的內容。 正確的資訊會依目前位置的每個執行緒，您的硬體，並且您的程式語言而有所不同。

    ![平行堆疊 視窗](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    在此範例中，從左到右我們看到這項資訊以 managed 程式碼：

    - 主執行緒 （左邊） 上已停止`Thread.Start`，其中的停止點由執行緒標記圖示![執行緒標記](../debugger/media/dbg-thread-marker.png "ThreadMarker")。
    - 兩個執行緒已進入`ServerClass.InstanceMethod`，其中之一就是目前的執行緒 （黃色箭號），而另一個執行緒已停止在`Thread.Sleep`。
    - 新的執行緒 （右側） 同時啟動，但已停止在`ThreadHelper.ThreadStart`。

2.  中的項目上按一下滑鼠右鍵**平行堆疊**視窗來查看可用的捷徑功能表上的選項。

    您可以採取各種動作，從這些以滑鼠右鍵按一下功能表中，但本教學課程中我們將會顯示更多中的這些詳細資料**平行監看式**視窗 （下一節）。

    > [!NOTE]
    > 若要查看清單檢視，每個執行緒的相關資訊，請使用**執行緒**視窗改。 請參閱[逐步解說：偵錯多執行緒應用程式](../debugger/how-to-use-the-threads-window.md)。

### <a name="set-a-watch-on-a-variable"></a>設定變數的監看式

1. 開啟**平行監看式**視窗中的選取**偵錯** > **Windows** > **平行監看式** > **平行監看式 1**。

2. 選取儲存格，您看到`<Add Watch>`文字 （或第 4 個資料行中的空白的標題儲存格） 並輸入`data`。

    每個執行緒的資料變數的值會出現在視窗中。

3. 選取儲存格，您看到`<Add Watch>`文字 （或空的標頭中的資料格的 5 日的資料行），然後輸入`count`。

    值`count`視窗中出現的每個執行緒的變數。 如果您沒有看到這麼多資訊，請嘗試按下**F11**幾次前進的偵錯工具中的執行緒執行。

    ![[平行監看式] 視窗](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. 以滑鼠右鍵按一下其中一個資料列在視窗中，若要查看可用的選項。

### <a name="flag-and-unflag-threads"></a>將執行緒加上旗標和取消旗標
您可以旗標追蹤重要的執行緒，並忽略其他執行緒的執行緒。

1. 在 [**平行監看式**] 視窗中，按住**Shift**鍵並選取多個資料列。

2. 以滑鼠右鍵按一下並選取**旗標**。

    標示所有選取的執行緒。 現在，您可以篩選以顯示已標幟的執行緒。

3.  在 [**平行監看式**視窗中，選取**僅顯示已標幟的執行緒**] 按鈕![顯示已標幟的執行緒](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker")。

    只有已標幟的執行緒會出現在清單中。

    > [!TIP]
    > 您有已標幟的一些執行緒後，您可以以滑鼠右鍵按一下程式碼編輯器中的程式碼行，並選擇**執行至游標處加上旗標的執行緒**。 請務必選擇 所有已標幟的執行緒的程式碼會到達。 Visual Studio 將會暫停執行緒上所選取一行程式碼，讓您更輕鬆地控制所執行的順序[凍結和解除凍結執行緒](#bkmk_freeze)。

4.  選取 [**僅顯示已標幟的執行緒**] 按鈕來切換回到**顯示所有執行緒**模式。

5. 將執行緒取消標幟，請以滑鼠右鍵按一下一或多個已標幟的執行緒，在**平行監看式**視窗，然後選取**取消旗標**。

### <a name="bkmk_freeze"></a> 凍結和解除凍結執行緒的執行

> [!TIP]
> 您可以凍結和解除凍結 （暫止和繼續） 來控制執行緒執行工作順序的執行緒。 這可協助您解決並行存取問題，例如死結和競爭情形。

1.  在 [**平行監看式**] 視窗，其中所有選取的資料列，以滑鼠右鍵按一下，然後選取**凍結**。

    在第二個資料行中，暫停圖示會顯示每個資料列。 暫停圖示表示已凍結執行緒。

2.  取消選取所有其他資料列，選取一個資料列。

3.  以滑鼠右鍵按一下資料列，然後選取**解除凍結**。

    暫停圖示消失在此資料列，指出已不再凍結執行緒。

4.  切換至程式碼編輯器，然後按**F11**。 只有在未凍結的執行緒執行。

    應用程式可能也會產生一些新的執行緒。 未標幟及未凍結任何新的執行緒。

### <a name="bkmk_follow_a_thread"></a> 請遵循單一執行緒的條件式中斷點

它可以是很有幫助進行偵錯工具中的單一執行緒的執行。 若要這麼做的方法之一是透過凍結您不感興趣的執行緒。 在某些情況下，您可能需要進行單一執行緒沒有凍結其他執行緒，例如若要重現特定錯誤。 若要依照沒有凍結的其他執行緒的執行緒，您必須避免分成多個您感興趣的執行緒上的程式碼除外。 您可以藉由設定[條件式中斷點](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)。

您可以設定中斷點，在不同的條件，例如執行緒名稱或執行緒識別碼。 它可能會很有幫助是您知道是唯一的每個執行緒的資料設定條件。 這是常見的偵錯案例，您會比較有興趣任何特定的執行緒比某些特定的資料值。

1. 以滑鼠右鍵按一下您先前建立的中斷點，然後選取**條件**。

2. 在 [**中斷點設定**] 視窗中，輸入`data == 5`條件運算式。

    ![條件式中斷點](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > 如果您是比較有興趣在特定執行緒，然後使用執行緒名稱或執行緒識別碼條件。 若要在**中斷點設定**視窗中，選取**篩選**而非**條件運算式**，並依照篩選秘訣。 您可以命名您的執行緒，應用程式程式碼，因為執行緒識別碼變更時重新啟動偵錯工具。

3. 關閉**中斷點設定**視窗。

4. 選取 重新啟動![重新啟動應用程式](../debugger/media/dbg-tour-restart.png "RestartApp")按鈕以重新啟動您的偵錯工作階段。

    您將會分成資料變數的值為 5 的所在的執行緒上的程式碼。 在 [**平行監看式**] 視窗中，尋找黃色箭號表示目前的偵錯工具內容。

5. 現在，您可以不進入程式碼 (**F10**) 並逐步執行程式碼 (**F11**) 並遵循單一執行緒的執行。

    只要中斷點條件是唯一的執行緒，且偵錯工具不會叫用其他任何中斷點 （您可能需要停用） 其他執行緒上的，您可以不進入程式碼，並逐步執行程式碼，而不需要切換至其他執行緒。

    > [!NOTE]
    > 當您進入偵錯工具時，會執行所有執行緒。 不過，偵錯工具不會中斷其他執行緒上的程式碼中，除非其中一個其他執行緒叫用中斷點。

## <a name="see-also"></a>另請參閱

- [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [如何：在偵錯時切換到另一個執行緒](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [如何：使用 [平行堆疊] 視窗](../debugger/using-the-parallel-stacks-window.md)
- [如何：使用平行監看式視窗](../debugger/how-to-use-the-parallel-watch-window.md)