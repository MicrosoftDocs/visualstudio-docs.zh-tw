---
title: 檢視 偵錯工具中的 GPU 執行緒 |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 1e3124f98855f5f7f303aff0d9e8b2608abbbeba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871313"
---
# <a name="how-to-use-the-gpu-threads-window"></a>HOW TO：使用 GPU 執行緒視窗
在 [GPU 執行緒] 視窗中，您可以檢查和處理正在偵錯的應用程式中，於 GPU 上執行的執行緒。 如需有關在 GPU 執行的應用程式的詳細資訊，請參閱[c + + AMP 概觀](/cpp/parallel/amp/cpp-amp-overview)。  
  
 [GPU 執行緒] 視窗包含一個資料表，其中每一個資料列代表一組在所有資料行中具有相同值的 GPU 執行緒。 您可以將資料行中的項目排序、重新排列、移除和設為群組。 您可以從 [GPU 執行緒] 視窗將執行緒加上旗標、取消旗標、凍結 (暫止) 和解除凍結 (繼續)。 下列各資料行會在 [GPU 執行緒] 視窗中顯示：  
  
- 旗標資料行，您可以在該資料行中標示想要特別注意的執行緒。  
  
- 目前的執行緒資料行，其中黃色箭號表示目前的執行緒。  
  
- [執行緒計數] 一欄顯示同一位置的執行緒數目。  
  
- [行] 一欄顯示每個執行緒群組所在的程式碼行。  
  
- [位址] 一欄顯示每個執行緒群組所在的指令位址。 根據預設，這個資料行是隱藏狀態。  
  
- [位置] 一欄是在原始程式碼中的位置。  
  
- [狀態] 一欄顯示執行緒為使用中、已封鎖、未啟動或完成。  
  
- [磚] 一欄顯示資料列中執行緒的磚索引。  
  
  資料表標頭會出現要顯示的 Tile 和執行緒。  
  
  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>若要顯示 GPU 執行緒視窗  
  
1.  在 [ **方案總管**] 中，開啟專案的捷徑功能表，然後選擇 [ **屬性**]。  
  
2.  在專案的 [屬性頁] 視窗中，選擇 [組態屬性] 中的 [偵錯]。  
  
3.  在 [要啟動的偵錯工具] 清單中，選取 [本機 Windows 偵錯工具]。 在 [偵錯工具類型] 清單中，選取 [僅限 GPU]。 您必須選擇這個偵錯工具，才能在 GPU 上執行的程式碼中的中斷點中斷。  
  
4.  選擇 [確定]  按鈕。  
  
5.  在 GPU 程式碼中設定中斷點。  
  
6.  在功能表列上，選擇 [偵錯]、[開始偵錯]。 等候應用程式到達中斷點。  
  
7.  在功能表列上，選擇 [偵錯]、[視窗]、[GPU 執行緒]。  
  
### <a name="to-switch-to-a-different-thread"></a>若要切換至不同的執行緒  
  
-   按兩下資料行  鍵盤選取資料列，然後選擇 enter 鍵。）  
  
### <a name="to-display-a-particular-tile-and-thread"></a>若要顯示特定 Tile 和執行緒  
  
1.  選擇 [GPU 執行緒] 視窗中的 [展開執行緒切換器] 按鈕。  
  
2.  在文字方塊中輸入 Tile 和執行緒值。  
  
3.  選擇上面有箭號的按鈕。  
  
### <a name="to-display-or-hide-a-column"></a>若要顯示或隱藏資料行  
  
-   開啟 [GPU 執行緒] 視窗的捷徑功能表，選擇 [欄位]，然後選擇要顯示或隱藏的欄位。  
  
### <a name="to-sort-by-a-column"></a>若要依資料行排序  
  
-   選取資料行標題。  
  
### <a name="to-group-threads"></a>若要群組執行緒  
  
-   開啟 [GPU 執行緒] 視窗的捷徑功能表，選擇 [群組依據]，然後選擇其中一個顯示的欄位名稱。 選擇 [無] 則會取消執行緒群組。  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>若要凍結或解除凍結一列執行緒  
  
-   開啟該資料列的捷徑功能表，然後選擇 [凍結] 或 [解除凍結]。  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>若要將一列執行緒加上旗標或取消旗標  
  
-   選取執行緒的旗標欄位，或開啟執行緒的捷徑功能表，並選擇 [加上旗標] 或 [取消旗標]。  
  
### <a name="to-display-only-flagged-threads"></a>若只要顯示加上旗標的執行緒  
  
-   在 [GPU 執行緒] 視窗中選擇旗標按鈕。  
  
## <a name="see-also"></a>請參閱  
 [對多執行緒應用程式進行偵錯](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [如何：使用平行監看式視窗](../debugger/how-to-use-the-parallel-watch-window.md)   
 [逐步解說：偵錯 c + + AMP 應用程式](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)