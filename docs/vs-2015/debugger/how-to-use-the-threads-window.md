---
title: 作法：使用執行緒視窗 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 835843d2328d9d17ac899fc12c97251b7e6b4659
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685327"
---
# <a name="how-to-use-the-threads-window"></a>作法：使用執行緒視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 [**執行緒**] 視窗中，您可以檢查及使用您正在偵錯的應用程式中的執行緒。  
  
 **執行緒**視窗包含的資料表，其中每個資料列會代表您的應用程式中的執行緒。 這份表格預設會列出應用程式中的所有執行緒，但是您可以篩選清單，只顯示您感興趣的執行緒。 每個資料行都會包含不同類型的資訊。 您也可以隱藏部分資料行。 如果您顯示所有資料行，則會從左到右顯示下列資訊：  
  
- 旗標資料行，您可以在其中標示想要特別注意的執行緒。 如需如何在執行緒的旗標的資訊，請參閱[How to:旗標，並將執行緒取消標幟](../debugger/how-to-flag-and-unflag-threads.md)。  
  
- 使用中執行緒資料行，其中黃色箭號表示使用中執行緒。 箭號的外框表示執行進入偵錯工具的執行緒。  
  
- **識別碼**資料行，內含每個執行緒的識別碼。  
  
- **Managed ID**資料行，內含 managed 執行緒的 managed 的識別碼。  
  
- **分類**資料行，可將執行緒分類為使用者介面執行緒、 遠端程序呼叫處理常式或背景工作執行緒。 特殊分類表示應用程式的主要執行緒。  
  
- **名稱**資料行，依名稱識別每個執行緒，如果有的話，或為\<無名稱 >。  
  
- **位置**資料行，它會顯示正在執行的執行緒。 您可以展開這個位置，以顯示執行緒的整個呼叫堆疊。  
  
- **優先順序**資料行，其中包含 優先順序 或 系統指派給每個執行緒的優先順序。  
  
- **Affinity Mask**資料行，也就是通常隱藏的進階資料行。 這個資料行顯示每個執行緒的處理器關連遮罩。 在多處理器系統中，關連遮罩會決定可以執行執行緒的處理器。  
  
- **暫停計數**資料行，內含暫停的計數。 這個計數決定是否可以執行執行緒。 如需暫停計數的說明，請參閱本主題後面的＜凍結和解除凍結執行緒＞。  
  
- **處理序名稱**資料行，內含每個執行緒所屬的程序。 當您偵錯多個處理序時，這個資料行十分有用，但它通常是隱藏的。  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>若要在中斷模式或執行模式顯示執行序視窗  
  
- 在 **偵錯**功能表上，指向**Windows**，然後按一下**執行緒**。  
  
### <a name="to-display-or-hide-a-column"></a>若要顯示或隱藏資料行  
  
- 在頂端的工具列**執行緒** 視窗中，按一下**資料行**，然後選取或清除您想要顯示或隱藏資料行名稱。  
  
### <a name="to-switch-the-active-thread"></a>若要切換使用中執行緒  
  
- 執行下列任一步驟：  
  
    - 按兩下任一執行緒。  
  
    - 以滑鼠右鍵按一下執行緒，然後按一下 **切換至執行緒**。  
  
         黃色箭號會顯示在新的使用中執行緒旁邊。 箭號的灰色外框識別執行進入偵錯工具的執行緒。  
  
## <a name="grouping-and-sorting-threads"></a>群組和排序執行緒  
 當您群組執行緒時，標題會出現在每個群組的表格中。 標題包含群組描述 (例如 [背景工作執行緒] 或 [未標幟的執行緒]) 和樹狀目錄控制項。 每個群組的成員執行緒會出現在群組標題下方。 如果您想要隱藏群組的成員執行緒，則可以使用樹狀目錄控制項來摺疊該群組。  
  
 因為群組的優先順序高於排序，所以您可以依據分類這類項目來群組執行緒，然後依據每個分類內的 ID 來進行排序。  
  
#### <a name="to-sort-threads"></a>若要排序執行緒  
  
1. 在頂端的工具列**執行緒** 視窗中，按一下頂端的任何資料行 按鈕。  
  
     執行緒現在是依據該資料行中的值進行排序。  
  
2. 如果想要反轉排序次序，請再按一下相同按鈕。  
  
     出現在清單頂端的執行緒現在會出現在底端。  
  
#### <a name="to-group-threads"></a>若要群組執行緒  
  
- 在 [**執行緒**] 視窗工具列上按一下**分組**清單，然後按一下您想要為執行緒群組依據的準則。  
  
#### <a name="to-sort-threads-within-groups"></a>若要排序群組內的執行緒  
  
1. 在頂端的工具列**執行緒** 視窗中，按一下**分組**清單，然後按一下您想要為執行緒群組依據的準則。  
  
