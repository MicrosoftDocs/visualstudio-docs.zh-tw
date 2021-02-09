---
title: " (c + +) 支援的程式碼變更 |Microsoft Docs"
description: 瞭解當您在 Visual Studio 中進行 c + + 專案的偵錯工具時，使用 [編輯後繼續] 功能時，支援的程式碼變更。
ms.custom: SEO-VS-2020
ms.date: 02/18/2020
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C++ language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C++], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: d000d2757321701c2e14427c6bbb4d3e4164d26f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876299"
---
# <a name="supported-code-changes-c"></a>支援的程式碼變更 (C++)
C + + 專案的 [編輯後繼續] 可處理大部分類型的程式碼變更。 不過，有些變更無法在程式執行期間套用。 若要套用這些變更，您必須停止執行，並建置新版的程式碼。

 如需在 Visual Studio 中使用 c + + 的 [編輯後繼續] 的詳細資訊，請參閱[編輯後繼續 (c + +) ](../debugger/edit-and-continue-visual-cpp.md)

## <a name="requirements"></a><a name="BKMK_Requirements"></a> 需求
### <a name="build-settings-project--properties"></a> (專案 > 屬性的組建設定) ：
  1. **C/c + + > 一般 > Debug 資訊格式**：適用于編輯後繼續的程式資料庫 (`/ZI`) 
  2. **C/c + + > 程式碼產生 > 啟用基本重建**：是 (`/Gm`) 
  3. **連結器 > 一般 > 啟用增量連結**：是 (`/INCREMENTAL`) 

     任何不相容的連結器設定 (例如 `/SAFESEH` 或 `/OPT:` ... ) 應該會在組建期間造成警告 _LNK4075_ 。  
     範例： `LINK : warning LNK4075: ignoring '/INCREMENTAL' due to '/OPT:ICF' specification`

### <a name="debugger-settings-debug--options--general"></a>偵錯工具設定 (Debug > 選項 > 一般) ：
  - 啟用原生編輯後繼續

     任何不相容的編譯器或連結器設定都會在 [編輯後繼續] 期間造成錯誤。  
     範例： `Edit and Continue : error  : ‘file.cpp’ in ‘MyApp.exe’ was not compiled with Edit and Continue enabled. Ensure that the file is compiled with the Program Database for Edit and Continue (/ZI) option.`

## <a name="unsupported-changes"></a><a name="BKMK_Unsupported_changes"></a> 不支援的變更
 下列 C/c + + 變更無法在調試會話期間套用。 如果您進行上述其中一項變更，然後嘗試套用程式碼變更，則 [ **輸出** ] 視窗中會出現錯誤或警告訊息。

- 大部分全域或靜態資料的變更。

- 變更從另一部電腦複製而來，而不是在本機上建置的可執行檔。

- 變更會影響物件 (例如，類別的資料成員) 配置的資料類型。

- 加入超過 64K 位元組的新程式碼或資料。

- 在指令指標之前的某一點加入需要建構函式的變數。

- 會影響需要執行階段初始化之程式碼的變更。

- 在某些執行個體中加入例外狀況處理常式。

- 變更資源檔。

- 變更唯讀檔中的程式碼。

- 變更沒有對應之 PDB 檔的程式碼。

- 變更沒有目的檔的程式碼。

* 修改 lambda：
  - 具有靜態或全域成員。
  - 會傳遞至 std：：函數。 這會導致正版 ODR 違規，並導致 C1092。

- [編輯後繼續] 不會更新靜態程式庫。 如果您變更靜態程式庫，執行仍會使用舊版繼續進行，而且不會發出任何警告。

## <a name="unsupported-scenarios"></a><a name="BKMK_Unsupported_scenarios"></a> 不支援的案例
 C/C++ 的 [編輯後繼續] 無法用於下列偵錯案例中：

- 偵錯以 [/Zo (增強最佳化偵錯)](/cpp/build/reference/zo-enhance-optimized-debugging)編譯的原生應用程式

- 在 Visual Studio 2015 Update 1 之前的 Visual Studio 版本中，將 UWP 應用程式或元件的偵錯工具。 從 Visual Studio 2015 Update 1 開始，您可以在 UWP c + + 應用程式和 DirectX 應用程式中使用 [編輯後繼續]，因為它現在支援 `/ZI` 使用參數的編譯器參數  `/bigobj` 。 您也可以搭配以 `/FASTLINK` 參數。

- 偵錯工具 8/8.1 Store 應用程式。 這些專案使用 VC 120 工具組和 C/c + + `/bigobj` 參數。 `/bigobj`只有 VC 140 工具組支援 [編輯後繼續]。

- 在 Windows 98 上偵錯。

- 混合模式 (原生/Managed) 偵錯。

- JavaScript 調試。

- SQL 偵錯

- 對傾印檔偵錯。

- 在未選取 [ **發生未處理的例外狀況時回溯呼叫堆疊** ] 選項的情況下，於發生未處理的例外狀況後編輯程式碼。

- 使用 [附加至]  來進行應用程式偵錯，而不要選擇 [偵錯]  功能表上的 [啟動]  來執行應用程式。

- 偵錯最佳化程式碼

- 由於建置錯誤以致新版本建置失敗之後，對舊版程式碼進行偵錯。

- 使用自訂編譯器 (*cl.exe*) 路徑。 基於安全性理由，在編輯後繼續時，若要重新編譯檔案，Visual Studio 一律會使用已安裝的編譯器。 如果您使用自訂編譯器路徑 (例如，透過檔案中的自訂 `$(ExecutablePath)` 變數 `*.props`) ，會顯示警告，並 Visual Studio 切換回使用相同版本/架構的已安裝編譯器。

