---
title: Debug 多重進程 |Microsoft Docs
description: 在 Visual Studio 中進行多個進程的偵錯工具。 在進程、中斷、繼續、逐步執行來源，以及結束或卸離個別進程之間啟動和切換。
ms.custom: SEO-VS-2020
ms.date: 11/20/2018
ms.topic: how-to
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 214025c2d128443223594fdb00fcf730e5a8091a
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728627"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a> (c #、Visual Basic、c + +) 進行多個進程的偵錯工具

Visual Studio 可以將有數個進程的方案進行 debug 錯。 您可以啟動和切換進程、中斷、繼續和逐步執行來源、停止偵測，以及結束或中斷個別進程的連結。

## <a name="start-debugging-with-multiple-processes"></a>使用多個進程開始偵錯工具

當 Visual Studio 方案中有多個專案可以獨立執行時，您可以選取偵錯工具啟動的專案。 目前的啟始專案會在 **方案總管** 以粗體顯示。

若要變更啟始專案，請在 [ **方案總管** 中，以滑鼠右鍵按一下不同的專案，然後選取 [ **設定為啟始專案**]。

若要從 **方案總管** 開始對專案進行錯錯，而不讓它成為啟始專案，請以滑鼠右鍵按一下專案，然後選取 [ **Debug**  >  **開始新實例**] 或 [**逐步執行新實例**]。

**若要從 [方案屬性] 設定啟始專案或多個專案：**

1. 在 **方案總管** 中選取方案，然後選取工具列中的 [ **屬性** ] 圖示，或以滑鼠右鍵按一下方案，然後選取 [ **屬性**]。

1. 在 [**屬性**] 頁面上，選取 [**通用屬性**  >  **啟始專案**]。

   ![變更專案的啟動類型](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. 選取 **目前選取****專案、單一啟始專案** 和專案檔，或 **多個啟始專案**。

   如果您選取 **多個啟始專案**，可以變更每個專案所要採取的啟動順序和動作： [ **啟動**]、[ **不進行調試** 程式] 或 [ **無**]。

1. 選取[套用]，或選取 **[確定**] 以套用並關閉對話方塊。

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> 附加至處理序

偵錯工具也可以 *附加* 至 Visual Studio 以外的進程（包括遠端裝置）上執行的應用程式。 附加至應用程式之後，您可以使用 Visual Studio 偵錯工具。 調試功能可能會受到限制。 這取決於應用程式是使用偵錯工具所建立，不論您是否有應用程式原始程式碼的存取權，以及 JIT 編譯程式是否正在追蹤偵錯工具資訊。

如需詳細資訊，請參閱 [附加至正在](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)執行的進程。

**附加至執行中的處理序：**

1. 當應用程式執行時，請選取 [ **Debug**  >  **附加至進程**]。

   ![[附加至進程] 對話方塊](../debugger/media/dbg_attachtoprocessdlg.png "[附加至處理序] 對話方塊")

1. 在 [ **附加至進程** ] 對話方塊中，從 [ **可使用的進程** ] 清單中選取處理常式，然後選取 [ **附加**]。

>[!NOTE]
>偵錯工具不會自動附加至所偵錯處理序啟動的子處理序 (即使子專案位於相同方案中)。 若要 debug 子進程，請在啟動後附加至子進程，或設定 Windows 登錄編輯程式在新的偵錯工具實例中啟動子進程。

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> 使用登錄編輯程式在偵錯工具中自動啟動進程

有時，您可能需要針對由另一個進程啟動的應用程式，來進行啟動程式碼的偵錯工具。 這類範例包括了服務和自訂安裝動作。 您可以讓偵錯工具啟動並自動附加至應用程式。

1. 執行 *regedit.exe* 來啟動 Windows 登錄編輯程式。

1. 在 [登錄編輯程式] 中，流覽至 **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options**。

1. 選取要在偵錯工具中啟動之應用程式的資料夾。

   如果應用程式未列為子資料夾，請以滑鼠右鍵按一下 [**影像檔執行選項**]，選取 [**新增**  >  **金鑰**]，然後輸入應用程式名稱。 或者，以滑鼠右鍵按一下樹狀結構中的新機碼、選取 [ **重新命名**]，然後輸入應用程式名稱。

1. 以滑鼠右鍵按一下樹狀結構中的新索引鍵，然後選取 [**新增**  >  **字串值**]。

1. 將新值的名稱從新值 **#1** 變更為 `debugger` 。

1. 以滑鼠右鍵按一下 **[偵錯工具** ]，然後選取 [ **修改**]。

   ![[編輯字串] 對話方塊](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "[編輯字串] 對話方塊")

1. 在 [ **編輯字串** ] 對話方塊的 `vsjitdebugger.exe` [ **值資料** ] 方塊中輸入，然後選取 **[確定]**。

   ![regedit.exe 中的自動偵錯工具起始項目](../debugger/media/dbg_execution_automaticstart_result.png "regedit.exe 中的自動偵錯工具起始項目")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> 使用多個進程進行偵錯工具
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

使用多個進程來對應用程式進行偵錯工具時，[中斷]、[逐步執行] 和 [繼續偵錯工具] 命令預設會影響所有進程 例如，當進程在中斷點暫停時，其他所有進程的執行也會暫止。 您可以變更這項預設行為，以便更充分掌控執行命令的目標。

**若要變更一個進程中斷時是否暫停所有進程：**

- 在 [**工具**] (或 [**調試** 程式]) >**選項** 偵錯工具] 下  >    >  ****，選取或清除 [**當一個進程中斷時中斷所有進程**] 核取方塊。

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> 中斷、逐步執行和繼續命令

下表說明在選取或取消選取 [ **一個進程中斷時中斷所有進程** ] 核取方塊時，偵錯工具的行為：

|**命令**|已選取|已取消選取|
|-|-|-|
|**Debug**   > **全部中斷**|所有處理序都會中斷。|所有處理序都會中斷。|
|**Debug**  > **繼續**|所有處理序都會繼續執行。|所有暫止的處理序都會繼續執行。|
|**Debug**  > **逐步****執行、不** 進入或 **跳出**|當目前處理序逐步執行時，所有處理序仍會執行。 <br />然後所有處理序都會中斷。|目前處理序會逐步執行。 <br />暫止的處理序會繼續執行。 <br />執行中的處理序會繼續執行。|
|**Debug**  > **逐步執行目前** 的程式、不進入 **目前的進程**，或 **跳出目前的進程**|N/A|目前處理序會逐步執行。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|
|來源視窗 **中斷點**|所有處理序都會中斷。|只要來源視窗處理序會中斷。|
|來源視窗 **執行至游標處**<br />來源視窗必須在目前處理序中。|當來源視窗處理序執行至游標處然後中斷時，所有處理序仍會執行。<br />然後所有其他處理序都會中斷。|來源視窗處理序會執行至游標處。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|
|**進程** 視窗 > **中斷進程**|N/A|選取的處理序會中斷。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|
|**進程** 視窗 > **繼續進程**|N/A|選取的處理序會繼續執行。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> 尋找來來源和符號 (.pdb) 檔案
若要流覽進程的原始程式碼，偵錯工具需要存取其原始程式檔和符號檔。 如需詳細資訊，請參閱 [指定符號 ( .pdb) 和原始](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)程式檔。

如果您無法存取進程的檔案，可以使用 [反組 **解碼] 視窗** 進行流覽。 如需詳細資訊，請參閱 [如何：使用](../debugger/how-to-use-the-disassembly-window.md)反組解碼視窗。

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> 在處理序之間切換

當您正在進行偵錯工具時，您可以附加至多個進程，但是在任何指定時間，偵錯工具中只會有一個作用中的進程。 您可以在 [偵錯位置] 工具列或 [處理序] 視窗中設定使用中或「目前的」處理序。 若要在處理序之間切換，兩個處理序必須處於中斷模式。

**若要從 [偵錯工具位置] 工具列設定目前的進程：**

1. 若要開啟 [**調試位置**] 工具列，請選取 [**視圖**  >  **工具列**  >  **調試位置**]。

1. 在偵錯工具期間，在 [ **調試** 程式] 工具列上，從 [ **進程** ] 下拉式清單中選取您想要設定為目前進程的進程。

   ![在進程之間切換](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**若要從 [進程] 視窗設定目前的進程：**

1. 若要開啟 [**進程**] 視窗，請在偵錯工具中選取 [ **Debug**  >  **Windows**  >  **進程**]。

1. 在 [ **進程** ] 視窗中，目前的進程會以黃色箭號標記。 按兩下您想要設定為目前進程的進程。

   ![進程視窗](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

切換至進程會將它設定為目前的偵錯工具來進行偵測。 偵錯工具視窗會顯示目前進程的狀態，而逐步執行命令只會影響目前的進程。

## <a name="stop-debugging-with-multiple-processes"></a>停止多個進程的偵錯工具

依預設，當您選取 [ **Debug**  >  **停止** 錯] 時，偵錯工具會結束或卸離所有進程。

- 如果在偵錯工具中啟動目前的進程，則會結束進程。

- 如果您將偵錯工具附加至目前的處理序，則偵錯工具會與處理序中斷連結，並讓處理序繼續執行。

如果您從 Visual Studio 的方案開始偵錯工具，然後附加至已在執行中的另一個進程，然後選擇 [ **停止調試**]，則偵錯工具會結束。 在 Visual Studio 中啟動的進程會結束，而您附加的進程會繼續執行。

若要控制 **停止調試** 程式影響個別進程的方式，請在 [ **進程** ] 視窗中，以滑鼠右鍵按一下處理常式，然後選取或清除 [ **當偵錯工具停止時** 中斷連結] 核取方塊。

>[!NOTE]
>[ **當某個進程中斷偵錯工具時中斷所有進程** ] 選項不會影響停止、終止或卸離進程。

### <a name="stop-terminate-and-detach-commands"></a>停止、結束及中斷連結命令

下表描述偵錯工具停止、終止和卸離命令與多個進程的行為：

|**命令**|**描述**|
|-|-|
|**Debug**  > **停止調試**|除非在 [ **進程** ] 視窗中變更行為，否則偵錯工具啟動的進程會結束，而且附加的進程也會卸離。|
|**Debug**  > **全部終止**|所有進程都會結束。|
|**Debug**  > **全部卸離**|偵錯工具會從所有處理序中斷連結。|
|**進程** 視窗 > 卸 **離進程**|偵錯工具會從選取的處理序中斷連結。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|
|**進程** 視窗 > **終止進程**|選取的進程已結束。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|
|**停止偵錯工具時**，**進程** 視窗 > 卸離|如果選取此選項，則會  >  從選取的進程 **中斷** 偵錯工具的偵錯工具。 <br />如果未選取此選項， **Debug**  >  **Stop 調試** 程式會結束選取的進程。 |

## <a name="see-also"></a>請參閱

- [指定符號 ( .pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [附加至正在執行的進程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [使用偵錯工具流覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)
- [即時調試](../debugger/just-in-time-debugging-in-visual-studio.md)
- [對多執行緒應用程式進行偵錯](../debugger/debug-multithreaded-applications-in-visual-studio.md)