2. 在 **執行緒** 視窗中，按一下頂端的任何資料行 按鈕。  
  
     執行緒現在是依據該資料行中的值進行排序。  
  
#### <a name="to-expand-or-collapse-all-groups"></a>若要展開或摺疊所有群組  
  
- 在頂端工具列中**執行緒** 視窗中，按一下**展開群組**或是**摺疊群組**。  
  
## <a name="searching-for-specific-threads"></a>搜尋特定執行緒  
 在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 中，您可以搜尋符合所指定字串的執行緒。 當您搜尋中的執行緒**執行緒** 視窗中，此視窗會顯示符合搜尋字串中的任何資料行的所有執行緒。 資訊包括出現在呼叫堆疊中頂端的執行緒位置**位置**資料行。 根據預設，不過，完整的呼叫堆疊是不會搜尋。  
  
#### <a name="to-search-for-specific-threads"></a>若要搜尋特定執行緒  
  
- 在 [執行緒]  視窗頂端的工具列中，移至 [搜尋]  方塊，並：  
  
    - 輸入搜尋字串，然後按 ENTER 鍵。  
  
         \-或-  
  
    - 按一下下拉式清單旁**搜尋**方塊，然後選取從先前的搜尋的搜尋字串。  
  
- (選擇性) 若要將整個呼叫堆疊併入搜尋中，請選取 [搜尋呼叫堆疊]  。  
  
## <a name="freezing-and-thawing-threads"></a>凍結和解除凍結執行緒  
 當您凍結執行緒時，即使有可用的資源，系統還是不會開始執行執行緒。  
  
 原生程式碼，您可以暫停或繼續執行緒，藉由呼叫 Windows 函式`SuspendThread`並`ResumeThread`或 MFC 函式[CWinThread::SuspendThread](https://msdn.microsoft.com/library/57189c7e-fd71-42e5-bc4b-3de7cd373d28)和[cwinthread:: Resumethread](https://msdn.microsoft.com/library/d6f97a2f-5c9f-4ee1-b978-d74938784db5). 如果您呼叫`SuspendThread`或是`ResumeThread`，您將變更*暫停計數*，會出現在**執行緒**視窗。 不過，如果您凍結或解除凍結原生執行緒，則不會變更暫停計數。 在機器碼中，除非將執行緒解除凍結，而且其暫停計數為零，否則無法執行執行緒。  
  
 在 Managed 程式碼中，凍結或解除凍結執行緒並不會變更暫停計數。 在 Managed 程式碼中，已凍結執行緒的暫停計數為 1。 在機器碼中，除非透過 `SuspendThread` 呼叫暫停執行緒，否則已凍結執行緒的暫停計數為 0。  
  
> [!NOTE]
> 當您偵錯機器碼對 Managed 程式碼的呼叫時，Managed 程式碼與呼叫它的機器碼會在相同的實體執行緒中執行。 暫止或凍結原生執行緒，也會凍結 Managed 程式碼。  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>若要凍結或解除凍結執行緒的執行  
  
- 在頂端工具列中**執行緒** 視窗中，按一下**凍結執行緒**或是**解除凍結執行緒**。  
  
     這個動作只會影響 [執行緒]  視窗中所選取的執行緒。  
  
## <a name="displaying-flagged-threads"></a>顯示已標幟的執行緒  
 您可以在 [執行緒]  視窗中以圖示來標記您想要特別注意的執行緒。 如需詳細資訊，請參閱[如何：旗標，並將執行緒取消標幟](../debugger/how-to-flag-and-unflag-threads.md)。 在 [執行緒] 視窗中，您可以選擇顯示所有執行緒或僅顯示加上旗標的執行緒。  
  
#### <a name="to-display-only-flagged-threads"></a>若只要顯示加上旗標的執行緒  
  
- 在左上角選擇旗標按鈕**執行緒**視窗。  
  
## <a name="displaying-thread-call-stacks-and-switching-between-frames"></a>顯示執行緒呼叫堆疊以及切換框架  
 在多執行緒程式中，每個執行緒都會有它自己的呼叫堆疊。 [執行緒]  視窗則提供便利的方式來檢視這些堆疊。  
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>若要檢視執行緒的呼叫堆疊  
  
- 在 [**位置**] 欄中，按一下執行緒位置旁邊的反轉的三角形。  
  
     會展開這個位置，以顯示執行緒的呼叫堆疊。  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>若要檢視或摺疊所有執行緒的呼叫堆疊  
  
- 在頂端的工具列**執行緒** 視窗中，按一下**展開呼叫堆疊**或是**摺疊呼叫堆疊**。  
  
## <a name="see-also"></a>另請參閱  
 [對多執行緒應用程式進行偵錯](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [逐步解說：針對多執行緒應用程式進行偵錯](../debugger/walkthrough-debugging-a-multithreaded-application.md)
