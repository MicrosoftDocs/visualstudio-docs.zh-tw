---
title: '分析 CPU 使用量資料 (ASP.NET Core) '
description: 使用 CPU 使用量診斷工具測量 ASP.NET Core 應用程式中的應用程式效能
ms.custom: mvc
ms.date: 02/14/2020
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: aa0c95e3a9f3598cd6399b565adb75faccac22a8
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761143"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet-core"></a>快速入門：在 Visual Studio (ASP.NET Core 中分析 CPU 使用量資料) 

Visual Studio 提供許多功能強大的功能，可協助您分析應用程式中的效能問題。 本主題提供了解一些基本功能的快速方法。 在這裡，我們會查看工具，找出因高 CPU 使用量而造成的效能瓶頸。 診斷工具可用於 Visual Studio 中的 .NET 開發 (包括 ASP.NET) 和原生/C++ 開發。

診斷中樞提供許多其他選項來執行和管理診斷工作階段。 如果這裡所述的 [CPU 使用量] 工具未提供您所需的資料，則[其他分析工具](../profiling/profiling-feature-tour.md)可提供不同種類的資訊，這可能會很有幫助。 在許多情況下，應用程式的效能瓶頸可能是 CPU 以外的問題所導致，例如記憶體、呈現 UI 或網路要求時間。 [效能提示](../profiling/perftips.md)是另一個偵錯工具整合的程式碼剖析工具，它也可讓您逐步執行程式碼，並識別特定函式或程式碼區塊完成的時間。

