---
title: "開始偵錯多執行緒應用程式 |Microsoft 文件"
ms.custom: H1HackMay2017
ms.date: 06/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 1d4298d60886d8fe8b402b59b1838a4171532ab1
ms.openlocfilehash: 3ffb550707280d76756cbd144ed03f4143ce144b
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="get-started-debugging-a-multithreaded-application-in-visual-studio"></a>開始偵錯 Visual Studio 中的多執行緒應用程式
Visual Studio 提供數個工具和可協助您偵錯多執行緒應用程式的使用者介面項目。 本教學課程示範如何使用執行緒標記**平行堆疊**視窗中，**平行監看式**視窗、 條件式中斷點和篩選中斷點。 本教學課程只需要幾分鐘時間，但是完成它會讓您熟悉的偵錯多執行緒應用程式的功能。

|         |         |
|---------|---------|
| ![觀看影片](../install/media/video-icon.png "WatchVideo") | [觀看影片](#video)多執行緒偵錯，顯示類似的步驟。 |

其他主題提供使用其他的多執行緒偵錯工具的其他資訊：

- 示範如何使用的類似主題**偵錯位置**工具列和**執行緒**視窗中，請參閱[逐步解說： 偵錯多執行緒應用程式](../debugger/how-to-use-the-threads-window.md)。

- 範例會使用具有類似主題的<xref:System.Threading.Tasks.Task>(managed 程式碼) 和並行執行階段 （c + +），請參閱[逐步解說： 偵錯平行應用程式](../debugger/walkthrough-debugging-a-parallel-application.md)。 如需適用於最多執行緒應用程式類型的一般偵錯秘訣，閱讀本主題和連結的主題。
  
若要開始本教學課程，您需要的多執行緒應用程式專案。 請依照下列步驟建立專案。  
  
#### <a name="to-create-the-multithreaded-app-project"></a>若要建立多執行緒應用程式專案  
  
1.  在**檔案**功能表上，選擇**新增**，然後按一下 **專案**。  
  
     [ **新增專案** ] 對話方塊隨即出現。  
  
2.  在**專案類型**s 方塊中，按一下您所選擇的語言： **Visual C#**， **Visual c + +**，或**Visual Basic**。  
  
3.  在**範本**方塊中，選擇**主控台應用程式**。  
  
4.  在**名稱**方塊中，輸入名稱 MyThreadWalkthroughApp。  
  
5.  按一下 [確定]。  
  
     新的主控台專案隨即出現。 專案建立之後，便會出現原始程式檔 (Source File)。 根據您選擇的語言，而可能 Program.cs、 MyThreadWalkthroughApp.cpp 或 Module1.vb 呼叫原始程式檔。  
  
6.  刪除原始程式檔中出現的程式碼，如下所示的範例程式碼取代它。

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
    #include "stdafx.h"
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
  
7.  在**檔案**功能表上，按一下 **全部儲存**。  
  
#### <a name="to-begin-the-tutorial"></a>若要開始本教學課程  
  
-   在原始碼程式碼編輯器中，尋找下列程式碼： 
  
    ```CSharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
#### <a name="to-start-debugging"></a>若要啟動偵錯  
  
1.  按一下左邊的裝訂邊的`Thread.Sleep`或`Thread::Sleep`陳述式來插入新的中斷點。  
  
     在原始碼程式碼編輯器左側裝訂邊上，會出現一個紅色圓圈。 這表示這個位置現在已設定中斷點。 
  
2.  在**偵錯**功能表上，按一下 **開始偵錯**(**F5**)。  
  
     Visual Studio 會建置方案，應用程式啟動偵錯工具附加，以執行，然後在中斷點停止應用程式。  
  
    > [!NOTE]
    > 如果您將焦點切換到主控台視窗，按一下 在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]視窗將焦點還給[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
4.  在原始碼程式碼編輯器中，找出包含中斷點的那一行：  
  
    ```CSharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    ```

    ```VB
    Thread.Sleep(3000)
    ```    
  
#### <a name="ShowThreadsInSource"></a>若要尋找執行緒標記  

1.  在 [偵錯] 工具列上，按一下 **在來源中顯示執行緒**按鈕![在來源中顯示執行緒](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")。

2. 按**F11**前進一行程式碼偵錯工具一次。
  
3.  查看來源視窗左邊的裝訂邊。 在這行中，您會看到*執行緒標記*圖示![執行緒標記](../debugger/media/dbg-thread-marker.png "ThreadMarker")類似於兩條布條。 執行緒標記表示執行緒會停在這個位置上。

    請注意，可能會在中斷點部分隱藏執行緒標記。 
  
4.  將指標移到執行緒標記上。 資料提示方塊就會出現。 資料提示方塊會指出每個已停止的執行緒的名稱和執行緒 ID 編號。 名稱在此情況下，可能是`<noname>`。 
  
5.  以滑鼠右鍵按一下執行緒標記，若要查看的捷徑功能表上的可用選項。
    
## <a name="ParallelStacks"></a>檢視執行緒的位置

在**平行堆疊**視窗中，您可以切換執行緒 檢視之間，並 （適用於以工作為基礎的程式設計） 工作 檢視中，而且您可以檢視每個執行緒的呼叫堆疊資訊。 在此應用程式中，我們可以使用 [執行緒] 檢視。

1. 開啟**平行堆疊**選擇視窗**偵錯 > Windows > 平行堆疊**。 您應該會看到類似這樣的項目 （確切的資訊將會根據每個執行緒、 硬體和您的程式語言的目前位置而不同）。

    ![平行堆疊 視窗](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    在此範例中，從左到右我們取得這項資訊：
    
    - 主執行緒 （左側） 已停止上`Thread.Start`(停止點會以執行緒標記圖示![執行緒標記](../debugger/media/dbg-thread-marker.png "ThreadMarker"))。
    - 兩個執行緒已進入`ServerClass.InstanceMethod`，其中是目前的執行緒 （黃色箭號），而另一個執行緒已停止在`Thread.Sleep`。
    - 新的執行緒 （右側） 也正在啟動 (停止`ThreadHelper.ThreadStart`)。

2.  以滑鼠右鍵按一下中的項目**平行堆疊**視窗來查看的捷徑功能表上的可用選項。

    您可以採取各種動作，從這些上按一下滑鼠右鍵功能表中，但本教學課程中我們會顯示更多詳細資料中**平行監看式**視窗 （下一節）。

    > [!NOTE]
    > 如果您是更有興趣查看清單檢視每個執行緒的相關資訊，請使用**執行緒**視窗改為。 請參閱[逐步解說： 偵錯多執行緒應用程式](../debugger/how-to-use-the-threads-window.md)。

## <a name="set-a-watch-on-a-variable"></a>在變數上設定監看式

1. 開啟**平行監看式**選擇視窗**偵錯 > Windows > 平行監看式 > 平行監看式 1**。

2. 按一下儲存格，您看到`<Add Watch>`文字 （或空的標頭中的儲存格第 4 個資料行），型別`data`，然後按 Enter。

    每個執行緒資料變數的值會出現在視窗中。

3. 再次按一下儲存格，您看到`<Add Watch>`文字 （或空的標頭中的儲存格第 5 個資料行），型別`count`，然後按 Enter。

    每個執行緒計數變數的值會出現在視窗中。 （如果您沒有看到這麼多資訊，請嘗試按下 F11 數次，若要繼續的偵錯工具中的執行緒執行。）

    ![[平行監看式] 視窗](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. 以滑鼠右鍵按一下其中一個資料列在視窗中，若要查看可用的選項。

## <a name="flagging-and-unflagging-threads"></a>將執行緒加上旗標和取消旗標  
您可以標示您要特別注意的執行緒。 加上旗標的執行緒是一個好的方法來追蹤重要的執行緒，並略過您不在意的執行緒。  
  
#### <a name="to-flag-threads"></a>若要為執行緒加上旗標  

1. 在**平行監看式**視窗中，按住 SHIFT 鍵並選取多個資料列。

2. 以滑鼠右鍵按一下，然後選擇 **旗標**。

    現在，所有選取的執行緒會加上旗標。 現在，您可以篩選要顯示已標幟的執行緒。
  
3.  在**平行監看式**視窗中，尋找**僅顯示已標幟的執行緒**按鈕![顯示已標幟執行緒](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker")。  
  
4.  按一下**僅顯示已標幟的執行緒** 按鈕。  
  
    現在清單中只會出現加上旗標的執行緒。

    > [!TIP]
    > 當您有某些執行緒加上標幟時，您可以在程式碼編輯器的程式碼行上按一下滑鼠右鍵並選擇**執行至游標處加上旗標的執行緒**（請確定您選擇的所有已標幟的執行緒程式碼會到達）。 這將會暫停程式碼，讓您更輕鬆地控制所執行的順序選取行上的執行緒[凍結和解除凍結執行緒](#bkmk_freeze)。

5.  按一下**僅顯示已標幟的執行緒**按鈕，切換回**顯示所有執行緒**模式。
    
#### <a name="to-unflag-threads"></a>若要取消執行緒的旗標

若要取消執行緒的旗標，您可以以滑鼠右鍵按一下一個或多個已標幟的執行緒，在**平行監看式**視窗，然後選擇 **取消旗標**。

## <a name="bkmk_freeze"></a>凍結和解除凍結執行緒的執行 

> [!TIP]
> 您可以凍結和解除凍結 （暫止和繼續） 控制執行緒執行工作順序的執行緒。 這可協助您解決並行存取問題，像是死結和競爭情形。
  
#### <a name="to-freeze-and-unfreeze-threads"></a>若要凍結和解除凍結執行緒  
  
1.  在**平行監看式**視窗中，所有選取的資料列，以滑鼠右鍵按一下並選取內含**凍結**。

    在第二個資料行，暫停圖示現在會顯示每個資料列。 暫停圖示表示已凍結執行緒。

2.  取消資料列選取一個資料列，即可。

3.  以滑鼠右鍵按一下資料列，然後選取**解除凍結**。

    暫停圖示消失在此資料列，指出已不再凍結執行緒。

4.  切換至程式碼編輯器中，按一下**F11**。 只有未凍結的執行緒會執行。

    應用程式可能也會執行個體化一些新的執行緒。 請注意，任何新的執行緒是未標示，並不會凍結。

## <a name="bkmk_follow_a_thread"></a>請依照下列單一執行緒，使用條件式中斷點

有時候，可能很有用的偵錯工具中的單一執行緒執行。 您可以執行的一種方法是凍結的執行緒，您不感興趣，但在某些情況下您可能想要在不凍結 （若要重現特定問題，例如） 的其他執行緒的情況下遵循單一執行緒。 若要依照沒有凍結的其他執行緒的執行緒，您必須避免中斷您感興趣的執行緒上的程式碼除外。 您可以藉由設定[條件中斷點](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)。

您可以設定中斷點，在不同的狀況，例如執行緒名稱或執行緒 id。 可能會很有幫助的另一個方法是在您知道將會是唯一的每個執行緒的資料上設定的條件。 這是常見的偵錯案例，您會更有興趣在任何特定的執行緒中某些特定的資料值。

#### <a name="to-follow-a-single-thread"></a>若要遵循單一執行緒

1. 以滑鼠右鍵按一下您先前建立的中斷點，然後選擇 **條件**。

2. 在**中斷點設定**視窗中，輸入`data == 5`條件運算式。

    ![條件式中斷點](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > 如果您是更有興趣的特定的執行緒，然後使用執行緒名稱或執行緒 ID 的條件。 若要這樣在**中斷點設定**視窗中，選取**篩選**而不是**條件運算式**，並依照篩選器的秘訣。 若要命名您的應用程式程式碼中的執行緒 （因為當您重新啟動偵錯工具時，就會變更執行緒 Id）。

3. 關閉**中斷點設定**視窗。

4. 按一下 重新啟動![重新啟動應用程式](../debugger/media/dbg-tour-restart.png "RestartApp")按鈕以重新啟動您的偵錯工作階段。

    您將會中斷資料變數的 5 的執行緒上的程式碼。 黃色箭號 （目前的偵錯工具內容） 尋找**平行監看式**視窗可讓您確認。

5. 現在，您可以不進入程式碼 (F10) 和逐步執行程式碼 (F11) 並遵循單一執行緒的執行。

    只要中斷點條件是唯一的執行緒，且偵錯工具不會叫用 （您可能需要停用它們） 的其他執行緒上的任何其他中斷點，您可以不進入程式碼，並逐步執行程式碼不需要切換到其他的執行緒。

    > [!NOTE]
    > 當您進入偵錯工具時，會執行所有執行緒。 不過，偵錯工具不會中斷其他執行緒上的程式碼，除非其中一個其他的執行緒叫用中斷點。 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>進一步了解多執行緒偵錯視窗 

#### <a name="to-switch-to-another-thread"></a>若要切換至另一個執行緒 

- 若要切換至另一個執行緒，請參閱[如何： 切換到另一個執行緒時偵錯](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

## <a name="video"></a>請觀看影片，以在多執行緒偵錯

<div style="padding-top: 56.25%; position: relative; width: 100%;">
<iframe style="position: absolute;top: 0;left: 0;right: 0;bottom: 0;" width="100%" height="100%" src="https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171" frameborder="0" allowfullscreen></iframe>
</div>

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>若要深入了解 平行堆疊 和 平行監看式視窗  
  
- 請參閱[How to： 使用平行堆疊視窗](../debugger/using-the-parallel-stacks-window.md) 

- 請參閱[How to： 使用平行監看式視窗](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>另請參閱  
 [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [如何：在偵錯時切換到另一個執行緒](../debugger/how-to-switch-to-another-thread-while-debugging.md)

