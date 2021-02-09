---
title: 瞭解如何對多執行緒應用程式進行偵錯工具
description: 在 Visual Studio 中使用 [平行堆疊] 和 [平行監看式] 視窗進行調試
ms.custom: ''
ms.date: 02/14/2020
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 28f9ab13cca4f1d31973f9526063eaa56574dcf4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870515"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>開始對多執行緒應用程式進行偵錯工具 (c #、Visual Basic、c + +) 

Visual Studio 提供數個工具和使用者介面元素，以協助您進行多執行緒應用程式的偵錯工具。 本教學課程示範如何使用執行緒標記、[ **平行堆疊** ] 視窗、[ **平行監看** 式] 視窗、條件中斷點和篩選中斷點。 完成本教學課程將讓您熟悉用於調試多執行緒應用程式的 Visual Studio 功能。

這兩個主題提供使用其他多執行緒調試工具的其他資訊：

- 若要使用 [ **偵錯工具位置** ] 工具列和 [ **執行緒** ] 視窗，請參閱逐步解說 [：將多執行緒應用程式偵錯工具](../debugger/how-to-use-the-threads-window.md)。

- 如需使用 <xref:System.Threading.Tasks.Task> (managed 程式碼) 和並行執行時間 (c + +) 的範例，請參閱 [逐步解說：將平行應用程式進行偵錯工具](../debugger/walkthrough-debugging-a-parallel-application.md)。 如需適用于大部分多執行緒應用程式類型的一般偵錯工具提示，請閱讀該主題和這個主題。

您將首先需要多執行緒應用程式專案。 範例如下。

## <a name="create-a-multithreaded-app-project"></a>建立多執行緒應用程式專案

1. 開啟 Visual Studio 並建立新專案。

   ::: moniker range=">=vs-2019"

   如果 [開始] 視窗未開啟，請 **選擇 [** 檔案 > **開始視窗]**。

   在 [開始] 視窗中，選擇 [ **建立新專案**]。

   在 [建立新專案] 視窗的搜尋方塊中輸入或鍵入 ASP.NET。 接下來，從 [語言] 清單中選擇 **c #**、 **c + +** 或 **Visual Basic** ，然後從 [平臺] 清單中選擇 [ **Windows** ]。 

   套用語言和平臺篩選器之後，請選擇 **( .Net Core) 的主控台應用程式** ，或針對 c + + **主控台應用程式** 範本，然後選擇 **[下一步]**。

   > [!NOTE]
   > 如果您沒有看到正確的範本，請移至 [**工具**  >  **取得工具和功能**]，這會開啟 Visual Studio 安裝程式。 選擇 [ **.net 桌面開發** ] 或 [ **使用 c + + 的桌面開發** ] 工作負載，然後選擇 [ **修改**]。

   在 [**設定您的新專案**] 視窗中，于 [**專案名稱**] 方塊中輸入或輸入 *MyThreadWalkthroughApp* 。 然後，選擇 [ **建立**]。

   ::: moniker-end
   ::: moniker range="vs-2017"
   從頂端功能表列中 **，選擇 [** 檔案  >  **新增**  >  **專案**]。 在 [ **新增專案** ] 對話方塊的左窗格中，選擇下列專案：

   - 針對 c # 應用程式，請選擇 [ **Visual c #**] 底下的 [ **Windows 桌面**]，然後在中間窗格中選擇 [ **主控台應用程式 ( .NET Framework)**]。
   - 若為 Visual Basic 應用程式，請在 [ **Visual Basic**] 下選擇 [ **Windows 桌面**]，然後在中間窗格中選擇 [ **主控台應用程式 (] .NET Framework)**。
   - 若是 c + + 應用程式，請在 [ **Visual C++**] 下，選擇 [ **windows 桌面**]，然後選擇 [ **windows 主控台應用程式**]。

   如果您沒有看到 **主控台應用程式 ( .net Core)** 或針對 c + +，**主控台應用程式** 專案範本，請移至 [**工具**  >  **取得工具和功能**]，這會開啟 Visual Studio 安裝程式。 選擇 [ **.net 桌面開發** ] 或 [ **使用 c + + 的桌面開發** ] 工作負載，然後選擇 [ **修改**]。

   然後，輸入 *MyThreadWalkthroughApp* 之類的名稱，然後按一下 **[確定]**。

   選取 [確定]。
   ::: moniker-end

   新的主控台專案隨即出現。 建立專案之後，會出現原始程式檔。 根據您所選擇的語言，來源檔案可能會稱為 *Program.cs*、 *MyThreadWalkthroughApp .cpp* 或 *Module1*。

1. 刪除出現在原始程式檔中的程式碼，並將它取代為下列適當的範例程式碼。

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
                "The instance method called by the worker thread has ended. " + data);
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
    // #include "pch.h" // Use with pre-compiled header
    #include <thread>
    #include <iostream>
    #include <vector>
    #include <string>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::string str = std::to_string(data);
        std::cout << "The function called by the worker thread has ended. " + str<< std::endl;
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
                    "The instance method called by the worker thread has ended. " + data)
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

