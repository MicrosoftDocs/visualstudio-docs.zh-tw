---
title: "檢查您的應用程式使用歷程偵錯 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 91cef7c8c037421b69cd13e69ab21543aaf89839
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio"></a>檢查與 IntelliTrace 歷程偵錯 Visual Studio 中的應用程式
您可以使用[歷程偵錯](../debugger/historical-debugging.md)向後移動和向前逐步執行您的應用程式並檢查其狀態。  
  
您可以在 Visual Studio Enterprise 版本而非 Professional 或 Community 版本中使用 IntelliTrace。  
  
## <a name="navigate-your-code-with-historical-debugging"></a>瀏覽您的程式碼使用歷程偵錯  
 讓我們從內含 bug 的簡單程式開始。 在 C# 主控台應用程式中，加入下列程式碼：  
  
```CSharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 我們假設預期值`resultInt`之後呼叫`AddAll()`為 20 (遞增的結果`testInt`20 倍)。 (我們也假設您無法看到中的 bug `AddInt()`)。但是，結果實際上是 44。 如何在不逐步執行 `AddAll()` 10 次的情況下找到 Bug？ 我們可以使用歷程偵錯更快且更輕鬆地找出錯誤。 方式如下：  
  
1.  在**工具 > 選項 > IntelliTrace > 一般**，請確定已啟用 IntelliTrace，然後選取**IntelliTrace 事件和呼叫資訊**。 如果您未選取此選項，則無法看到巡覽邊 (如下所述)。  
  
2.  在 `Console.WriteLine(resultInt);` 行上設定中斷點。  
  
3.  開始偵錯。 程式碼會執行到中斷點。 在**區域變數**視窗中，您可以看到的值`resultInt`是 44。  
  
4.  開啟**診斷工具**視窗 (**偵錯 > 顯示診斷工具**)。 程式碼視窗應該如下所示：  
  
     ![在中斷點的程式碼視窗](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  您應該會在左邊界旁邊看到雙箭頭，就在中斷點正上方。 這個區域稱為巡覽邊，並用於歷程偵錯。 按一下箭頭。  
  
     在程式碼視窗中，您應該會看到前一行程式碼 (`int resultInt = AddIterative(testInt);`) 加上粉紅色。 在視窗上方，您應該會看到一個訊息，現在您已經準備進行歷程偵錯。  
  
     程式碼視窗現在如下所示：  
  
     ![歷程偵錯模式中的程式碼視窗](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  現在您可以逐步執行`AddAll()`方法 (**F11**，或**逐步執行**巡覽邊中的按鈕。 逐步往前 (**F10**，或**移至下一個呼叫**巡覽邊中。 粉紅色行現在位於 `j = AddInt(j);` 行。 **F10**在此情況下不會逐步下一行程式碼。 而是會逐步執行至下一個函式呼叫。 歷程偵錯呼叫會巡覽不同的呼叫，並略過不包括函式呼叫的程式碼行。  
  
7.  現在會逐步執行 `AddInt()` 方法。 您應該會立即看到此程式碼中的 Bug。  

## <a name="next-steps"></a>後續步驟

此程序只會大略探討您可以如何處理歷程偵錯。

- 若要檢視快照集，偵錯時，請參閱[檢視使用 IntelliTrace 步驟後的快照集](../debugger/how-to-use-intellitrace-step-back.md)。
- 若要進一步了解不同的設定以及巡覽邊中不同按鈕的效果，請參閱[IntelliTrace 功能](../debugger/intellitrace-features.md)。