---
title: 偵錯多個處理序 |Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62853422"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>偵錯多個處理序 (C#，Visual Basic 中， C++)

Visual Studio 可以有數個程序的方案進行偵錯。 您可以啟動和處理序之間切換、 中斷、 繼續，並逐步執行來源、 停止偵錯，和 end 或從個別的處理序中斷連結。

## <a name="start-debugging-with-multiple-processes"></a>使用多個處理序開始偵錯

當 Visual Studio 方案中的多個專案可以獨立執行時，您可以選取 偵錯工具啟動哪個專案。 目前的啟始專案會出現在中以粗體字**方案總管 中**。

若要變更啟始專案，在**方案總管**，以滑鼠右鍵按一下不同的專案，然後選取**設定為啟始專案**。

若要開始偵錯的專案**方案總管**而不讓它成為啟始專案，以滑鼠右鍵按一下專案，然後選取**偵錯** > **開始新執行個體**或是**逐步執行新執行個體**。

**若要從方案內容中設定啟始專案或多個專案：**

1. 選取中的解決方案**方案總管**，然後選取**屬性**工具列上或以滑鼠右鍵按一下方案中的圖示，然後選取**屬性**。

1. 在 **屬性**頁面上，選取**通用屬性** > **啟始專案**。

   ![變更專案的啟動類型](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. 選取 **目前的選取範圍**，**單一啟始專案**和 專案檔中，或**多個啟始專案**。

   如果您選取**多個啟始專案**，您可以變更才會針對每個專案的啟動順序和動作：**開始**，**啟動但不偵錯**，或**None**。

1. 選取 **套用**，或**確定**套用並關閉對話方塊。

### <a name="BKMK_Attach_to_a_process"></a> 附加至處理序

偵錯工具也可以*附加*在 Visual Studio 中，包括在遠端裝置上的外部程序中執行的應用程式。 您將附加至應用程式之後，您可以使用 Visual Studio 偵錯工具。 偵錯功能可能有限。 這取決於是否使用偵錯資訊建置應用程式、 您是否能存取應用程式的原始程式碼，和 JIT 編譯器是否追蹤偵錯資訊。

如需詳細資訊，請參閱 <<c0> [ 附加至執行中處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。

**附加至執行中的處理序：**

1. 在應用程式執行時，選取**偵錯** > **附加至處理序**。

   ![附加至處理序 對話方塊](../debugger/media/dbg_attachtoprocessdlg.png "附加至處理序 對話方塊")

1. 在 **附加至處理序**對話方塊方塊中，選取的程序**可用的處理序**清單，然後再選取**附加**。

>[!NOTE]
>偵錯工具不會自動附加至所偵錯處理序啟動的子處理序 (即使子專案位於相同方案中)。 若要偵錯子處理序，附加至子處理序之後它會啟動，, 或是設定 Windows 登錄編輯程式，以新的偵錯工具執行個體中啟動子處理序。

### <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> 使用登錄編輯程式自動啟動偵錯工具中的 處理序

有時候，您可能需要偵錯啟始程式碼由另一個處理序啟動的應用程式。 這類範例包括了服務和自訂安裝動作。 您可以讓偵錯工具啟動，並會自動附加至應用程式。

1. 開始執行的 Windows 登錄編輯程式*regedit.exe*。

1. 在登錄編輯器中，瀏覽至**HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options**。

1. 選取要在偵錯工具中啟動之應用程式的資料夾。

   如果應用程式未列為子資料夾，以滑鼠右鍵按一下**Image File Execution Options**，選取**新增** > **金鑰**，然後輸入應用程式名稱。 或者，您也可以以滑鼠右鍵按一下樹狀目錄中，選取新的金鑰**重新命名**，然後輸入 應用程式名稱。

1. 以滑鼠右鍵按一下樹狀目錄中選取新的金鑰**的新** > **字串值**。

1. 將新值的名稱變更**新數值 #1**至`debugger`。

1. 以滑鼠右鍵按一下**偵錯工具**，然後選取**修改**。

   ![編輯字串 對話方塊](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "編輯字串 對話方塊")

1. 在 [**編輯字串**] 對話方塊中，輸入`vsjitdebugger.exe`中**數值資料**方塊，然後按 **[確定]**。

   ![自動偵錯工具起始項目在 regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "自動偵錯工具啟動 regedit.exe 中的項目")

## <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> 使用多個處理序進行偵錯
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

偵錯時具有數個程序的應用程式，中斷、 逐步執行，並繼續偵錯工具命令會影響所有處理程序，根據預設。 例如，當處理程序會在中斷點暫止，所有其他處理序的執行也會暫止。 您可以變更這項預設行為，以便更充分掌控執行命令的目標。

**若要變更是否某個處理序中斷時，會暫停所有處理程序：**

- 底下**工具**(或**偵錯**) >**選項** > **偵錯** > **一般**，選取或清除**如果其中一個處理序中斷，就中斷所有處理序**核取方塊。

### <a name="BKMK_Break__step__and_continue_commands"></a> 中斷、逐步執行和繼續命令

下表描述的偵錯行為命令何時**中斷所有處理序，當其中一個處理序中斷**選取或取消選取核取方塊：

|**命令**|已選取|已取消選取|
|-|-|-|
|**偵錯**  > **全部中斷**|所有處理序都會中斷。|所有處理序都會中斷。|
|**偵錯** > **繼續**|所有處理序都會繼續執行。|所有暫止的處理序都會繼續執行。|
|**偵錯** > **進入**，**不進入函式**，或**跳離函式**|當目前處理序逐步執行時，所有處理序仍會執行。 <br />然後所有處理序都會中斷。|目前處理序會逐步執行。 <br />暫止的處理序會繼續執行。 <br />執行中的處理序會繼續執行。|
|**偵錯** > **逐步執行目前處理序**，**進入目前處理序的步驟**，或**跳離目前處理序的函式**|N/A|目前處理序會逐步執行。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|
|來源視窗**中斷點**|所有處理序都會中斷。|只要來源視窗處理序會中斷。|
|來源視窗**執行至游標處**<br />來源視窗必須在目前處理序中。|當來源視窗處理序執行至游標處然後中斷時，所有處理序仍會執行。<br />然後所有其他處理序都會中斷。|來源視窗處理序會執行至游標處。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|
|**處理程序**視窗中 >**中斷處理序**|N/A|選取的處理序會中斷。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|
|**處理程序**視窗中 >**繼續處理序**|N/A|選取的處理序會繼續執行。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|

### <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> 尋找來來源和符號 (.pdb) 檔案
若要瀏覽處理序的原始程式碼，偵錯工具會需要存取其原始程式檔和符號檔。 如需詳細資訊，請參閱[指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

如果您無法存取處理程序的檔案，您可以使用瀏覽**反組譯碼**視窗。 如需詳細資訊，請參閱[如何：使用反組譯碼視窗](../debugger/how-to-use-the-disassembly-window.md)。

### <a name="BKMK_Switch_between_processes"></a> 在處理序之間切換

當您在偵錯，但在任何指定時間只有一個處理序是在偵錯工具中，您可以附加至多個處理序。 您可以在 [偵錯位置] 工具列或 [處理序] 視窗中設定使用中或「目前的」處理序。 若要在處理序之間切換，兩個處理序必須處於中斷模式。

**若要設定目前的處理序，從偵錯位置工具列：**

1. 若要開啟 **偵錯位置**工具列上，選取**檢視** > **工具列** > **偵錯位置**。

1. 在偵錯期間**偵錯位置**工具列上，選取您想要設定為從目前的處理序的處理序**程序**下拉式清單。

   ![切換處理序](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**若要從處理序 視窗中設定目前的處理序：**

1. 若要開啟 **處理程序**視窗中的，偵錯時，選取**偵錯** > **Windows** > **程序**。

1. 在 [**處理序**] 視窗中，目前的處理序會以黃色箭號標示。 按兩下您想要設定為目前的處理序的程序。

   ![處理序 視窗](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

切換至處理序設定為目前的處理序，以進行偵錯。 偵錯工具視窗會顯示目前的處理序的狀態，並逐步執行的命令會影響目前處理序。

## <a name="stop-debugging-with-multiple-processes"></a>停止使用多個處理序進行偵錯

根據預設，當您選取**偵錯** > **停止偵錯**，偵錯工具會結束或中斷所有處理程序。

- 如果目前的處理序已啟動的偵錯工具中，就會結束處理程序。

- 如果您將偵錯工具附加至目前的處理序，則偵錯工具會與處理序中斷連結，並讓處理序繼續執行。

如果您啟動偵錯的處理序，從 Visual Studio 方案，然後將附加到已在執行，另一個處理序，然後選擇**停止偵錯**、 偵錯工作階段隨即結束。 在 Visual Studio 中已啟動的處理序結束，而您附加至處理程序會繼續執行。

若要控制的方式，**停止偵錯**影響個別處理序，在**處理程序**視窗中，以滑鼠右鍵按一下處理程序，然後選取或清除**時停止偵錯中斷連結**  核取方塊。

>[!NOTE]
>**中斷所有處理序，當其中一個處理序中斷**偵錯工具選項不會影響停止、 結束，或是從處理序中斷連結。

### <a name="stop-terminate-and-detach-commands"></a>停止、結束及中斷連結命令

下表說明偵錯工具停駐點的行為、 結束及中斷連結具有多個處理序的命令：

|**命令**|**描述**|
|-|-|
|**偵錯** > **停止偵錯**|除非在變更行為**處理序**視窗中，偵錯工具來啟動處理序會結束，並附加的處理序會中斷連結。|
|**偵錯** > **全部結束**|所有處理程序會結束。|
|**偵錯** > **中斷所有連結**|偵錯工具會從所有處理序中斷連結。|
|**處理程序**視窗中 >**中斷處理序**|偵錯工具會從選取的處理序中斷連結。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|
|**處理程序**視窗中 >**結束處理序**|選取的處理序會結束。<br />其他處理序維持其現有的狀態 (已暫止或執行中)。|
|**處理程序**視窗中 >**偵錯停止時中斷連結**|如果選取，請**偵錯** > **停止偵錯**會從選取的處理序中斷連結。 <br />如果未選取，**偵錯** > **停止偵錯**終止選取的處理程序。 |

## <a name="see-also"></a>另請參閱

- [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Attach to running processes](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) (附加到正在執行的處理序)
- [Navigating through code with the debugger](../debugger/navigating-through-code-with-the-debugger.md) (使用偵錯工具巡覽程式碼)
- [Just-In-Time 偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)
- [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)