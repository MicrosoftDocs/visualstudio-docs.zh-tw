---
title: 在偵錯工具中使用傾印檔案 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/05/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db6d4e8bc5b2f09194e03bbadc8f49b773d24f1e
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386949"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>在 Visual Studio 偵錯工具中傾印檔案

<a name="BKMK_What_is_a_dump_file_"></a>傾印*檔案是一個*快照，會顯示正在執行的進程，以及在某個時間點針對應用程式載入的模組。 含有堆積資訊的傾印也包含應用程式在該時間點的記憶體快照。

在 Visual Studio 中開啟含有堆積的傾印檔案，類似于在 debug 會話的中斷點停止。 雖然您無法繼續執行，但您可以在傾印時檢查應用程式的堆疊、執行緒和變數值。

傾印主要是用來從開發人員無法存取的電腦上偵測問題。 當您無法在自己的電腦上重現損毀或無回應的程式時，可以使用客戶電腦的傾印檔案。 測試人員也會建立傾印來儲存損毀或無回應的程式資料，以用於進行更多測試。

Visual Studio 偵錯工具可以儲存 Managed 程式碼或機器碼的傾印檔案。 它可以將 Visual Studio 或其他應用程式所建立的傾印檔案，以*小型*傾印格式儲存檔案。

## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a> 需求和限制

- 若要從64位電腦進行檔案的檔案調試，Visual Studio 必須在64位的電腦上執行。

- Visual Studio 可以對來自 ARM 裝置的原生應用程式傾印檔案進行偵錯。 它也可以從 ARM 裝置（但僅在原生偵錯工具中），對受管理應用程式的傾印進行 debug。

- 若要在 Visual Studio 中偵測[核心模式](/windows-hardware/drivers/debugger/kernel-mode-dump-files)傾印檔案或使用[SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension)的偵錯工具延伸模組，請在[WINDOWS 驅動程式套件（WDK）](/windows-hardware/drivers/download-the-wdk)中下載適用于 windows 的偵錯工具。

- Visual Studio 無法以較舊的[完整使用者模式](/windows/desktop/wer/collecting-user-mode-dumps)傾印格式來偵測儲存的傾印檔案。 完整的使用者模式傾印與具有堆積的傾印不同。

- 對最佳化程式碼的傾印檔案進行偵錯可能會造成混淆。 例如，編譯器內嵌函式會造成未預期的呼叫堆疊，而其他最佳化可能會變更變數的存留期。

## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a> 包含或不含堆積的傾印檔案

傾印檔案不一定有堆積資訊。

- **使用**堆積傾印檔案包含應用程式記憶體的快照，包括變數在傾印時的值。 Visual Studio 也會將載入的原生模組二進位檔儲存在含有堆積的傾印檔案中，這可讓您更輕鬆地進行調試。 Visual Studio 可以從含有堆積的傾印檔案載入符號，即使找不到應用程式二進位檔也一樣。

- **不含**堆積的傾印檔案比使用堆積的傾印小很多，但偵錯工具必須載入應用程式二進位檔以尋找符號資訊。 載入的二進位檔必須完全符合在傾印建立期間執行的二進位檔。 不含堆積的傾印檔案只會儲存堆疊變數的值。

## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a> 建立傾印檔案

當您在 Visual Studio 中進行進程的偵錯工具時，可以在偵錯工具于例外狀況或中斷點停止時儲存傾印。

啟用[即時](../debugger/just-in-time-debugging-in-visual-studio.md)偵測之後，您可以將 Visual Studio 偵錯工具附加至 Visual Studio 以外的損毀進程，然後從偵錯工具儲存傾印檔案。 請參閱[附加至正在](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)執行的進程。

**儲存傾印檔案：**

1. 在偵測期間，當錯誤或中斷點停止時，**請選取 [**  >  **將另存**傾印為]。

1. 在 [**另存**傾印] 對話方塊的 [**存檔類型**] 底下，選取 [**使用堆積**的**小型**傾印或小型傾印（預設值）]。

1. 流覽至路徑並選取傾印檔案的名稱，然後選取 [**儲存**]。

>[!NOTE]
>您可以使用支援 Windows 小型傾印格式的任何程式來建立傾印檔案。 例如，[Windows Sysinternals](https://technet.microsoft.com/sysinternals/default) 提供的 **Procdump** 命令列公用程式可以根據觸發程序或視需要建立處理序損毀傾印檔案。 如需使用其他工具建立傾印檔案的相關資訊，請參閱[需求和限制](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations)。

## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a> 開啟傾印檔案

1. 在 Visual Studio 中，**選取 [** 檔案] [開啟檔案]  >  **Open**  >  ** **。

1. 在 [開啟檔案]**** 對話方塊中，找出並選取傾印檔案。 它通常會有*dmp*副檔名。 選取 [確定]。

   [**小型**傾印檔案摘要] 視窗會顯示傾印檔案的摘要和模組資訊，以及您可以採取的動作。

   ![小型傾印摘要頁面](../debugger/media/dbg_dump_summarypage.png "小型傾印摘要頁面")

1. 在 [**動作**] 底下：
   - 若要設定符號載入位置，請選取 [**設定符號路徑**]。
   - 若要開始進行調試，請選取 [**僅限 Managed 的 debug**]、[**僅限原生**的 Debug]、[**混合**式] 或 [**使用 managed 記憶體**進行

## <a name="find-exe-pdb-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a>尋找 .exe、.pdb 和原始檔

若要在傾印檔案上使用完整的調試功能，請 Visual Studio 需求：

- 建立傾印的 *.exe*檔，以及傾印進程所使用的其他二進位檔（dll 等等）。
- *.Exe*和其他二進位檔的符號（*.pdb*）檔。
- 在建立傾印時，與檔案版本完全相符的 *.exe*和 *.pdb*檔案。
- 相關模組的來源檔案。 如果找不到原始檔，您可以使用模組的反組解碼。

如果傾印具有堆積資料，Visual Studio 可以處理某些模組遺漏的二進位檔，但它必須有足夠的模組二進位檔，才能產生有效的呼叫堆疊。

### <a name="search-paths-for-exe-files"></a>.Exe 檔案的搜尋路徑

Visual Studio 會自動在這些位置中搜尋未包含在傾印檔案中的 *.exe*檔案：

1. 包含傾印檔案的資料夾。
2. 傾印檔案指定的模組路徑，這是收集傾印之機器上的模組路徑。
3. [**工具**] （或 [ **Debug**]）中指定的符號路徑 >**選項**] [  >  **調試**  >  **符號**]。 您也可以從 [傾印檔案**摘要**] 視窗的 [**動作**] 窗格開啟 [**符號**] 頁面。 在此頁面上，您可以新增更多位置進行搜尋。

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>使用 [無二進位]、[沒有符號] 或 [找不到來源] 頁面

如果 Visual Studio 找不到在傾印中偵測模組所需的檔案，則會顯示 [**找不到二進位**檔]、[**找不**到任何符號] 或 [**找不到來源**] 頁面。 這些頁面會提供有關此問題原因的詳細資訊，並提供可協助您找出檔案的動作連結。 請參閱[指定符號（.pdb）和原始](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)檔。

## <a name="see-also"></a>另請參閱

- [即時調試](../debugger/just-in-time-debugging-in-visual-studio.md)
- [指定符號（.pdb）和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)