---
title: 調試多個進程 |微軟文檔
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a2679825d41a6360dde05e7511d607f8be69dfa
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302550"
---
# <a name="debug-multiple-processes"></a>對多重處理序進行偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

以下說明如何開始偵錯處理序、在處理序之間切換、中斷和繼續執行、逐步執行來源、停止偵錯，以及結束處理序或中斷處理序連結。  
  
## <a name="contents"></a><a name="BKMK_Contents"></a>內容  
 [設定多個處理序的執行行為](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [查找源和符號 （.pdb） 檔](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [在 VS 方案中啟動多個處理序、附加至處理序、在偵錯工具中自動啟動處理序](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [切換進程、中斷並繼續執行、單一步驟源](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [停止偵錯、結束處理序或中斷處理序連結](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
## <a name="configure-the-execution-behavior-of-multiple-processes"></a><a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>配置多個進程的執行行為  
 根據預設，當偵錯工具中有多個處理序正在執行時，中斷、逐步執行或停止偵錯工具命令通常會影響所有處理序。 例如，當一個處理序在中斷點暫止時，所有其他處理序的執行也會暫止。 您可以變更這項預設行為，以便更充分掌控執行命令的目標。  
  
1. 在 [ **偵錯** ] 功能表上選擇 [ **選項和設定**]。  
  
2. 在 **"調試****""常規**"頁上，清除 **"當一個進程中斷時"所有進程"** 核取方塊。  
  
   ![返回頂部](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)  
  
## <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> 尋找來來源和符號 (.pdb) 檔案  
 若要巡覽處理序的原始程式碼，偵錯工具需要存取處理序的原始程式檔和符號檔。 請參閱[指定符號 （.pdb） 和原始檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。  
  
 如果您無法存取處理序的檔案，可以使用 [反組譯碼] 視窗進行巡覽。 [請參閱如何：使用拆卸視窗](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![返回頂部](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)  
  
## <a name="start-multiple-processes-in-a-vs-solution-attach-to-a-process-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a>在 VS 解決方案中啟動多個進程，附加到進程，在調試器中自動啟動進程  
  
- [在 Visual Studio 解決方案中開始調試多個進程](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution)•[更改啟動專案](#BKMK_Change_the_startup_project)•[在解決方案中啟動特定專案](#BKMK_Start_a_specific_project_in_a_solution)•[在解決方案中啟動多個專案](#BKMK_Start_multiple_projects_in_a_solution)•[附加到進程](#BKMK_Attach_to_a_process)•[自動啟動調試器中的進程](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
> 偵錯工具不會自動附加至所偵錯處理序啟動的子處理序 (即使子專案位於相同方案中)。 若要偵錯子處理序：  
> 
> - 在子處理序啟動之後附加至該子處理序。  
> 
>   -或-  
>   - 將 Windows 設定為自動在偵錯工具的新執行個體中啟動子處理序。  
  
### <a name="start-debugging-multiple-processes-in-a-visual-studio-solution"></a><a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a>在視覺化工作室解決方案中開始調試多個進程  
 如果您的 Visual Studio 方案中有多個可以獨立執行的專案 (在個別處理序中執行的專案)，您就可以選取偵錯工具要啟動的專案。  
  
 ![變更專案的啟動類型](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
#### <a name="change-the-startup-project"></a><a name="BKMK_Change_the_startup_project"></a>更改啟動專案  
 要更改解決方案的啟動專案，請在解決方案資源管理器中選擇專案，然後從內容功能表中選擇 **"設置為啟動專案**"。  
  
#### <a name="start-a-specific-project-in-a-solution"></a><a name="BKMK_Start_a_specific_project_in_a_solution"></a>在解決方案中啟動特定專案  
 要在不更改預設啟動專案的情況下啟動解決方案的專案，請在解決方案資源管理器中選擇專案，然後從內容功能表中選擇 **"調試**"。 然後，您可以選擇 **"開始新實例****"或"步進到新實例**"。  
  
 ![返回頂級](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [VS 解決方案中的多個進程，附加到進程，在調試器中自動啟動進程](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![返回頂部](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)  
  
#### <a name="start-multiple-projects-in-a-solution"></a><a name="BKMK_Start_multiple_projects_in_a_solution"></a>在解決方案中啟動多個專案  
  
1. 在解決方案資源管理器中選擇解決方案，然後在內容功能表中選擇 **"屬性**"。  
  
2. 在"**屬性**"對話方塊中選擇 **"常見屬性****"啟動專案**。  
  
3. 對於要更改的每個專案，請選擇 **"開始"、****不調試即可啟動**或 **"無**"。  
  
   ![返回頂級](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [VS 解決方案中的多個進程，附加到進程，在調試器中自動啟動進程](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![返回頂部](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)  
  
### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> 附加至處理序  
 調試器還可以*附加到*在 Visual Studio 外部的進程中運行的程式，包括在遠端設備上運行的程式。 附加至程式之後，您就可以使用偵錯工具的執行命令、檢查程式狀態等等。 根據程式建置時是否包含偵錯資訊以及您是否能存取程式的原始程式碼，還有 Common Language Runtime JIT 編譯器是否會追蹤偵錯資訊，可能會對檢查程式狀態的能力有所限制。  
  
 有關詳細資訊[，請參閱附加到正在運行的進程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
 **附加至正在本機電腦上執行的處理序**  
  
 選擇**調試**，**附加到進程**。 在"**附加到進程"** 對話方塊中，從 **"可用進程"** 清單中選擇"進程"，然後選擇 **"附加**"。  
  
 ![附加到進程對話方塊](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![返回頂部](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)  
  
### <a name="automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>在調試器中自動啟動進程  
 有時候，您可能需要對其他處理序所啟動程式的啟始程式碼進行偵錯。 這類範例包括了服務和自訂安裝動作。 在這些案例中，您可以讓偵錯工具在應用程式啟動時啟動並自動附加。  
  
1. 啟動登錄編輯程式 **（regedit.exe**）。  
  
2. 導航到**HKEY_LOCAL_MACHINE\軟體\微軟\Windows NT_當前版本\影像檔執行選項資料夾**。  
  
3. 選取要在偵錯工具中啟動之應用程式的資料夾。  
  
    如果應用的名稱未列為子資料夾，請選擇**影像檔執行選項**，然後在內容功能表上選擇 **"新建**"**鍵**。 選擇新鍵，在快顯功能表上選擇 **"重命名**"，然後輸入應用的名稱。  
  
4. 在應用資料夾的內容功能表上，選擇 **"新建**"、"**字串值**"。  
  
5. 將新值的名稱從 **"新值"** 更改為`debugger`。  
  
6. 在調試器條目的內容功能表上，選擇 **"修改**"。  
  
7. 在"編輯字串"對話方塊中，`vsjitdebugger.exe`在 **"值資料**"框中鍵入。  
  
    ![[編輯字串] 對話方塊](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![regedit.exe 中的自動偵錯工具起始項目](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![返回頂部](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)  
  
## <a name="switch-processes-break-and-continue-execution-step-through-source"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>切換進程、中斷並繼續執行、單一步驟源  
  
- [在進程之間切換](#BKMK_Switch_between_processes)•[中斷、步進和繼續命令](#BKMK_Break__step__and_continue_commands)  
  
### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> 在處理序之間切換  
 進行偵錯時，您可以附加至多個處理序，但是無論在任何時間，偵錯工具一次只能有一個使用中處理序。 您可以在"調試位置"工具列或 **"進程"** 視窗中設置活動或*當前*進程。 若要在處理序之間切換，兩個處理序必須處於中斷模式。  
  
 **若要設定目前的處理序**  
  
- 在"調試位置"工具列上，選擇 **"過程**"以查看 **"過程"** 清單方塊。 選取您要指定為目前處理序的處理序。  
  
   ![在進程之間切換](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   如果**調試位置**工具列不可見，請選擇 **"工具****"，自訂**。 在**工具列**選項卡上，選擇 **"調試位置**"。  
  
- 打開 **"進程"** 視窗（**快捷方式 Ctrl_Alt_Z），** 找到要設置為當前進程的進程，然後按兩下它。  
  
   ![進程視窗](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   目前的處理序會以黃色箭號標記。  
  
  切換至專案會將該專案設為目前要偵錯的處理序。 您檢視的所有偵錯工具視窗都會顯示目前處理序的狀態，而且所有逐步執行命令只會影響目前處理序。  
  
  ![返回頂部](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[交換器進程、中斷並繼續執行、單一步驟源](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![返回頂部](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)  
  
### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> 中斷、逐步執行和繼續命令  
  
> [!NOTE]
> 根據預設，中斷、繼續和逐步執行偵錯工具命令會影響所有正在偵錯的處理序。 要更改此行為，請參閱[配置多個進程的執行行為](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**命令**|**當一個進程中斷時中斷所有進程**<br /><br /> 已核取 (預設值)|**當一個進程中斷時中斷所有進程**<br /><br /> 已清除|  
|**調試**功能表：<br /><br /> -   **全部中斷**|所有處理序都會中斷。|所有處理序都會中斷。|  
|**調試**功能表：<br /><br /> -   **繼續**|所有處理序都會繼續執行。|所有暫止的處理序都會繼續執行。|  
|**調試**功能表：<br /><br /> -   **步入**<br />-   **單一步驟**<br />-   **走出來**|當目前處理序逐步執行時，所有處理序仍會執行。<br /><br /> 然後所有處理序都會中斷。|目前處理序會逐步執行。<br /><br /> 暫止的處理序會繼續執行。<br /><br /> 執行中的處理序會繼續執行。|  
|**調試**功能表：<br /><br /> -   **進入當前流程的步驟**<br />-   **超越當前流程的步驟**<br />-   **退出當前流程**|N/A|目前處理序會逐步執行。<br /><br /> 其他處理序維持其現有的狀態 (已暫止或執行中)。|  
|來源視窗<br /><br /> -   **中斷點**|所有處理序都會中斷。|只要來源視窗處理序會中斷。|  
|來源視窗內容功能表：<br /><br /> -   **運行到游標**<br /><br /> 來源視窗必須在目前處理序中。|當來源視窗處理序執行至游標處然後中斷時，所有處理序仍會執行。<br /><br /> 然後所有其他處理序都會中斷。|來源視窗處理序會執行至游標處。<br /><br /> 其他處理序維持其現有的狀態 (已暫止或執行中)。|  
|**處理**視窗內容功能表：<br /><br /> -   **中斷過程**|N/A|選取的處理序會中斷。<br /><br /> 其他處理序維持其現有的狀態 (已暫止或執行中)。|  
|**處理**視窗內容功能表：<br /><br /> -   **繼續處理**|N/A|選取的處理序會繼續執行。<br /><br /> 其他處理序維持其現有的狀態 (已暫止或執行中)。|  
  
 ![返回頂部](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[交換器進程、中斷並繼續執行、單一步驟源](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![返回頂部](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)  
  
## <a name="stop-debugging-terminate-or-detach-from-processes"></a><a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a>停止調試、終止或從進程分離  
  
- [停止、結束及中斷連結命令](#BKMK_Stop__terminate__and_detach_commands)  
  
  預設情況下，當您選擇**調試**器時**停止調試**時，調試器會終止或從所有進程分離，具體取決於調試器中進程如何打開：  
  
- 如果目前處理序是在偵錯工具中啟動，則會結束該處理序。  
  
- 如果您將偵錯工具附加至目前的處理序，則偵錯工具會與處理序中斷連結，並讓處理序繼續執行。  
  
  例如，如果從 Visual Studio 解決方案開始調試進程，請附加到正在運行的另一個進程，然後選擇 **"停止調試**"，調試會話結束，在 Visual Studio 中啟動的進程終止，而您連接的進程保持運行。 您可以使用下列程序控制停止偵錯的方式。  
  
> [!NOTE]
> **當一個進程中斷選項時中斷所有進程**不會影響停止調試或終止和從進程分離。  
  
 **若要變更停止偵錯影響個別處理序的方式**  
  
- 打開**進程**視窗（快捷方式**Ctrl_Alt_Z**）。 選擇進程，然後在**調試停止時選擇或清除"分離"** 核取方塊。  
  
### <a name="stop-terminate-and-detach-commands"></a><a name="BKMK_Stop__terminate__and_detach_commands"></a>停止、終止和分離命令  
  
|||  
|-|-|  
|**命令**|**描述**|  
|**調試**功能表：<br /><br /> -   **停止調試**|除非調試停止時**進程**視窗 **"分離"** 更改了行為選項：<br /><br /> 1. 調試器啟動的進程將終止。<br />2. 附加的進程與調試器分離。|  
|**調試**功能表：<br /><br /> -   **終止所有**|所有處理序都會結束。|  
|**調試**功能表：<br /><br /> -   **全部分離**|偵錯工具會從所有處理序中斷連結。|  
|**處理**視窗內容功能表：<br /><br /> -   **分離過程**|偵錯工具會從選取的處理序中斷連結。<br /><br /> 其他處理序維持其現有的狀態 (已暫止或執行中)。|  
|**處理**視窗內容功能表：<br /><br /> -   **終止進程**|選取的處理序將會結束。<br /><br /> 其他處理序維持其現有的狀態 (已暫止或執行中)。|  
|**處理**視窗內容功能表：<br /><br /> -   **調試停止時分離**|切換所選進程的**調試**、**停止調試**的行為：<br /><br /> - 已檢查：調試器從進程分離。<br />- 已清除：進程已終止。|  
  
 ![返回頂部](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[停止調試、終止或從進程分離](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![返回頂部](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)  
  
## <a name="see-also"></a>另請參閱  
 [指定符號 （.pdb） 和原始檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [附加到正在運行的進程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [使用調試器導航代碼](../debugger/navigating-through-code-with-the-debugger.md)   
 [及時調試](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [對多執行緒應用程式進行偵錯](../debugger/debug-multithreaded-applications-in-visual-studio.md)
