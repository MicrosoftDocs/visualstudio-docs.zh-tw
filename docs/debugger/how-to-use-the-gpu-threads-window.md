---
title: 檢視 偵錯工具中的 GPU 執行緒 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c99e0e1bf64a6a88778d4bfcf27a796916a0f044
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38800915"
---
# <a name="how-to-use-the-gpu-threads-window"></a>如何：使用 GPU 執行緒視窗
在 [GPU 執行緒] 視窗中，您可以檢查和處理正在偵錯的應用程式中，於 GPU 上執行的執行緒。 如需有關在 GPU 執行的應用程式的詳細資訊，請參閱[c + + AMP 概觀](/cpp/parallel/amp/cpp-amp-overview)。  
  
 [GPU 執行緒] 視窗包含一個資料表，其中每一個資料列代表一組在所有資料行中具有相同值的 GPU 執行緒。 您可以將資料行中的項目排序、重新排列、移除和設為群組。 您可以從 [GPU 執行緒] 視窗將執行緒加上旗標、取消旗標、凍結 (暫止) 和解除凍結 (繼續)。 下列各資料行會在 [GPU 執行緒] 視窗中顯示：  
  
-   旗標資料行，您可以在該資料行中標示想要特別注意的執行緒。  
  
-   目前的執行緒資料行，其中黃色箭號表示目前的執行緒。  
  
-   **執行緒計數**資料行，在相同位置顯示的執行緒數目。  
  
-   **列**資料行，顯示每個執行緒群組所在的程式碼行。  
  
-   **地址**資料行，顯示每個執行緒群組所在的指令位址。 根據預設，這個資料行是隱藏狀態。  
  
-   **位置**資料行，這是在原始程式碼中的位置。  
  
-   **狀態**資料行，顯示執行緒為作用中、 已封鎖、 未啟動或完成。  
  
-   **圖格**資料行，資料列中顯示執行緒的磚索引。  
  
 資料表標頭會出現要顯示的 Tile 和執行緒。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>若要顯示 GPU 執行緒視窗  
  
1.  在 [ **方案總管**] 中，開啟專案的捷徑功能表，然後選擇 [ **屬性**]。  
  
2.  在 **屬性頁**專案中，視窗底下**組態屬性**，選擇**偵錯**。  
  
3.  在 **偵錯工具來啟動**清單中，選取**本機 Windows 偵錯工具**。 在 **偵錯工具類型**清單中，選取**僅限 GPU**。 您必須選擇這個偵錯工具，才能在 GPU 上執行的程式碼中的中斷點中斷。  
  
4.  選擇 [確定]  按鈕。  
  
5.  在 GPU 程式碼中設定中斷點。  
  
6.  在功能表列上，選擇 [偵錯]、[開始偵錯]。 等候應用程式到達中斷點。  
  
7.  功能表列上，選擇**偵錯**， **Windows**， **GPU 執行緒**。  
  
### <a name="to-switch-to-a-different-thread"></a>若要切換至不同的執行緒  
  
-   按兩下資料行  (鍵盤：選取資料列並選擇 Enter)。  
  
### <a name="to-display-a-particular-tile-and-thread"></a>若要顯示特定 Tile 和執行緒  
  
1.  選擇**展開執行緒切換器**[GPU 執行緒] 視窗中的按鈕。  
  
2.  在文字方塊中輸入 Tile 和執行緒值。  
  
3.  選擇上面有箭號的按鈕。  
  
### <a name="to-display-or-hide-a-column"></a>若要顯示或隱藏資料行  
  
-   開啟 GPU 執行緒 視窗的捷徑功能表，選擇 **資料行**，然後選擇您想要顯示或隱藏的資料行。  
  
### <a name="to-sort-by-a-column"></a>若要依資料行排序  
  
-   選取資料行標題。  
  
### <a name="to-group-threads"></a>若要群組執行緒  
  
-   開啟 GPU 執行緒 視窗的捷徑功能表，選擇  **Group By**，然後選擇其中一個顯示的資料行名稱。 選擇**無**取消執行緒群組。  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>若要凍結或解除凍結一列執行緒  
  
-   開啟資料列的捷徑功能表，然後選擇**凍結**或是**解除凍結**。  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>若要將一列執行緒加上旗標或取消旗標  
  
-   選取執行緒的旗標資料行或開啟執行緒的捷徑功能表並選擇 **旗標**或是**取消旗標**。  
  
### <a name="to-display-only-flagged-threads"></a>若只要顯示加上旗標的執行緒  
  
-   在 [GPU 執行緒] 視窗中選擇旗標按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [如何： 使用平行監看式視窗](../debugger/how-to-use-the-parallel-watch-window.md)   
 [逐步解說：偵錯 C++ AMP 應用程式](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)