---
title: 調試多個進程 |微軟文檔
ms.date: 11/20/2018
ms.topic: conceptual
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
ms.openlocfilehash: 160e219b6fc2ab314f8d0dd91043c18101f2c3a5
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302221"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>調試多個進程（C#、視覺化基礎、C++）

Visual Studio 可以調試具有多個進程的解決方案。 您可以在進程之間啟動和切換、中斷、繼續和逐步完成源、停止調試以及結束或分離各個進程。

## <a name="start-debugging-with-multiple-processes"></a>使用多個進程開始調試

當 Visual Studio 解決方案中的多個專案可以獨立運行時，您可以選擇啟動調試器的專案。 當前啟動專案在**解決方案資源管理器**中以粗體顯示。

要更改啟動專案，請在**解決方案資源管理器**中，按右鍵其他專案，然後選擇"**設置為啟動專案**"。

要從**解決方案資源管理器**開始調試專案而不使其成為啟動專案，請按右鍵專案並選擇 **"調試** > **啟動"新實例**或 **"跨入新實例**"。

**要從解決方案屬性設置啟動專案或多個專案，可以使用以下功能：**

1. 在 **"解決方案資源管理器"** 中選擇解決方案，然後選擇工具列中的 **"屬性"** 圖示，或按右鍵解決方案並選擇 **"屬性**"。

