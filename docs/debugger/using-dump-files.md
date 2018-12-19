---
title: 使用傾印檔案偵錯工具 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/05/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e30f9d29ba3c922d70c8acdf7d4db5d8a1670fd
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066950"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>在 Visual Studio 偵錯工具中的傾印檔案

<a name="BKMK_What_is_a_dump_file_"></a> A*傾印檔案*是快照集，其中顯示正在執行的程序和時間點的應用程式已載入的模組。 包含堆積資訊的傾印也在該點包含應用程式的記憶體的快照集。 

開啟 Visual Studio 中的堆積傾印檔案，就像在偵錯工作階段中的中斷點處停止。 雖然您無法繼續執行，您可以在傾印時檢查堆疊、 執行緒和應用程式的變數值。

傾印主要用於偵錯從開發人員沒有存取權的機器的問題。 您無法重現當機，或您自己的電腦上的停止回應時，您可以使用客戶電腦的傾印檔案。 測試人員也會建立傾印來儲存損毀，或用來設定測試的詳細資料的停止回應。 

Visual Studio 偵錯工具可以儲存 Managed 程式碼或機器碼的傾印檔案。 它可以由 Visual Studio 或其他儲存在檔案的應用程式建立的傾印檔案進行偵錯*小型傾印*格式。

##  <a name="BKMK_Requirements_and_limitations"></a> 需求和限制

-   偵錯傾印檔案的 64 位元電腦，您必須執行 Visual Studio，在 64 位元電腦上。

-   Visual Studio 可以對來自 ARM 裝置的原生應用程式傾印檔案進行偵錯。 它也可以偵錯傾印的受管理的應用程式，從 ARM 裝置，但僅限原生偵錯工具。

-   若要偵錯[核心模式](/windows-hardware/drivers/debugger/kernel-mode-dump-files)傾印檔案，或使用[SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension)偵錯在 Visual Studio 中的延伸模組下載中的 Windows 偵錯工具[Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk)。

-   Visual Studio 無法偵錯傾印檔案儲存在較舊[完整使用者模式傾印](/windows/desktop/wer/collecting-user-mode-dumps)格式。 完整的使用者模式傾印不包含堆積的傾印相同。

-   對最佳化程式碼的傾印檔案進行偵錯可能會造成混淆。 例如，編譯器內嵌函式會造成未預期的呼叫堆疊，而其他最佳化可能會變更變數的存留期。

##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> 包含或不含堆積的傾印檔案

傾印檔案可能會或可能沒有堆積資訊。

-   **堆積的傾印檔案**包含應用程式的記憶體，包括變數的值，在傾印時的快照集。 Visual Studio 也會儲存已載入的原生模組二進位的檔可以讓您更容易偵錯堆積的傾印檔案中。 Visual Studio 可以從傾印檔案包含堆積，載入符號，即使找不到應用程式二進位。 

-   **傾印檔案，不含堆積**會遠低於傾印的堆積，但偵錯工具必須載入的應用程式二進位檔，以尋找符號資訊。 載入的二進位檔必須完全符合傾印建立期間執行的項目。 不含堆積的傾印檔案儲存只有堆疊變數的值。

##  <a name="BKMK_Create_a_dump_file"></a> 建立傾印檔案

雖然您正在偵錯在 Visual Studio 中的程序，您可以在偵錯工具停止於例外狀況或中斷點時儲存傾印。 

具有[Just-In-Time 偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)啟用，您還可以將 Visual Studio 偵錯工具附加至 Visual Studio 中，外部的損毀處理序，然後從 偵錯工具中儲存傾印檔案。 請參閱[附加至執行中處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。

**儲存傾印檔案：**

1. 於錯誤或中斷點停止偵錯期間，當選取**偵錯** > **存傾印**。 

1. 在 **存傾印**對話方塊的 **將儲存為類型**，選取**小型傾印**或**包含堆積的小型傾印**（預設值）。

1. 瀏覽路徑並選取傾印檔案的名稱，然後選取**儲存**。 

>[!NOTE]
>您可以使用任何支援 Windows 小型傾印格式的程式，以建立傾印檔案。 例如，[Windows Sysinternals](http://technet.microsoft.com/sysinternals/default) 提供的 **Procdump** 命令列公用程式可以根據觸發程序或視需要建立處理序損毀傾印檔案。 請參閱[需求和限制](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations)如需使用其他工具建立傾印檔案的詳細資訊。

##  <a name="BKMK_Open_a_dump_file"></a> 開啟傾印檔案

1. 在 Visual Studio 中，選取**檔案** > **Open** > **檔案**。

1. 在 [開啟檔案] 對話方塊中，找出並選取傾印檔案。 這類檔案的副檔名通常是 *.dmp*。 選取 [確定]。

   **小型傾印檔案摘要**視窗會顯示摘要和模組的資訊傾印檔案，以及動作可能需要。

   ![小型傾印摘要頁面](../debugger/media/dbg_dump_summarypage.png "小型傾印摘要頁面")

1. 底下**動作**:
   - 若要設定符號載入作業的位置，選取**設定符號路徑**。
   - 若要開始偵錯，請選取**使用 僅限 Managed 偵錯**，**與 僅限原生偵錯**，**混合進行偵錯**，或**偵錯 Managed 記憶體使用**。

##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> 尋找.exe、.pdb 和原始程式檔

若要使用完整偵錯功能在傾印檔案，Visual Studio 需要：

- *.Exe*檔案，建立傾印和其他二進位檔 （Dll 等），傾印處理序使用。
- *.exe* 和其他二進位檔的符號 (*.pdb*) 檔。
- *.Exe*並 *.pdb*完全符合的版本和組建的檔案的檔案傾印建立。
- 相關的模組的原始程式檔。 如果找不到原始程式檔，您可以使用反組譯碼的模組。

傾印包含堆積資料，如果 Visual Studio 可以應付遺漏二進位檔的某些模組，但它必須擁有足夠的模組，才能產生有效的呼叫堆疊的二進位檔。 

### <a name="search-paths-for-exe-files"></a>.Exe 檔案的搜尋路徑

Visual Studio 會自動搜尋這些位置 *.exe*不包含在傾印檔案中的檔案：

1. 包含傾印檔案的資料夾。
2. 模組路徑傾印檔案會指定，這是收集傾印的電腦上的模組路徑。
3. 中指定的符號路徑**工具**(或**偵錯**) >**選項** > **偵錯** >  **符號**。 您也可以開啟**符號**頁面上，從**動作**窗格**傾印檔案摘要**視窗。 在此頁面上，您可以新增多個要搜尋的位置。

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>使用二進位 No、 未載入符號，或 找不到來源頁面

如果 Visual Studio 找不到檔案以便偵錯傾印中的模組，它會顯示**No 二進位找到**，**找不到符號**，或**找不到來源**頁面。 這些頁面提供的問題，原因的詳細的資訊，並提供動作的連結，可協助您找出檔案。 請參閱[指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

## <a name="see-also"></a>另請參閱

- [Just-In-Time 偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)
- [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)