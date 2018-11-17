---
title: 開始使用偵錯工具 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 755c4a0b66c91aa37f96d3d6f06972878ee856b8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771614"
---
# <a name="getting-started-with-the-debugger"></a>開始使用偵錯工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 偵錯工具在任何語言都中都很容易使用。 在此我們會示範一個簡單的 C# 程式偵錯，但您可以將相同的步驟套用到 C++ 及 JavaScript 等其他語言的程式碼。  
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a> 基本的 C# 專案進行偵錯  
 讓我們開始的簡單 C# 主控台應用程式 (**檔案 / 新增 / 專案**，然後選取**Visual C#** ，然後選取**主控台應用程式**)。 如果您從未使用過之前的 Visual studio，請參閱[逐步解說： 建立簡單的應用程式](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)。 **Main**方法只是將 1 加到整數變數 10 次，並會列印到主控台的結果：  
  
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
  
 建置此程式碼**偵錯**組態。 這是預設組態。 如需有關組態的詳細資訊，請參閱 <<c0> [ 了解組建組態](../ide/understanding-build-configurations.md)。  
  
 執行此程式碼偵錯工具中，依序按一下**偵錯] / [開始偵錯**(或**開始**的工具列上，或**F5**)。 應用程式幾乎會立即結束，因此您實際上無法分辨是否有任何資訊列印輸出到主控台視窗。  
  
 您可以設定中斷點，並在即將達到中斷點之前，停止已經執行一段時間的程式碼，然後再查看主控台視窗。 若要設定中斷點，請將游標置於`Console.WriteLine`行，然後按一下**偵錯 / 新的中斷點 / 函式中斷點**，或只按一下同一行的左邊界。 中斷點的外觀類似下圖所示：  
  
 ![設定中斷點](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 如需有關中斷點的詳細資訊，請參閱 < [Using Breakpoints](../debugger/using-breakpoints.md)。  
  
##  <a name="BKMK_Inspect_Variables"></a> 檢查變數  
 偵錯通常涉及尋找不包含在特定時間點的預期的值的變數。 我們將說明一些您可以檢查變數的方式。  
  
 開始再次偵錯。 在 `Console.WriteLine` 程式碼執行之前停止執行。 您可能會導致它繼續逐步執行 (按一下**偵錯] / [逐步移轉**或是**F10**)。 在此情況下您可能已選擇**逐步**(**F11**) 並取得相同的結果，我們將在稍後說明的差異。 方法中最後一個大括號所括起的行，應該會轉為黃色。 檢視主控台視窗 您應該會看到**10**。  
  
 您可以將滑鼠停留**testInt**變數，以在資料提示中檢視目前的值。  
  
 ![DBG&#95;Basics&#95;Data&#95;Tips](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 您應該只在程式碼視窗下方會看到**自動變數**，**區域變數**，並**監看式**windows。 這些視窗會顯示執行時變數目前的值。 這兩個**自動變數**並**區域變數**windows 顯示**testInt**的值**10**。  
  
 ![偵錯時的自動變數 視窗](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 如需有關這些視窗的詳細資訊，請參閱[自動變數 和 [區域變數] 視窗](../debugger/autos-and-locals-windows.md)。  
  
 讓我們看看變數值如何隨著我們逐步執行程式而變更。 上設定中斷點`testInt += 1;`行，然後重新啟動偵錯。 您應該會看到**testInt**中**區域變數**並 **[自動變數]** windows 是**0**，並**我**是**1**。 當您繼續偵錯 (**偵錯] / [繼續**，或**繼續**的工具列上，或**F5**)，您可以看到的值**testInt**若要變更**1**，然後**2**，依此類推。 當您不想查看這些變更，以移除中斷點 (**偵錯] / [切換中斷點**，或按一下上面的邊界)，並繼續偵錯。 如果您想要移除所有中斷點，請按一下**偵錯] / [刪除所有中斷點**，或**CTRL + SHIFT + F9**，然後按一下**是**上的對話方塊中，會要求**嗎想要移除所有中斷點嗎？**.  
  
## <a name="stepping-into-and-over-function-calls"></a>逐步執行函式呼叫及不進入函式呼叫  
 您可以在偵錯工具陳述式所-陳述式來執行程式碼 (**逐步**) 或偵錯工具會略過的函式時，您可以執行程式碼 (**不進入函式**) 若要快速取得您正在比較有興趣 （程式碼函式程式碼仍會執行）。 您可以在相同的偵錯工作階段中的這兩種方法之間進行切換。  
  
 若要查看之間的差異**逐步**並**不進入函式**，我們需要加入另一個方法呼叫的方法。 將方法加入 C# 應用程式，並從 Main 方法呼叫該方法。 此程式碼應該類似下列所示：  
  
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
  
 在 Main 方法中的 `Method1();` 呼叫上設定中斷點，並開始偵錯。 中斷執行時，按一下**偵錯] / [逐步執行**(或**逐步**的工具列上，或**F11**)。 在 Method1() 中第一個大括號再次中斷執行：  
  
 ![逐步執行程式碼](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 停止偵錯和重新啟動，並在中斷點中斷執行，當按一下**偵錯] / [逐步移轉**(或**不進入函式**的工具列上，或**F10**)。 於 `Console.WriteLine("end");` 再次中斷執行。  
  
 如果您想要深入了解偵錯工具巡覽程式碼，請參閱 <<c0> [ 使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)。