1. 在 **"屬性"** 頁上，**選擇"常見屬性** > **啟動專案**"。

   ![變更專案的啟動類型](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. 選擇 **"當前選擇**"、**單個啟動專案和**專案檔案或**多個啟動專案**。

   如果選擇**多個啟動專案**，則可以更改每個專案的啟動順序和操作：**啟動**、**不調試啟動**或**無**。

1. 選擇 **"應用**"**或"確定**"以應用並關閉對話方塊。

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> 附加至處理序

調試器還可以*附加到*在 Visual Studio 外部的進程中運行的應用，包括在遠端設備上。 附加到應用後，可以使用視覺化工作室調試器。 調試功能可能受到限制。 這取決於應用是否使用調試資訊構建，您是否有權訪問應用的原始程式碼，以及 JIT 編譯器是否跟蹤調試資訊。

有關詳細資訊，請參閱[附加到正在運行的進程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。

**附加至執行中的處理序：**

1. 應用運行時，選擇**調試** > **附加到進程**。

   ![附加到進程對話方塊](../debugger/media/dbg_attachtoprocessdlg.png "[附加至處理序] 對話方塊")

1. 在"**附加到進程"** 對話方塊中，從 **"可用進程"** 清單中選擇"進程"，然後選擇"**附加**"。

>[!NOTE]
>偵錯工具不會自動附加至所偵錯處理序啟動的子處理序 (即使子專案位於相同方案中)。 要調試子進程，請先在子進程啟動後附加到子進程，或者將 Windows 登錄編輯程式配置為在新的調試器實例中啟動子進程。

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>使用登錄編輯程式在調試器中自動啟動進程

有時，您可能需要調試由另一個進程啟動的應用的啟動代碼。 這類範例包括了服務和自訂安裝動作。 您可以啟動調試器並自動附加到應用。

1. 通過運行*regedit.exe*啟動 Windows 登錄編輯程式。

1. 在登錄編輯程式中，導航到**HKEY_LOCAL_MACHINE_軟體\微軟\Windows NT_當前版本_影像檔執行選項**。

1. 選取要在偵錯工具中啟動之應用程式的資料夾。

   如果應用未列為子資料夾，則按右鍵 **"影像檔執行選項**"，選擇 **"新建** > **鍵**"並鍵入應用名稱。 或者，按右鍵樹中的新鍵，選擇 **"重命名**"，然後輸入應用名稱。

1. 按右鍵樹中的新鍵並選擇 **"新** > **字串值**"。

1. 將新值的名稱從 **"新值"#1**更改為`debugger`。

1. 按右鍵**調試器**並選擇 **"修改**"。

   ![[編輯字串] 對話方塊](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "[編輯字串] 對話方塊")

1. 在 **"編輯字串"** 對話方塊中，`vsjitdebugger.exe`在 **"值資料**"框中鍵入，然後選擇 **"確定**"。

   ![regedit.exe 中的自動偵錯工具起始項目](../debugger/media/dbg_execution_automaticstart_result.png "regedit.exe 中的自動偵錯工具起始項目")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>使用多個進程進行調試
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

使用多個進程調試應用時，中斷、步進和繼續調試器命令預設會影響所有進程。 例如，當進程在中斷點掛起時，所有其他進程的執行也會掛起。 您可以變更這項預設行為，以便更充分掌控執行命令的目標。

**要更改在一個進程中斷時是否暫停所有進程：**

- 在 **"工具**（或**調試**）>**選項** > **調試** > **一般**"下，選擇或清除 **"一個進程中斷時的所有進程**"核取方塊。

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> 中斷、逐步執行和繼續命令

下表描述了選擇或取消選擇**一個進程中斷時"中斷所有進程"時**調試命令的行為核取方塊：

|**命令**|已選取|已取消選取|
|-|-|-|
|**調試**  > **中斷全部**|所有處理序都會中斷。|所有處理序都會中斷。|
|**調試** > **繼續**|所有處理序都會繼續執行。|所有暫止的處理序都會繼續執行。|
|**調試** > **步驟到**、**單一步驟**或**退出**|當目前處理序逐步執行時，所有處理序仍會執行。 <br />然後所有處理序都會中斷。|目前處理序會逐步執行。 <br />暫止的處理序會繼續執行。 <br />執行中的處理序會繼續執行。|
|**調試** > **步驟到當前流程**、**在當前流程上的步驟**或**退出當前流程**|N/A|目前處理序會逐步執行。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|
|源視窗**中斷點**|所有處理序都會中斷。|只要來源視窗處理序會中斷。|
|源視窗 **"運行到游標"**<br />來源視窗必須在目前處理序中。|當來源視窗處理序執行至游標處然後中斷時，所有處理序仍會執行。<br />然後所有其他處理序都會中斷。|來源視窗處理序會執行至游標處。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|
|**處理**視窗>**中斷過程**|N/A|選取的處理序會中斷。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|
|**進程**視窗>**繼續進程**|N/A|選取的處理序會繼續執行。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> 尋找來來源和符號 (.pdb) 檔案
要導航進程的原始程式碼，調試器需要訪問其原始檔案和符號檔。 有關詳細資訊，請參閱[指定符號 （.pdb） 和原始檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

如果無法訪問進程的檔，則可以使用 **"拆解"** 視窗進行導航。 有關詳細資訊，請參閱[如何：使用"拆解"視窗](../debugger/how-to-use-the-disassembly-window.md)。

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> 在處理序之間切換

調試時可以附加到多個進程，但在任何給定時間調試器中只有一個進程處於活動狀態。 您可以在 [偵錯位置]**** 工具列或 [處理序]**** 視窗中設定使用中或「目前的」** 處理序。 若要在處理序之間切換，兩個處理序必須處於中斷模式。

**要從"調試位置"工具列設置當前進程，可以執行以下設置：**

1. 要打開 **"調試位置**"工具列，請選擇 **"查看** > **工具列** > **調試位置**"。

1. 在調試期間，在 **"調試位置**"工具列上，從 **"進程**"下拉清單中選擇要設置為當前進程的進程。

   ![在進程之間切換](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**要從"進程"視窗設置當前進程，**

1. 要打開**進程**視窗，請在調試時選擇 **"調試** > **Windows** > **進程**"。

1. 在 **"進程"** 視窗中，當前進程用黃色箭頭標記。 按兩下要設置為當前進程的進程。

   ![進程視窗](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

切換到進程將其設置為當前進程以進行調試。 調試器視窗顯示當前進程的狀態，步進命令僅影響當前進程。

## <a name="stop-debugging-with-multiple-processes"></a>停止使用多個進程進行調試

預設情況下，當您選擇**調試** > **停止調試**時，調試器將結束或從所有進程分離。

- 如果在調試器中啟動當前進程，則該過程將結束。

- 如果您將偵錯工具附加至目前的處理序，則偵錯工具會與處理序中斷連結，並讓處理序繼續執行。

如果從 Visual Studio 解決方案開始調試進程，然後附加到已運行的另一個進程，然後選擇 **"停止調試**"，調試會話結束。 在 Visual Studio 中啟動的進程結束，而附加到的進程將繼續運行。

要控制**停止調試**對單個進程的影響，請在 **"進程"** 視窗中按右鍵進程，然後在**調試停止時選擇或清除"分離"** 核取方塊。

>[!NOTE]
>**當一個進程中斷調試器選項時中斷所有進程**不會影響停止、終止或從進程分離。

### <a name="stop-terminate-and-detach-commands"></a>停止、結束及中斷連結命令

下表描述了調試器停止、終止和分離具有多個進程的命令的行為：

|**命令**|**描述**|
|-|-|
|**調試** > **停止調試**|除非在 **"進程"** 視窗中更改行為，否則調試器啟動的進程將結束，並分離附加的進程。|
|**調試** > **終止所有**|所有進程都結束了。|
|**調試** > **分離全部**|偵錯工具會從所有處理序中斷連結。|
|**處理**視窗>**分離過程**|偵錯工具會從選取的處理序中斷連結。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|
|**進程**視窗>**終止進程**|所選進程將結束。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|
|**調試停止時****處理**視窗>分離|如果選中，**調試** > **停止調試**將從所選進程分離。 <br />如果未選中，**調試** > **停止調試**將結束所選進程。 |

## <a name="see-also"></a>另請參閱

- [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [附加到執行中的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [使用調試器導航代碼](../debugger/navigating-through-code-with-the-debugger.md)
- [及時調試](../debugger/just-in-time-debugging-in-visual-studio.md)
- [調試多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)