Windows 8 及更新版本必須執行附有偵錯工具的分析工具 ([診斷工具] 視窗)。 在 Windows 7 及更新版本，您可以使用事後分析工具：[效能分析工具](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>建立專案

1. 開啟 Visual Studio 並建立專案。

   ::: moniker range="vs-2017"
   從頂端功能表列中 **，選擇 [** 檔案 > **新增** > **專案**]。

   在左窗格的 [ **新增專案** ] 對話方塊中，展開 [ **Visual c #**]，然後選擇 [ **Web**]。 在中間窗格中，選擇 [ **ASP.NET Web 應用程式 ( .Net Core)**]。 然後將專案命名為 *MyProfilingApp_MVC*。

   > [!NOTE]
   > 如果您沒有看到 **ASP.NET Web 應用程式 ( .Net Core)** 專案範本，請在 [**新增專案**] 對話方塊的左窗格中，選擇 [**開啟] Visual Studio 安裝程式** 連結。 Visual Studio 安裝程式即會啟動。 選擇 [ASP.NET 與網頁程式開發] 工作負載，然後選擇 [修改]。

   在出現的對話方塊中，選擇中間窗格中的 [MVC]，然後按一下 [確定]。
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   在 Visual Studio 2019 中，選擇 [開始] 視窗中的 [ **建立新專案** ]。 如果 [開始] 視窗未開啟，請 **選擇 [** 檔案  >  **開始視窗]**，然後選擇 [**建立新專案**]。

   在 [搜尋] 方塊中輸入 **web 應用程式**，選擇 [ **c #** ] 作為 [語言]，選擇 [ **ASP.NET Core 的 Web 應用程式] (模型視圖控制器)**]，然後選擇 **[下一步]** 在下一個畫面中，將專案命名為 *MyProfilingApp_MVC*，然後選擇 **[下一步]**。

   選擇建議的目標架構 ( .NET Core 3.1) 或 .NET 5，然後選擇 [ **建立**]。

   > [!NOTE]
   > 如果您沒有看到 **ASP.NET Web 應用程式 ( .Net Core)** 範本，您可以從 [ **建立新專案** ] 視窗進行安裝。 在 [找不到您要找的資料嗎?] 訊息中，選擇 [安裝更多工具和功能] 連結。 然後，在 Visual Studio 安裝程式中選擇 **ASP.NET 與網頁程式開發** 工作負載。
   ::: moniker-end

   Visual Studio 建立並開啟您的新專案。

1. 在方案總管中，以滑鼠右鍵按一下 [模型] 資料夾，然後選擇 [**加入**  >  **類別**]。

1. 將新的類別命名為 `Data.cs`，然後選擇 [新增]。

1. 在方案總管中，開啟 `Models/Data.cs`，然後將下列 `using` 陳述式新增至檔案頂端：

    ```csharp
    using System.Threading;
    ```

1. 在 Data.cs 中，將下列程式碼：

    ```csharp
    public class Data
    {
    }
    ```

    使用此程式碼取代：

    ```csharp
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void GenerateData()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            var x = GetNumber();
        }

        private int GetNumber()
        {
            var rand = new Random();
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);
            var result = 0;
            lock (m_totalItersLock)
            {
                m_totalIterations += iters;
            }
            // we're just spinning here
            // and using Random to frustrate compiler optimizations
            for (var i = 0; i < iters; i++)
            {
                result = rand.Next();
            }
            return result;
        }
    }

    public class Simple
    {
        int numberOfThreads = 200;

        public Simple()
        {
            for (int i = 0; i < numberOfThreads; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.GenerateData));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }

        public int GetData()
        {
            // Not returning any meaningful data.
            return numberOfThreads;
        }
    }
    ```

1. 在方案總管中，開啟 *Controller/homecontrollers.cs*，並取代下列程式碼：

   ::: moniker range="vs-2017"

    ```csharp
    public ActionResult About()
    {
        ViewBag.Message = "Your application description page.";

        return View();
    }
    ```

    使用此程式碼取代：

    ```csharp
    public ActionResult About()
    {
        Models.Simple s = new Models.Simple();

        ViewBag.Message = "Your application description page.";

        return View(s.GetData());
    }
    ```

    ::: moniker-end
    ::: moniker range=">=vs-2019"

    ```csharp
    public IActionResult Privacy()
    {
        return View();
    }
    ```

    使用此程式碼取代：

    ```csharp
    public IActionResult Privacy()
    {
        Models.Simple s = new Models.Simple();

        return View(s.GetData());
    }
    ```

    ::: moniker-end


## <a name="step-1-collect-profiling-data"></a>步驟 1︰收集分析資料

1. 首先，在 `Simple` 建構函式的這行程式碼上，於應用程式中設定中斷點：

    `for (int i = 0; i < 200; i++)`

    按一下程式碼行左側的裝訂邊，以設定中斷點。

1. 接下來，在 `Simple` 建構函式結尾的右大括弧上，設定第二個中斷點：

     ![設定中斷點進行分析](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    藉由設定兩個中斷點，您可以將資料收集的範圍限制在您想分析的程式碼部分。

1. 除非您關閉 [診斷工具] 視窗，否則該視窗已出現。 若要再次顯示視窗，請按一下 [ **Debug**  >  **Windows**  >  **Show 診斷工具**]。

1. 按一下 [ **Debug**  >  **開始** 錯 (] 或 [**啟動**] 工具列上的 [啟動]，或按 **F5**) 。

1. 當應用程式完成載入時，請按一下網頁頂端的適當連結來開始執行新程式碼。

   ::: moniker range="vs-2017"
   在 Visual Studio 2017 中，按一下 [ **關於** ] 連結以執行程式碼。
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   在 Visual Studio 2019 中，按一下 [ **隱私權** ] 連結以執行程式碼。
   ::: moniker-end

1. 請查看 [診斷工具] 的 [摘要] 檢視。

1. 當偵錯工具暫停時，請啟用 CPU 使用量資料的收集，方法是選擇 [記錄 CPU 分析]，然後開啟 [CPU 使用量] 索引標籤。

     ![診斷工具啟用 CPU 分析](../profiling/media/quickstart-cpu-usage-summary.png)

     啟用資料收集時，記錄按鈕會顯示紅色圓圈。

     當您選擇 [記錄 CPU 分析] 時，Visual Studio 就會開始錄製您的函式以及它們所需的執行時間，也會提供您可以用來專注於取樣工作階段特定區段的時間軸圖表。只有在應用程式於中斷點停止時，您才能檢視這個收集的資料。

6. 按 F5 使應用程式執行至第二個中斷點。

     現在，您擁有在兩個中斷點之間執行的程式碼區域專屬的應用程式效能資料。

     程式碼剖析工具隨即開始準備執行緒資料。 等候它完成。

     [CPU 使用量] 工具會在 [CPU Usage (CPU 使用量)] 索引標籤中顯示報告。

     此時，您可以開始分析資料。

## <a name="step-2-analyze-cpu-usage-data"></a>步驟 2：分析 CPU 使用量資料

建議您先檢查 [CPU 使用量] 下方的函式清單、識別執行最多工作的函式，仔細觀察每一項，接著開始分析您的資料。

1. 在函式清單中，檢查執行最多工作的函式。

     ![診斷工具 CPU 使用量索引標籤](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > 執行工作最多的函式會優先列出 (不是以呼叫順序列出)。 這可協助您快速找出執行時間最長的函式。

2. 在函式清單中，按兩下 `MyProfilingApp_MVC.Models.ServerClass::GetNumber` 函式。

    當您按兩下函式時，[呼叫端/被呼叫端] 檢視會在左窗格中開啟。

    ![診斷工具的呼叫端/被呼叫端檢視](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    在此檢視中，選取的函式會出現在標題和 [目前的函式] 方塊中 (在此範例中為 `ServerClass::GetNumber`)。 呼叫目前函式的函式顯示在左邊的 [Calling Function (呼叫的函式)] 下方，而目前函式所呼叫的任何函式會顯示在右邊的 [Called Functions (所呼叫函式)] 方塊。 (您可以選取任一個方塊來變更目前的函式。)

    此檢視會顯示總時間 (毫秒) 及完成函式所需時間在整體應用程式執行時間所佔的百分比。

    [函式主體] 也會顯示函式主體所花費的總時間 (和時間百分比)，不包括呼叫的函式和所呼叫函式所花的時間。 (在此圖中，2235 毫秒中的 2220 毫秒花在函式主體，其餘時間 (< 20 毫秒) 則花在此函式所呼叫的外部程式碼)。 實際值會根據您的環境而不同。

    > [!TIP]
    > [函式主體] 值高可能表示函式本身內有效能瓶頸。

## <a name="next-steps"></a>下一步

- [分析記憶體使用量](../profiling/memory-usage.md)以找出效能瓶頸。
- [分析 CPU 使用量](../profiling/cpu-usage.md)以取得 CPU 使用量工具的詳細深入資訊。
- 不附加偵錯工具或是以執行中的應用程式為目標來分析 CPU 使用量。如需詳細資訊，請參閱[使用或不使用偵錯工具來執行分析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)中的[收集分析資料但不偵錯](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的分析](../profiling/index.yml)
- [初步認識分析工具](../profiling/profiling-feature-tour.md)
