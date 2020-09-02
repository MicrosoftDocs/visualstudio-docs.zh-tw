---
title: 如何：使用執行緒視窗 |Microsoft Docs
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
ms.openlocfilehash: da41524fcb231ea399dbbd2a2904afd935e5c4f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "67824249"
---
# <a name="how-to-use-the-threads-window"></a>如何：使用執行緒視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 [ **執行緒** ] 視窗中，您可以檢查並使用您要進行偵錯工具中的執行緒。  
  
 [ **執行緒** ] 視窗包含一個資料表，其中每個資料列都代表您應用程式中的執行緒。 這份表格預設會列出應用程式中的所有執行緒，但是您可以篩選清單，只顯示您感興趣的執行緒。 每個資料行都會包含不同類型的資訊。 您也可以隱藏部分資料行。 如果您顯示所有資料行，則會從左到右顯示下列資訊：  
  
- 旗標資料行，您可以在其中標示想要特別注意的執行緒。 如需如何旗標執行緒的詳細資訊，請參閱 [如何：旗標和解除標記執行緒](../debugger/how-to-flag-and-unflag-threads.md)。  
  
- 使用中執行緒資料行，其中黃色箭號表示使用中執行緒。 箭號的外框表示執行進入偵錯工具的執行緒。  
  
- **識別碼**資料行，其中包含每個執行緒的識別碼。  
  
- 受管理的 **識別碼** 資料行，其中包含 managed 執行緒的 managed 識別碼。  
  
- **分類**資料行，會將執行緒分類為使用者介面執行緒、遠端程序呼叫處理常式或背景工作執行緒。 特殊分類表示應用程式的主要執行緒。  
  
- **名稱**資料行，依名稱識別每個執行緒（如果有的話），或 \<No Name> 。  
  
- [ **位置** ] 資料行，顯示執行緒執行的位置。 您可以展開這個位置，以顯示執行緒的整個呼叫堆疊。  
  
- **Priority**資料行，其中包含系統指派給每個執行緒的優先順序或優先順序。  
  
- [ **相似性遮罩** ] 資料行，這是通常會隱藏的 advanced 資料行。 這個資料行顯示每個執行緒的處理器關連遮罩。 在多處理器系統中，關連遮罩會決定可以執行執行緒的處理器。  
  
- **擱置的計數**資料行，包含暫停的計數。 這個計數決定是否可以執行執行緒。 如需暫停計數的說明，請參閱本主題後面的＜凍結和解除凍結執行緒＞。  
  
- [ **進程名稱** ] 資料行，其中包含每個執行緒所屬的進程。 當您偵錯多個處理序時，這個資料行十分有用，但它通常是隱藏的。  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>若要在中斷模式或執行模式顯示執行序視窗  
  
- 在 [ **調試** ] 功能表上，指向 [ **視窗**]，然後按一下 [ **執行緒**]。  
  
### <a name="to-display-or-hide-a-column"></a>若要顯示或隱藏資料行  
  
- 在 [ **執行緒** ] 視窗頂端的工具列中，按一下 [資料 **行**]，然後選取或清除您要顯示或隱藏的資料行名稱。  
  
### <a name="to-switch-the-active-thread"></a>若要切換使用中執行緒  
  
- 執行下列任一步驟：  
  
  - 按兩下任一執行緒。  

  - 以滑鼠右鍵按一下執行緒，然後按一下 [ **切換至執行緒**]。  

    黃色箭號會顯示在新的使用中執行緒旁邊。 箭號的灰色外框識別執行進入偵錯工具的執行緒。  
  
## <a name="grouping-and-sorting-threads"></a>群組和排序執行緒  
 當您群組執行緒時，標題會出現在每個群組的表格中。 標題包含群組描述 (例如 [背景工作執行緒] 或 [未標幟的執行緒]) 和樹狀目錄控制項。 每個群組的成員執行緒會出現在群組標題下方。 如果您想要隱藏群組的成員執行緒，則可以使用樹狀目錄控制項來摺疊該群組。  
  
 因為群組的優先順序高於排序，所以您可以依據分類這類項目來群組執行緒，然後依據每個分類內的 ID 來進行排序。  
  
#### <a name="to-sort-threads"></a>若要排序執行緒  
  
1. 在 [ **執行緒** ] 視窗頂端的工具列中，按一下任何資料行頂端的按鈕。  
  
     執行緒現在是依據該資料行中的值進行排序。  
  
2. 如果想要反轉排序次序，請再按一下相同按鈕。  
  
     出現在清單頂端的執行緒現在會出現在底端。  
  
#### <a name="to-group-threads"></a>若要群組執行緒  
  
- 在 [ **執行緒** ] 視窗工具列中，按一下 [ **群組依據** ] 清單，然後按一下您要分組執行緒的準則。  
  
#### <a name="to-sort-threads-within-groups"></a>若要排序群組內的執行緒  
  
1. 在 [ **執行緒** ] 視窗頂端的工具列中，按一下 [ **群組依據** ] 清單，然後按一下您要分組執行緒的準則。  
  
