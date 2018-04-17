---
title: 開始使用 Visual Studio 中偵錯工具 |Microsoft 文件
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: get-started-article
ms.assetid: 0b3138c4-b840-446a-a15c-10ed8e2dd050
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 171b07d453c81883354848f70458bab39daa313e
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2018
---
# <a name="get-started-with-the-visual-studio-debugger"></a>開始使用 Visual Studio 偵錯工具
Visual Studio 偵錯工具在任何語言都中都很容易使用。 這裡我們會示範一個簡單的 C# 程式，偵錯，但您可以將相同的步驟套用至 c + + 及 JavaScript 等其他語言中的程式碼。

若要觀看視訊，其中顯示類似的功能，請參閱[偵錯工具使用者入門](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6)。
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a> 基本的 C# 專案進行偵錯  
 讓我們從簡單 C# 主控台應用程式開始 (**檔案 > 新增 > 專案**，然後選取**Visual C#**然後**主控台應用程式**)。 如果您從未使用過 Visual Studio 過，請參閱[逐步解說： 建立簡單的應用程式](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)。 **Main**方法只要將 1 加入至整數變數 10 次，並會列印到主控台的結果：  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 建置此程式碼**偵錯**組態。 這是預設組態。 如需有關組態的詳細資訊，請參閱[了解建置組態](../ide/understanding-build-configurations.md)。  
  
 執行這個程式碼偵錯工具中，依序按一下**偵錯 > 開始偵錯**(或**啟動**的工具列上，或**F5**)。 應用程式幾乎會立即結束，因此您實際上無法分辨是否任何項目列印輸出在主控台視窗中。  
  
 您可以設定中斷點，並在即將達到中斷點之前，停止已經執行一段時間的程式碼，然後再查看主控台視窗。 若要設定中斷點，請將游標置於`Console.WriteLine`直線，並按一下**偵錯 > 新增中斷點 > 函式中斷點**，或只按一下同一行的左邊界。 中斷點的外觀類似下圖所示：  
  
 ![設定中斷點](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 如需有關中斷點的詳細資訊，請參閱[使用中斷點](../debugger/using-breakpoints.md)。  
  
##  <a name="BKMK_Inspect_Variables"></a> 檢查變數  
 偵錯通常包括找出不包含您預期在特定時間點值的變數。 我們將示範一些您可以檢查變數的方式。  
  
 開始再次偵錯。 在 `Console.WriteLine` 程式碼執行之前停止執行。 您可以讓它繼續逐步執行 (按一下**偵錯 > 不進入函式**或**F10**)。 在此情況下您可能已選擇**逐步執行**(**F11**) 並收到相同的結果，我們將在稍後說明的差異。 方法中最後一個大括號所括起的行，應該會轉為黃色。 檢視主控台視窗 您應該會看到**10**。  
  
 您可以將滑鼠停留在**testInt**變數，以檢視資料提示中的目前值。  
  
 ![DBG&#95;Basics&#95;Data&#95;Tips](../debugger/media/dbg_basics_data_tips.png "DBG_Basics_Data_Tips")  
  
 您應該只在程式碼視窗下方會看到**自動變數**，**區域變數**，和**監看式**windows。 這些視窗會顯示執行時變數目前的值。 這兩個**自動變數**和**區域變數**windows 顯示**testInt**值是**10**。  
  
 ![偵錯時的自動變數視窗](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 如需有關這些視窗的詳細資訊，請參閱[自動變數 和 [區域變數] 視窗](../debugger/autos-and-locals-windows.md)。  
  
 我們來看看如何隨著我們逐步執行程式變更變數的值。 上設定中斷點`testInt += 1;`行，然後重新啟動偵錯。 您應該會看到**testInt**中**區域變數**和**自動變數**windows **0**，和**我**是**1**。 當您繼續偵錯 (**偵錯 > 繼續**，或**繼續**的工具列上，或**F5**)，您可以看到的值**testInt**若要變更**1**，然後**2**，依此類推。 當您想再觀查這些變更時，以移除中斷點 (**偵錯 > 切換中斷點**，或按一下邊界上)，然後繼續偵錯。 如果您想要移除所有中斷點，請按一下**偵錯 > 刪除所有中斷點**，或**CTRL + SHIFT + F9**，然後按一下**是**對話方塊，詢問上**執行您想要移除所有中斷點嗎？**.  
  
## <a name="stepping-into-and-over-function-calls"></a>逐步執行函式呼叫及不進入函式呼叫  
 您可以在 偵錯工具陳述式所-陳述式中執行程式碼 (**逐步執行**) 或偵錯工具會略過函式時，您可以執行程式碼 (**不進入函式**) 若要快速取得程式碼，您感興趣 （函式程式碼仍會執行）。 您可以在相同的偵錯工作階段中這兩種方法之間切換。  
  
 若要查看之間的差異**逐步執行**和**不進入函式**，我們需要加入另一個方法呼叫的方法。 將方法加入 C# 應用程式，並從 Main 方法呼叫該方法。 此程式碼應該類似下列所示：  
  
```csharp  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 在 Main 方法中的 `Method1();` 呼叫上設定中斷點，並開始偵錯。 當執行中斷時，按一下**偵錯 > 逐步執行**(或**逐步執行**的工具列上，或**F11**)。 在 Method1() 中第一個大括號再次中斷執行：  
  
 ![逐步執行程式碼](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 停止偵錯和重新啟動，並在中斷點中斷執行，當按一下**偵錯 > 不進入函式**(或**不進入函式**的工具列上，或**F10**)。 於 `Console.WriteLine("end");` 再次中斷執行。  
  
 如果您想要瞭解如何使用偵錯工具巡覽程式碼的詳細資訊，請參閱[使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)。