---
title: 如何：使用平行監看式視窗 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 734a55cb06ee46afc6fc3518d6dffe349690d3d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697498"
---
# <a name="how-to-use-the-parallel-watch-window"></a>如何：使用平行監看式視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 [平行監看式] 視窗中，您可以同時在多個執行緒上顯示某個運算式保存的值。 每一列代表應用程式中執行的一個執行緒，不過一個執行緒可能在多列上表示。 更精確的說，每一列代表一個函式呼叫，該函式呼叫的簽章與目前堆疊框架上的函式相符。 您可以將資料行中的項目排序、重新排列、移除和設為群組。 您可以將執行緒加上旗標、取消旗標、凍結 (暫止) 和解除凍結 (繼續)。 下列資料行會在 [平行監看式]**** 視窗中顯示：  
  
- 旗標資料行，您可以在該資料行中標示想要特別注意的執行緒。  
  
- 框架資料行，其中的箭號表示選取的框架。  
  
- 可以顯示電腦、處理序、Tile、工作和執行緒的可設定資料行。  
  
  > [!TIP]
  > 您必須開啟 [ **平行** 工作] 視窗，才能在 [ **平行監看** 式] 視窗中顯示工作資訊。  
  
- 資料 **\<Add Watch>** 行，您可以在其中輸入要監看的運算式。  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>若要顯示 [平行監看式] 視窗  
  
1. 在程式碼中設定中斷點。  
  
2. 在功能表列上，選擇 [偵錯]****、[開始偵錯]****。 等候應用程式到達中斷點。  
  
3. 在功能表列上依序選擇 [偵錯]****、[視窗]****、[平行監看式]****，然後選擇監看式視窗。 您最多可以開啟四個視窗。  
  
### <a name="to-add-a-watch-expression"></a>若要加入監看運算式  
  
- 選取 **\<Add Watch>** 並指定監看式運算式。  
  
### <a name="to-flag-or-unflag-a-thread"></a>若要將執行緒加上旗標或取消旗標  
  
- 選取資料列的旗標資料行，或開啟執行緒的快捷方式功能表，然後選擇 [ **旗** 標] 或 [取消 **標記**]。  
  
### <a name="to-display-only-flagged-threads"></a>若只要顯示加上旗標的執行緒  
  
- 在 [ **平行監看** 式] 視窗的左上角，選擇 [只顯示已標記旗標] 按鈕。  
  
### <a name="to-switch-frames"></a>若要切換框架  
  
- 按兩下框架資料行  (鍵盤：選取資料列並按 Enter)。  
  
### <a name="to-sort-a-column"></a>若要排序資料行  
  
- 選取資料行標題。  
  
### <a name="to-group-threads"></a>若要群組執行緒  
  
- 開啟 [平行監看式] 視窗的捷徑功能表，選擇 [分組依據]****，然後選擇適當的子功能表項目。  
  
### <a name="to-freeze-or-thaw-threads"></a>若要凍結或解除凍結執行緒  
  
- 開啟該列的捷徑功能表，然後選擇 [凍結]**** 或 [解除凍結]****。  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>若要匯出 [平行監看式] 視窗中的資料  
  
- 選擇 [在 Excel 中開啟]**** 按鈕，然後選擇 [在 Excel 中開啟]**** 或 [匯出至 CSV]****。  
  
### <a name="to-filter-by-a-boolean-expression"></a>若要依布林運算式篩選  
  
- 在 [依布林運算式篩選]**** 方塊中輸入布林運算式。 偵錯工具會針對每個執行緒內容評估運算式。 只有值為 `true` 的列才會顯示。  
  
## <a name="see-also"></a>另請參閱  
 [Debug 多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [如何：使用 GPU 執行緒視窗](../debugger/how-to-use-the-gpu-threads-window.md)   
 [逐步解說： C++ AMP 應用程式的偵錯工具](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)