1. 在 [File] \(檔案\) 功能表上，選取 [Save All] \(全部儲存\)。

1.  () 只 Visual Basic 方案總管 (右窗格) 中，以滑鼠右鍵按一下專案節點，選擇 [ **屬性**]。 在 [ **應用程式** ] 索引標籤下，將 **啟始物件** 變更為 **Simple**。

## <a name="debug-the-multithreaded-app"></a>將多執行緒應用程式進行偵錯工具

1. 在 [原始程式碼編輯器] 中，尋找下列其中一個程式碼片段：

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

1. 以滑鼠左鍵按一下或語句的左邊裝訂 `Thread.Sleep` 線 `std::this_thread::sleep_for` ，以插入新的中斷點。

    在裝訂邊上，紅色圓圈表示中斷點設定在這個位置。

2. 在 [ **調試** ] 功能表上，選取 [ **開始調試** ] (**F5**) 。

    Visual Studio 會建立方案、應用程式會開始執行，並附加偵錯工具，然後應用程式會在中斷點停止。

3. 在 [原始程式碼編輯器] 中，找出包含中斷點的行。

### <a name="discover-the-thread-marker"></a><a name="ShowThreadsInSource"></a>探索執行緒標記  

1. 在調試的工具列中，選取 [ **在來源中顯示執行緒** ] 按鈕 ![顯示來源中的執行緒](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")。

2. 按 **F11** 鍵一次，讓偵錯工具在一行程式碼中前進。

3. 查看來源視窗左邊的裝訂邊。 在此行中，您會看到類似兩個雙絞線執行緒的 *執行緒標記* 圖示  ![執行緒標記](../debugger/media/dbg-thread-marker.png "ThreadMarker") 。 執行緒標記表示執行緒會停在這個位置上。

    中斷點可能會部分隱藏執行緒標記。

4. 將指標移到執行緒標記上。 隨即顯示資料提示，告訴您每個已停止執行緒的名稱和執行緒識別碼號碼。 在此情況下，名稱可能是 `<noname>` 。

5. 選取執行緒標記以查看快速鍵功能表上可用的選項。

### <a name="view-the-thread-locations"></a><a name="ParallelStacks"></a>查看執行緒位置

在 [ **平行堆疊** ] 視窗中，您可以在 [執行緒] 和 [工作]) 工作視圖的工作程式設計 (之間切換，也可以查看每個執行緒的呼叫堆疊資訊。 在此應用程式中，我們可以使用執行緒的觀點。

1. 選擇 [ **Debug**   >  **Windows**  >  **平行堆疊**] 來開啟 [平行堆疊] 視窗。 您應該會看到類似下面的內容。 確切的資訊會根據每個執行緒的目前位置、硬體和程式語言而有所不同。

    ![平行堆疊視窗](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    在此範例中，我們會從左至右看到 managed 程式碼的這項資訊：

    - 主執行緒 (左邊) 已停止 `Thread.Start` ，其中停止點是由執行緒標記圖示 ![執行緒標記](../debugger/media/dbg-thread-marker.png "ThreadMarker")所表示。
    - 有兩個執行緒進入 `ServerClass.InstanceMethod` ，其中一個是目前的執行緒 (黃色箭號) ，而另一個執行緒已在中停止 `Thread.Sleep` 。
    - 在右) 上 (的新執行緒也會啟動，但會在上停止 `ThreadHelper.ThreadStart` 。

2. 以滑鼠右鍵按一下 [ **平行堆疊** ] 視窗中的專案，以查看快捷方式功能表上可用的選項。

    您可以從這些快顯功能表執行各種動作，但在本教學課程中，我們會在 [ **平行監看** 式] 視窗中顯示更多詳細資料， (接下來的章節) 。

    > [!NOTE]
    > 若要查看包含每個執行緒資訊的清單查看，請改用 [ **執行緒** ] 視窗。 請參閱 [逐步解說： Debug 多執行緒應用程式](../debugger/how-to-use-the-threads-window.md)。

### <a name="set-a-watch-on-a-variable"></a>在變數上設定監看式

1. 選取 [ **Debug** Windows   >    >  **parallel watch**  >  **parallel watch 1**]，開啟 [平行監看式] 視窗。

2. 選取您在 `<Add Watch>` 第4個數據行中看到文字 (或空白標頭資料格的資料格) 然後輸入 `data` 。

    每個執行緒的資料變數值會出現在視窗中。

3. 選取您看到 `<Add Watch>` 文字 (的資料格，或第5個數據行中的空白標頭資料格) 然後輸入 `count` 。

    `count`每個執行緒的變數值會出現在視窗中。 如果您還沒看到這項資訊，請試著按幾次 **F11** ，以在偵錯工具中繼續執行執行緒。

    ![平行監看式視窗](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. 以滑鼠右鍵按一下視窗中的其中一個資料列，以查看可用的選項。

### <a name="flag-and-unflag-threads"></a>將執行緒加上旗標和取消旗標
您可以為執行緒加上旗標，以追蹤重要的執行緒，並忽略其他執行緒。

1. 在 [ **平行監看** 式] 視窗中，按住 **Shift** 鍵，然後選取多個資料列。

2. 以滑鼠右鍵按一下並選取 [ **旗** 標]。

    所有選取的執行緒都會加上旗標。 現在，您可以篩選，只顯示已加上旗標的執行緒。

3. 在 [ **平行監看** 式] 視窗中，選取 [ **僅顯示** 加上旗標的執行緒] 按鈕以 ![顯示標示](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker")的

    只有已加上旗標的執行緒才會出現在清單中。

    > [!TIP]
    > 在您標示某些執行緒之後，您可以用滑鼠右鍵按一下程式碼編輯器中的一行程式碼，然後選擇 [ **執行標示為執行緒] 游標**。 請務必選擇所有標示的執行緒都會到達的程式碼。 Visual Studio 將會在所選的程式程式碼上暫停執行緒，讓您可以藉由 [凍結和解除凍結執行緒](#bkmk_freeze)，更輕鬆地控制執行的順序。

4. 再次選取 [ **僅顯示** 已加上旗標的執行緒] 按鈕，切換回以 **顯示所有線程** 模式。

5. 若要取消標示執行緒，請在 [**平行監看** 式] 視窗中，以滑鼠右鍵按一下一或多個加上旗 **標的執行緒**

### <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a> 凍結和解除凍結執行緒執行

> [!TIP]
> 您可以凍結和解除凍結 (暫停和繼續) 執行緒，以控制執行緒執行工作的順序。 這可協助您解決並行問題，例如鎖死和競爭情形。

1. 在 [ **平行監看** 式] 視窗中，選取所有資料列，按一下滑鼠右鍵並選取 [ **凍結**]。

    在第二個數據行中，每個資料列都會出現一個暫停圖示。 暫停圖示表示執行緒已凍結。

2. 選取一個資料列，即可取消選取所有其他資料列。

3. 以滑鼠右鍵按一下資料列，然後選取 [ **解除凍結**]。

    暫停圖示會在此資料列中消失，表示執行緒已不再凍結。

4. 切換至 [程式碼編輯器]，然後按 **F11** 鍵。 只有未凍結的執行緒才會執行。

    應用程式也可能會具現化一些新的執行緒。 任何新的執行緒都未標記且不會凍結。

### <a name="follow-a-single-thread-with-conditional-breakpoints"></a><a name="bkmk_follow_a_thread"></a> 遵循具有條件式中斷點的單一執行緒

在偵錯工具中執行單一執行緒可能會很有説明。 其中一個方法是凍結您不感興趣的執行緒。 在某些情況下，您可能需要在不凍結其他執行緒的情況下，遵循單一執行緒，例如重現特定的錯誤。 若要在不凍結其他執行緒的情況下追蹤執行緒，您必須避免中斷程式碼，但不包括您感興趣的執行緒。 您可以設定 [條件式中斷點](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)來完成這項作業。

您可以在不同的條件（例如執行緒名稱或執行緒識別碼）上設定中斷點。 它可能很有説明，就是針對您已知對每個執行緒而言是唯一的資料設定條件。 這是常見的偵錯工具案例，在此情況下，您對某些特定的資料值比較感興趣，而非任何特定的執行緒。

1. 以滑鼠右鍵按一下您先前建立的中斷點，然後選取 [ **條件**]。

2. 在 [ **中斷點設定** ] 視窗中，輸入 `data == 5` 條件運算式。

    ![條件中斷點](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > 如果您對特定執行緒更有興趣，請使用條件的執行緒名稱或執行緒識別碼。 若要在 [ **中斷點設定** ] 視窗中執行這項操作，請選取 [ **篩選** ]，不要選取 [ **條件運算式**]，並遵循篩選提示。 當您重新開機偵錯工具時，您可能會想要在應用程式程式碼中命名您的執行緒，因為執行緒識別碼會變更。

3. 關閉 [ **中斷點設定** ] 視窗。

4. 選取 [重新開機 ![重新開機應用程式](../debugger/media/dbg-tour-restart.png ">restartapp") ] 按鈕，重新開機您的偵錯工具會話。

    您將會在資料變數值為5的執行緒上中斷程式碼。 在 [ **平行監看** 式] 視窗中，尋找指出目前偵錯工具內容的黃色箭號。

5. 現在，您可以不進入程式碼 (**F10**) ，然後逐步執行程式碼 (**F11**) 並遵循單一執行緒的執行。

    只要中斷點條件對執行緒而言是唯一的，而且偵錯工具並不會叫用其他執行緒上的任何其他中斷點 (您可能需要停用它們) ，您可以不進入程式碼並逐步執行程式碼，而不需要切換到其他執行緒。

    > [!NOTE]
    > 當您前進偵錯工具時，將會執行所有線程。 但是，偵錯工具不會在其他執行緒上中斷程式碼，除非其中一個執行緒叫用中斷點。

## <a name="see-also"></a>另請參閱

- [對多執行緒應用程式進行偵錯](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [如何：在偵錯時切換到另一個執行緒](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [如何：使用平行堆疊視窗](../debugger/using-the-parallel-stacks-window.md)
- [如何：使用平行監看式視窗](../debugger/how-to-use-the-parallel-watch-window.md)