2. 在 [ **執行緒** ] 視窗中，按一下任何資料行頂端的按鈕。  
  
     執行緒現在是依據該資料行中的值進行排序。  
  
#### <a name="to-expand-or-collapse-all-groups"></a>若要展開或摺疊所有群組  
  
- 在 [ **執行緒** ] 視窗頂端的工具列中，按一下 [ **展開群組** ] 或 [折迭 **群組**]。  
  
## <a name="searching-for-specific-threads"></a>搜尋特定執行緒  
 在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 中，您可以搜尋符合所指定字串的執行緒。 當您在 [ **執行緒** ] 視窗中搜尋執行緒時，此視窗會顯示所有符合任何資料行中搜尋字串的執行緒。 該資訊包括出現在 [ **位置** ] 資料行中呼叫堆疊頂端的執行緒位置。 不過，預設不會搜尋整個呼叫堆疊。  
  
#### <a name="to-search-for-specific-threads"></a>若要搜尋特定執行緒  
  
- 在 [執行緒]**** 視窗頂端的工具列中，移至 [搜尋]**** 方塊，並：  
  
  - 輸入搜尋字串，然後按 ENTER 鍵。  

    \- 或 -  

  - 按一下 [ **搜尋** ] 方塊旁邊的下拉式清單，並從先前的搜尋中選取搜尋字串。  
  
- (選擇性) 若要將整個呼叫堆疊併入搜尋中，請選取 [搜尋呼叫堆疊]****。  
  
## <a name="freezing-and-thawing-threads"></a>凍結和解除凍結執行緒  
 當您凍結執行緒時，即使有可用的資源，系統還是不會開始執行執行緒。  
  
 在機器碼中，您可以藉由呼叫 Windows 函式 `SuspendThread` 和 `ResumeThread` 或 MFC 函數 [CWinThread：： SuspendThread](https://msdn.microsoft.com/library/57189c7e-fd71-42e5-bc4b-3de7cd373d28) 和 [CWinThread：： ResumeThread](https://msdn.microsoft.com/library/d6f97a2f-5c9f-4ee1-b978-d74938784db5)來暫停或繼續執行緒。 如果您呼叫 `SuspendThread` 或 `ResumeThread` ，就會變更 [**執行緒**] 視窗中顯示的*暫停計數*。 不過，如果您凍結或解除凍結原生執行緒，則不會變更暫停計數。 在機器碼中，除非將執行緒解除凍結，而且其暫停計數為零，否則無法執行執行緒。  
  
 在 Managed 程式碼中，凍結或解除凍結執行緒並不會變更暫停計數。 在 Managed 程式碼中，已凍結執行緒的暫停計數為 1。 在機器碼中，除非透過 `SuspendThread` 呼叫暫停執行緒，否則已凍結執行緒的暫停計數為 0。  
  
> [!NOTE]
> 當您偵錯機器碼對 Managed 程式碼的呼叫時，Managed 程式碼與呼叫它的機器碼會在相同的實體執行緒中執行。 暫止或凍結原生執行緒，也會凍結 Managed 程式碼。  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>若要凍結或解除凍結執行緒的執行  
  
- 在 [ **執行緒** ] 視窗頂端的工具列中，按一下 [ **凍結執行緒** ] 或 [ **解除凍結執行緒**]。  
  
     這個動作只會影響 [執行緒]**** 視窗中所選取的執行緒。  
  
## <a name="displaying-flagged-threads"></a>顯示已標幟的執行緒  
 您可以在 [執行緒]**** 視窗中以圖示來標記您想要特別注意的執行緒。 如需詳細資訊，請參閱 [如何：旗標和解除標記執行緒](../debugger/how-to-flag-and-unflag-threads.md)。 在 [執行緒] 視窗中，您可以選擇顯示所有執行緒或僅顯示加上旗標的執行緒。  
  
#### <a name="to-display-only-flagged-threads"></a>若只要顯示加上旗標的執行緒  
  
- 選擇 [ **執行緒** ] 視窗左上角的 [旗標] 按鈕。  
  
## <a name="displaying-thread-call-stacks-and-switching-between-frames"></a>顯示執行緒呼叫堆疊以及切換框架  
 在多執行緒程式中，每個執行緒都會有它自己的呼叫堆疊。 [執行緒]**** 視窗則提供便利的方式來檢視這些堆疊。  
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>若要檢視執行緒的呼叫堆疊  
  
- 在 [ **位置** ] 資料行中，按一下執行緒位置旁的反三角形。  
  
     會展開這個位置，以顯示執行緒的呼叫堆疊。  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>若要檢視或摺疊所有執行緒的呼叫堆疊  
  
- 在 [ **執行緒** ] 視窗頂端的工具列中，按一下 [ **展開呼叫堆疊** ] 或 [折迭 **呼叫堆疊**]。  
  
## <a name="see-also"></a>另請參閱  
 [Debug 多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [逐步解說：偵錯多執行緒應用程式](../debugger/walkthrough-debugging-a-multithreaded-application.md)
