---
title: 平行執行緒中的變數上設定監看式 |Microsoft 文件
ms.custom: ''
ms.date: 04/25/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 570f77cddede91a81dc15200ebcf02b27f1a4f2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio"></a>在 Visual Studio 中的平行執行緒中的變數上設定監看式
在 [平行監看式] 視窗中，您可以同時在多個執行緒上顯示某個運算式保存的值。 每一列代表應用程式中執行的一個執行緒，不過一個執行緒可能在多列上表示。 更精確的說，每一列代表一個函式呼叫，該函式呼叫的簽章與目前堆疊框架上的函式相符。 您可以將資料行中的項目排序、重新排列、移除和設為群組。 您可以將執行緒加上旗標、取消旗標、凍結 (暫止) 和解除凍結 (繼續)。 下列各欄會顯示在**平行監看式**視窗：  
  
-   旗標資料行，您可以在該資料行中標示想要特別注意的執行緒。  
  
-   目前的執行緒資料行，其中黃色箭號表示目前的執行緒 （尾端彎曲的綠色箭號表示非目前執行緒的目前偵錯工具內容）。  
  
-   可以顯示電腦、處理序、Tile、工作和執行緒的可設定資料行。  
  
    > [!TIP]
    >  Dislay 工作資訊中**平行監看式**視窗中，您必須先開啟**工作**視窗。  
  
-   空白*加入監看式*資料行，您可以在其中輸入要監看的運算式。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>若要顯示 [平行監看式] 視窗  
  
1.  在程式碼中設定中斷點。  
  
2.  在功能表列上，選擇 [偵錯]、[開始偵錯]。 等候應用程式到達中斷點。  
  
3.  在功能表列上選擇 **偵錯**， **Windows**，**平行監看式**，然後選擇 監看式視窗。 您最多可以開啟四個視窗。  
  
### <a name="to-add-a-watch-expression"></a>若要加入監看運算式  
  
-   選取其中一個空白*加入監看式*資料行，然後輸入 監看式運算式。  
  
### <a name="to-flag-or-unflag-a-thread"></a>若要將執行緒加上旗標或取消旗標  
  
-   選取資料列的旗標資料行 （第一個資料行），或開啟執行緒的捷徑功能表並選擇 **旗標**或**取消旗標**。  
  
### <a name="to-display-only-flagged-threads"></a>若只要顯示加上旗標的執行緒  
  
-   選擇**僅顯示已標幟**左上角的按鈕**平行監看式**視窗。  
  
### <a name="to-switch-to-another-thread"></a>若要切換至另一個執行緒  
  
-   按兩下目前的執行緒資料行 （第二個資料行）。 (鍵盤：選取資料列並按 Enter)。  
  
### <a name="to-sort-a-column"></a>若要排序資料行  
  
-   選取資料行標題。  
  
### <a name="to-group-threads"></a>若要群組執行緒  
  
-   開啟 平行監看式 視窗的捷徑功能表，選擇  **Group By**，然後選擇適當的子功能表項目。  
  
### <a name="to-freeze-or-thaw-threads"></a>若要凍結或解除凍結執行緒  
  
-   開啟資料列的捷徑功能表並選擇 **凍結**或**解除凍結**。  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>若要匯出 [平行監看式] 視窗中的資料  
  
-   選擇**在 Excel 中開啟**按鈕，然後選擇**在 Excel 中開啟**或**匯出至 CSV**。  
  
### <a name="to-filter-by-a-boolean-expression"></a>若要依布林運算式篩選  
  
-   輸入布林運算式中的**依布林運算式篩選**方塊。 偵錯工具會針對每個執行緒內容評估運算式。 只有值為 `true` 的列才會顯示。  
  
## <a name="see-also"></a>請參閱  
 [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [如何： 使用 GPU 執行緒視窗](../debugger/how-to-use-the-gpu-threads-window.md)   
 [逐步解說：偵錯 C++ AMP 應用程式](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)