---
title: 使用偵錯工具消費者入門 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
manager: jillfra
ms.openlocfilehash: e093abd5e836bcb7ee236979c00d574a07ecfd3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202330"
---
# <a name="getting-started-with-the-debugger"></a>開始使用偵錯工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 偵錯工具在任何語言都中都很容易使用。 在此我們會示範一個簡單的 C# 程式偵錯，但您可以將相同的步驟套用到 C++ 及 JavaScript 等其他語言的程式碼。  
  
## <a name="debug-a-basic-c-project"></a><a name="BKMK_Start_debugging_a_VS_project"></a> 對基本 c # 專案進行 Debug  
 讓我們從簡單的 c # 主控台應用程式開始， (檔案 **/新增/專案**，然後選取 [ **Visual c #** ]，然後選取 [ **主控台應用程式**) 。 如果您從未使用過 Visual Studio，請參閱 [逐步解說：建立簡單的應用程式](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)。 **Main**方法只會將1加到整數變數10次，並將結果列印到主控台：  
  
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
  
 在 **調試** 程式設定中建立此程式碼。 這是預設組態。 如需設定的詳細資訊，請參閱 [瞭解組建](../ide/understanding-build-configurations.md)設定。  
  
 若要在偵錯工具中執行此程式碼，請按一下 [ **Debug/開始調試** 程式] (或在工具列上 **啟動** ，或按 **F5**) 。 應用程式幾乎會立即結束，因此您實際上無法分辨是否有任何資訊列印輸出到主控台視窗。  
  
 您可以設定中斷點，並在即將達到中斷點之前，停止已經執行一段時間的程式碼，然後再查看主控台視窗。 若要設定中斷點，請將游標放在 `Console.WriteLine` 該行，然後按一下 [偵測] **/[新增中斷點]/**[函式中斷點]，或直接在同一行的左邊界中按一下。 中斷點的外觀類似下圖所示：  
  
 ![設定中斷點](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 如需中斷點的詳細資訊，請參閱 [使用中斷點](../debugger/using-breakpoints.md)。  
  
## <a name="inspect-variables"></a><a name="BKMK_Inspect_Variables"></a> 檢查變數  
 偵錯工具通常需要尋找未包含您預期特定點值的變數。 我們將示範一些可供您檢查變數的方式。  
  
 開始再次偵錯。 在 `Console.WriteLine` 程式碼執行之前停止執行。 您可以逐步執行 (按一下 [Debug]/[ **跳過** ] 或 [ **F10** ]) 來執行它。 在此情況下，您可以選擇 [ **逐步** 執行] (**F11**) 並取得相同的結果;我們稍後會說明其差異。 方法中最後一個大括號所括起的行，應該會轉為黃色。 檢視主控台視窗 您應該會看到 **10**。  
  
 您可以將滑鼠停留在 **testInt** 變數上，以在資料提示中查看目前的值。  
  
 ![DBG&#95;基本&#95;資料&#95;秘訣](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 在程式碼視窗下方，您應該會 **看到 [自動**變數]、[ **區域變數** **] 和 [監看** 式] 視窗。 這些視窗會顯示執行時變數目前的值。 [自動變數] **和 [** **區域變數** ] 視窗會顯示 **testInt** ，其值為 **10**。  
  
 ![偵錯時的自動變數視窗](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 如需這些視窗的詳細資訊，請參閱自動 [變數和區域變數視窗](../debugger/autos-and-locals-windows.md)。  
  
 讓我們看看變數值如何隨著我們逐步執行程式而變更。 在該行設定中斷點 `testInt += 1;` ，然後重新開機偵錯工具。 您應該會在 [區域變數] 和 [自動**變數** **] 視窗中**看到**testInt**是**0**，而**我**是**1**。 當您繼續進行偵錯工具 (**Debug/continue**，或在工具列上 **繼續** ，或按 **F5**) 時，您可以看到 **testInt** 的值變更為 **1**、 **2**，依此類推。 當您厭倦查看這些變更時，請移除中斷點 (**Debug/切換中斷點**，或在邊界) 中按一下它，然後繼續進行偵錯工具。 如果您想要移除所有中斷點，請按一下 [**偵錯工具/刪除所有中斷點**] 或**CTRL + SHIFT + F9**，然後在詢問**您是否要移除所有中斷點**的對話方塊中按一下 **[是**]。  
  
## <a name="stepping-into-and-over-function-calls"></a>逐步執行函式呼叫及不進入函式呼叫  
 您可以在偵錯工具語句中執行程式碼 (**逐步** 執行) 或者，您可以在偵錯工具略過函式時執行程式 **代碼 (不** 進入) ，以快速取得您更感興趣 (函式程式碼仍) 執行的程式碼。 您可以在相同的調試會話中切換這兩種方法。  
  
 若要查看 [逐步**執行] 和 [** 不**進入**] 之間的差異，我們必須加入由另一個方法所呼叫的方法。 將方法加入 C# 應用程式，並從 Main 方法呼叫該方法。 此程式碼應該類似下列所示：  
  
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
  
 在 Main 方法中的 `Method1();` 呼叫上設定中斷點，並開始偵錯。 當執行中斷時，在工具列上按一下 [ **Debug]/** [ (逐步執行] 或 [逐步執行] **，或按** **F11**) 。 在 Method1() 中第一個大括號再次中斷執行：  
  
 ![逐步執行程式碼](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 停止錯並重新啟動，並在中斷點中斷時，按一下工具列上的 [ **Debug/over** (] 或 [ **跳過** ]，或按 **F10 鍵**) 。 於 `Console.WriteLine("end");` 再次中斷執行。  
  
 如果您想要深入瞭解如何使用偵錯工具來導覽程式碼，請參閱 [使用偵錯工具流覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)。
