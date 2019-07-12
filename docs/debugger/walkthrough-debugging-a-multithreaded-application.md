---
title: 在 偵錯工具中檢視的往來文章 |Microsoft Docs
ms.date: 10/29/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f65bd7a904f30f132f654b6dd718532d9d0e66e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821581"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window-c-visual-basic-c"></a>在 Visual Studio 偵錯工具中檢視往來文章，使用 [執行緒] 視窗 (C#，Visual Basic 中， C++)
在 [**執行緒**] 視窗中，您可以檢查及使用您要偵錯應用程式中的執行緒。 如需如何使用的逐步指引**執行緒** 視窗中，請參閱[逐步解說：使用 [執行緒] 視窗進行偵錯](../debugger/how-to-use-the-threads-window.md)。

## <a name="use-the-threads-window"></a>使用執行緒視窗
 **執行緒**視窗包含的資料表，其中每個資料列描述您的應用程式中的個別執行緒。 這份表格預設會列出應用程式中的所有執行緒，但是您可以篩選清單，只顯示您感興趣的執行緒。 每個資料行描述不同類型的資訊。 您也可以隱藏部分資料行。 如果您顯示所有資料行時，下列資料行出現，請從左到右：

- **旗標**:在此未標記的專欄中，您可以將標記您要特別注意的執行緒。 如需如何在執行緒的旗標的資訊，請參閱[How to:旗標，並將執行緒取消標幟](../debugger/how-to-flag-and-unflag-threads.md)。

- **目前的執行緒**:此未加上標籤的資料行中的黃色箭號表示目前的執行緒。 箭號外框表示非目前執行緒的目前偵錯工具內容。

- **識別碼**:顯示每個執行緒的識別碼。

- **受管理識別碼**:會顯示 managed 執行緒的 managed 的識別碼。

- **類別目錄**:為使用者介面執行緒、 遠端程序呼叫處理常式或背景工作執行緒顯示執行緒的類別。 特殊分類表示應用程式的主要執行緒。

- **名稱**:依名稱識別每個執行緒，如果有的話，或為\<無名稱 >。

- **位置**：顯示執行緒正在執行。 您可以展開這個位置，以顯示執行緒的整個呼叫堆疊。

- **優先順序**:（預設為隱藏） 的進階資料行，顯示 優先順序 或 系統指派給每個執行緒的優先順序。

- **Affinity Mask**:（預設為隱藏） 的進階資料行，其會顯示每個執行緒的處理器親和性遮罩。 在多處理器系統中，關連遮罩會決定可以執行執行緒的處理器。

- **暫停計數**:進階 （預設為隱藏） 顯示之資料行暫停的計數。 這個計數決定是否可以執行執行緒。 如需暫停計數的詳細資訊，請參閱[凍結和解除凍結執行緒](#freeze-and-thaw-threads)。

- **處理序名稱**:（預設為隱藏） 的進階資料行，會顯示每個執行緒所屬的程序。 當您偵錯的許多程序，此資料行中的資料可以是很有用。

- **處理序識別碼**:（預設為隱藏） 的進階資料行，會顯示每個執行緒所屬的處理序識別碼。

- **傳輸限定詞**:進階資料行 （預設為隱藏） 可唯一識別偵錯工具所連線的電腦。

### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>若要在中斷模式或執行模式顯示執行序視窗

- 當 Visual Studio 處於偵錯模式中時，選取**偵錯**功能表上，指向**Windows**，然後選取**執行緒**。

### <a name="to-display-or-hide-a-column"></a>若要顯示或隱藏資料行

- 在頂端的工具列**執行緒**視窗中，選取**資料行**。 然後，選取或清除您想要顯示或隱藏資料行名稱。

## <a name="display-flagged-threads"></a>顯示已標幟的執行緒
 您可以在 [執行緒]  視窗中以圖示來標記您想要特別注意的執行緒。 如需詳細資訊，請參閱[如何：將執行緒加上旗標和取消旗標](../debugger/how-to-flag-and-unflag-threads.md) 在 [執行緒]  視窗中，您可以選擇顯示所有執行緒或僅顯示加上旗標的執行緒。

### <a name="to-display-only-flagged-threads"></a>若只要顯示加上旗標的執行緒

- 選擇**僅顯示已標幟執行緒**頂端的工具列中**執行緒**視窗。 （如果它灰色，您必須先加上旗標某些執行緒。）

## <a name="freeze-and-thaw-threads"></a>凍結和解除凍結執行緒
 當您凍結執行緒時，系統將不會啟動執行緒的執行，即使資源可供使用。

 原生程式碼，您可以暫停或繼續執行緒，藉由呼叫 Windows 函式`SuspendThread`和`ResumeThread`。 或者，您也可以呼叫 MFC 的函式[CWinThread::SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread)並[cwinthread:: Resumethread](/cpp/mfc/reference/CWinThread-class#resumethread)。 如果您呼叫`SuspendThread`或是`ResumeThread`，則*暫停計數*所示**執行緒**視窗將會變更。 如果您凍結或解除凍結原生執行緒，則不會變更暫停的計數。 執行緒無法執行原生程式碼中，除非它解除凍結，而且具有的暫停的計數為零。

 在 managed 程式碼，暫停的計數會變更您凍結或解除凍結執行緒時。 如果您凍結執行緒在 managed 程式碼時，其暫停的計數為 1。 當您凍結執行緒原生程式碼時，其暫停的計數為 0，除非您使用`SuspendThread`呼叫。

> [!NOTE]
> 當您偵錯機器碼對 Managed 程式碼的呼叫時，Managed 程式碼與呼叫它的機器碼會在相同的實體執行緒中執行。 暫止或凍結原生執行緒，也會凍結 Managed 程式碼。

### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>若要凍結或解除凍結執行緒的執行

- 在頂端的工具列**執行緒**視窗中，選取**凍結執行緒**或是**解除凍結執行緒**。

     這個動作只會影響 [執行緒]  視窗中所選取的執行緒。

### <a name="switch-to-another-thread"></a>切換至另一個執行緒

黃色箭號表示目前的執行緒 （及執行指標的位置）。 具有尾端彎曲的綠色箭號表示非目前執行緒具有目前的偵錯工具內容。

#### <a name="to-switch-to-another-thread"></a>若要切換至另一個執行緒

- 請遵循下列其中一種方式：

  - 按兩下任一執行緒。

  - 以滑鼠右鍵按一下執行緒，然後選取**切換至執行緒**。

## <a name="group-and-sort-threads"></a>群組和排序執行緒
 當您群組執行緒時，標題會出現在每個群組的表格中。 標題包含群組描述 (例如 [背景工作執行緒]  或 [未標幟的執行緒])  和樹狀目錄控制項。 每個群組的成員執行緒會出現在群組標題下方。 如果您想要隱藏群組的成員執行緒，可用於樹狀結構控制項中摺疊群組。

 因為群組的優先順序高於排序，所以您可以依據分類這類項目來群組執行緒，然後依據每個分類內的 ID 來進行排序。

### <a name="to-sort-threads"></a>若要排序執行緒

1. 在頂端的工具列**執行緒** 視窗中，選取任何資料行頂端的按鈕。

     執行緒現在是依據該資料行中的值進行排序。

2. 如果您想要反轉排序次序，請再次選取同一個按鈕。

     出現在清單頂端的執行緒現在會出現在底端。

### <a name="to-group-threads"></a>若要群組執行緒

- 在 [**執行緒**] 視窗工具列上，選取**分組**清單，然後選取您想要為執行緒群組依據的準則。

### <a name="to-sort-threads-within-groups"></a>若要排序群組內的執行緒

1. 在頂端的工具列**執行緒**視窗中，選取**分組**清單，然後選取您想要為執行緒群組依據的準則。

2. 在 [**執行緒**] 視窗中，選取任何資料行頂端的按鈕。

     執行緒現在是依據該資料行中的值進行排序。

### <a name="to-expand-or-collapse-all-groups"></a>若要展開或摺疊所有群組

- 在頂端的工具列**執行緒**視窗中，選取**展開群組**或是**摺疊群組**。

## <a name="search-for-specific-threads"></a>搜尋特定執行緒
 您可以搜尋符合指定的字串中的執行緒**執行緒**視窗。 當您搜尋執行緒時，視窗會顯示比對任何資料行中的搜尋字串的所有執行緒。 該資訊包括 [位置]  資料行中出現在呼叫堆疊頂端的執行緒位置。 根據預設，不被搜尋的完整呼叫堆疊。

### <a name="to-search-for-specific-threads"></a>若要搜尋特定執行緒

1. 在 [執行緒]  視窗頂端的工具列中，移至 [搜尋]  方塊，並：

     - 輸入搜尋字串，然後按**Enter**。

     \-或-

     - 選取下拉式清單旁**搜尋**方塊，然後選取從先前的搜尋的搜尋字串。

2. (選擇性) 若要將整個呼叫堆疊併入搜尋中，請選取 [搜尋呼叫堆疊]  。

## <a name="display-thread-call-stacks-and-switch-between-frames"></a>顯示執行緒呼叫堆疊，並在畫面格之間切換
在多執行緒程式中，每個執行緒都會有它自己的呼叫堆疊。 [執行緒]  視窗則提供便利的方式來檢視這些堆疊。

> [!TIP]
> 針對每個執行緒的呼叫堆疊的視覺表示法，使用[平行堆疊](../debugger/get-started-debugging-multithreaded-apps.md)視窗。

### <a name="to-view-the-call-stack-of-a-thread"></a>若要檢視執行緒的呼叫堆疊

- 在 [**位置**] 欄中，選取執行緒位置旁邊的反轉的三角形。

     會展開這個位置，以顯示執行緒的呼叫堆疊。

### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>若要檢視或摺疊所有執行緒的呼叫堆疊

- 在頂端的工具列**執行緒**視窗中，選取**展開呼叫堆疊**或是**摺疊呼叫堆疊**。

## <a name="see-also"></a>另請參閱
- [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [開始對多執行緒應用程式進行偵錯](../debugger/get-started-debugging-multithreaded-apps.md)