- FASTBuild 組建系統。 FASTBuild 目前與「啟用最小量重建 (`/Gm`) 」編譯器參數不相容，因此不支援「編輯後繼續」。

- 舊版架構/VC 工具組。 使用 VC 140 工具組時，預設的偵錯工具支援 X86 和 X64 應用程式的 [編輯後繼續]。 舊版工具組僅支援 X86 應用程式。 VC 120 之前的工具組應使用舊版偵錯工具，方法是核取 _[Debug > Options > 一般 >_ 使用原生相容性模式]，以便使用 [編輯後繼續]。

## <a name="linking-limitations"></a><a name="BKMK_Linking_limitations"></a> 連結的限制

### <a name="linker-options-that-disable-edit-and-continue"></a><a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> 停用 [編輯後繼續] 的連結器選項
 下列連結器選項停用 [編輯後繼續]：

- 設定 **/OPT:REF**、 **/OPT:ICF**，或 **/INCREMENTAL:NO** 會停用 [編輯後繼續]，並且產生下列警告：  
     `LINK : warning LNK4075: ignoring /EDITANDCONTINUE due to /OPT specification`

- 設定 **/order**、 **/RELEASE** 或 **/Force** 會停用 [編輯後繼續]，並出現下列警告：  
     `LINK : warning LNK4075: ignoring /INCREMENTAL due to /option specification`

- 設定任何能夠防止建立程式資料庫 (.PDB) 檔的選項，即可停用 [編輯後繼續] 並且不顯示任何特定警告。

### <a name="auto-relinking-limitations"></a><a name="BKMK_Auto_relinking_limitations"></a> 自動重新連結的限制
 根據預設，[編輯後繼續] 會在偵錯工作階段結束後重新連結程式，建立最新的執行檔。

 如果您不是在原來的組建位置上偵錯，[編輯後繼續] 無法重新連結您的程式。 會有一則訊息告訴您必須手動重建。

 [編輯後繼續] 不重建靜態程式庫。 如果您使用 [編輯後繼續] 來變更靜態程式庫，則必須手動重建程式庫，再用它重新連結應用程式。

 [編輯後繼續] 不會叫用自訂組建步驟。 如果您的程式使用自訂的建置步驟，您應當以手動方式重建，讓自訂的建置步驟能夠被叫用。 在那情況下，您可以在 [編輯後繼續] 之後停用重新連結，確保您會被提示以手動重建。

 **若要在編輯後繼續後停用重新連結**

1. 在 [ **偵錯** ] 功能表上選擇 [ **選項和設定**]。

2. 在 [選項]  對話方塊的 [偵錯]  節點下，選取 [編輯後繼續]  節點。

3. 清除 [ **偵錯後重新連結程式碼變更** ] 核取方塊。

## <a name="precompiled-header-limitations"></a><a name="BKMK_Precompiled_header_limitations"></a> 先行編譯標頭限制
 根據預設，[編輯後繼續] 會在背景載入並處理預先編譯的標頭，以加速程式碼變更的處理。 載入預先編譯的標頭檔須配置實體記憶體，如果您是在一部 RAM 不足的電腦上進行編譯，這可能會是個問題。 您可以在偵錯時，使用 [Windows 工作管理員] 判斷可用的實體記憶體數量，來判斷這樣是否會發生問題。 如果此一數量大於預先編譯的標頭檔的大小，[編輯後繼續] 應該不會有問題。 如果數量小於您先行編譯的標頭大小，您可以防止 [編輯後繼續] 在背景中載入先行編譯的標頭。

 **若要停用編輯後繼續的先行編譯標頭的背景載入**

1. 在 [ **偵錯** ] 功能表上選擇 [ **選項和設定**]。

2. 在 [選項]  對話方塊的 [偵錯]  節點下，選取 [編輯後繼續]  節點。

3. 清除 [ **允許先行編譯** ] 核取方塊。

## <a name="idl-attribute-limitations"></a><a name="BKMK_IDL_attribute_limitations"></a> IDL 屬性限制
 [編輯後繼續] 不會重新產生介面定義 (IDL) 檔， 所以您偵錯時並不會反映出 IDL 屬性的變更。 若要看到 IDL 屬性的變更結果，就必須停止偵錯並重建應用程式。 如果 IDL 屬性有所變更，[編輯後繼續] 並不會產生錯誤或警告。 如需詳細資訊，請參閱 [IDL 屬性](/cpp/windows/idl-attributes)。

## <a name="diagnosing-issues"></a><a name="BKMK_Diagnosing_issues"></a> 診斷問題
 如果您的案例不符合上述任何條件，您可以藉由設定下列 DWORD 登錄值來收集更多詳細資料：
 1. 開啟開發人員命令提示字元。
 2. 執行以下命令：  
     `VsRegEdit.exe set “C:\Program Files (x86)\Microsoft Visual Studio\[Version]\[YOUR EDITION]” HKCU Debugger NativeEncDiagnosticLoggingLevel DWORD 1`

 在 debug 會話開始時設定此值，會導致 [編輯後繼續] 的各種元件 go-spew 詳細資訊記錄到 **輸出視窗** 的 [  >  **調試** 程式] 窗格。

## <a name="see-also"></a>另請參閱
- [編輯後繼續 (C++)](../debugger/edit-and-continue-visual-cpp.md)
