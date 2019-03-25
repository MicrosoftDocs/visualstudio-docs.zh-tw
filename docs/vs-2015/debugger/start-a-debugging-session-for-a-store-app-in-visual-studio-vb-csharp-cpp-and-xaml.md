---
title: (VB、 C#、 c + + 和 XAML） 的 Visual Studio 中啟動的市集應用程式的偵錯工作階段 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 66ec0e79-8261-4c19-a618-3fd1b3f71bbd
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb49d00d069a86be83ec02b92efe4ac93fc706b3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802573"
---
# <a name="start-a-debugging-session-for-a-store-app-in-visual-studio-vb-c-c-and-xaml"></a>在 Visual Studio 中，為市集應用程式啟動偵錯工作階段 (VB、C#、C++ 和 XAML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

適用於 Windows 和 Windows Phone] (../Image/windows_and_phone_content.png"windows_and_phone_content")  

 本主題說明如何對於以 XAML 和 Visual  C++、Visual C# 或 Visual Basic撰寫的市集應用程式，開始偵錯工作階段。 要對應用程式進行偵錯，必須設定偵錯工作階段並選擇應用程式的啟動方式。  

> [!NOTE]
>  如以 JavaScript 和 HTML 撰寫的應用程式，請參閱[啟動偵錯工作階段 (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)。  

##  <a name="BKMK_In_this_topic"></a>本主題內容  
 [開始偵錯的簡易方式](#BKMK_The_easy_way_to_start_debugging)  

 [設定偵錯工作階段](#BKMK_Configure_the_debugging_session)  

- [開啟專案的偵錯屬性頁](#BKMK_Open_the_debugging_property_page_for_the_project)  

- [選擇組建組態選項](#BKMK_Choose_the_build_configuration_options)  

- [選擇部署目標](#BKMK_Choose_the_deployment_target)  

- [選擇要使用的偵錯工具](#BKMK_Choose_the_debugger_to_use)  

- [(選擇性) 延遲開始偵錯工作階段](#BKMK__Optional__Delay_starting_the_debug_session)  

- [(選擇性) 停用網路回送](#BKMK__Optional__Disable_network_loopbacks)  

- [(選擇性) 當您開始偵錯時重新安裝應用程式](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)  

- [(選擇性) 停用驗證需求以啟動遠端偵錯工具](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)  

  [開始偵錯工作階段](#BKMK_Start_the_debugging_session)  

- [開始偵錯 (F5)](#BKMK_Start_debugging__F5_)  

- [開始偵錯 (F5)，但延遲啟動應用程式](#BKMK_Start_debugging__F5__but_delay_the_app_start)  

- [在偵錯工具中啟動已安裝的應用程式](#BKMK_Start_an_installed_app_in_the_debugger)  

- [將偵錯工具附加至執行中的應用程式](#BKMK_Attach_the_debugger_to_a_running_app_)  

  -   [將應用程式設定成以偵錯模式執行](#BKMK_Set_the_app_to_run_in_debug_mode)  

  -   [附加偵錯工具](#BKMK_Attach_the_debugger)  

##  <a name="BKMK_The_easy_way_to_start_debugging"></a> 開始偵錯的簡易方式  

1. 在 Visual Studio 中開啟應用程式方案。  

2. 選擇 f5 鍵。  

   Visual Studio 會建置附加了偵錯工具的應用程式，並加以啟動。 執行會持續到中斷點為止，若以手動方式暫停執行，就會發生未處理的例外狀況，或結束應用程式。 如需詳細資訊，請參閱 <<c0> [ 巡覽偵錯工作階段 （Xaml 和 C#）](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) 。  

##  <a name="BKMK_Configure_the_debugging_session"></a> 設定偵錯工作階段  

###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> 開啟專案的偵錯屬性頁  

1.  在 [方案總管] 中選取專案。 在捷徑功能表上選擇 [ **屬性**]。  

2.  執行下面步驟以開啟專案的偵錯屬性頁：  

    -   針對 Visual C# 與 Visual Basic 應用程式，請選擇 [ **偵錯**]。  

         ![C&#35; &#47; VB 專案偵錯屬性頁](../debugger/media/dbg-csvb-debugpropertypage.png "DBG_CsVb_DebugPropertyPage")  

    -   針對 Visual C++ 應用程式，請展開 [ **組態屬性**  ] 節點，然後選擇 [ **偵錯**]。  

         ![C&#43; &#43; Windows 市集應用程式偵錯屬性頁](../debugger/media/dbg-cpp-debugpropertypage.png "DBG_CPP_DebugPropertyPage")  

###  <a name="BKMK_Choose_the_build_configuration_options"></a> 選擇組建組態選項  

1.  請從 [ **組態** ] 清單中選擇 [ **偵錯** ] 或 [ **使用中 (偵錯)**]。  

2.  從 [ **平台** ] 清單中選擇要為其建置的目標平台。 在大部分情況下，[ **任何 CPU** ] (在 Visual C++ 中是 [**所有平台** ]) 是最佳選擇。  

###  <a name="BKMK_Choose_the_deployment_target"></a> 選擇部署目標  
 ![僅適用於 Windows](../debugger/media/windows-only-content.png "windows_only_content")  

 您可以在 Visual Studio 電腦、本機電腦上的 Visual Studio 模擬器或遠端裝置上部署和偵錯 Windows 市集應用程式。  

- 針對 C# 與 Visual Basic 應用程式，請在專案的 [ **偵錯** ] 屬性頁上，從 [ **目標裝置** ] 清單中選擇目標。  

- 針對 C++ 應用程式，請從 [ **偵錯** ] 屬性頁上的 [ **要啟動的偵錯工具** ] 清單中選擇目標：  

  選擇下列其中一個選項：  

|||  
|-|-|  
|**本機電腦**|在本機電腦上對目前工作階段中的應用程式進行偵錯。 請參閱[本機電腦上的執行 Windows 市集應用程式](../debugger/run-windows-store-apps-on-the-local-machine.md)。|  
|**模擬器**|在 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 應用程式的 Visual Studio 模擬器中進行應用程式偵錯。 模擬器是可讓您對本機電腦上無法使用的裝置功能 (例如觸控筆勢與裝置旋轉) 進行偵錯的桌面視窗。 請參閱[在模擬器中的執行 Windows 市集應用程式](../debugger/run-windows-store-apps-in-the-simulator.md)。|  
|**遠端電腦**|在透過內部網路連接到本機電腦的裝置上，或使用乙太網路纜線直接連接的裝置上，對應用程式進行偵錯。 若要遠端偵錯，必須在遠端裝置上安裝並執行 Visual Studio 遠端工具。 請參閱[在遠端電腦上的執行 Windows 市集應用程式](../debugger/run-windows-store-apps-on-a-remote-machine.md)。|  

 如果您選擇 [ **遠端電腦**]，請透過下列其中一種方法指定遠端電腦的名稱或 IP 位址：  

- 輸入遠端電腦的名稱或 IP 位址。  

  -   針對 C# 與 Visual Basic 應用程式，請在 [ **遠端電腦** ] 方塊中輸入名稱或 IP 位址。  

  -   針對 C++ 應用程式，請在 [ **電腦名稱** ] 方塊中輸入名稱或 IP 位址。  

- 從 [ **選取遠端偵錯工具連接** ] 對話方塊中選擇遠端電腦。  

   若要開啟此對話方塊：  

  - 針對 C# 與 Visual Basic 應用程式，請選擇 [ **尋找**]。  

  - 針對 c + + 應用程式中，選擇中的向下箭號**電腦名稱**方塊，然後選擇**\<尋找...>**。  

    ![選取遠端偵錯工具連接 對話方塊](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  

  > [!NOTE]
  >  [ **選取遠端偵錯工具連接** ] 對話方塊會顯示位於本機子網路上的電腦，以及透過乙太網路纜線直接連接至 Visual Studio 電腦的任何電腦。 若要指定另一部電腦，請在 [ **電腦名稱** ] 方塊中輸入名稱。  

  ![僅適用於 Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")  

  您可以將 Windows Phone 市集應用程式部署至裝置或其中一個 Visual Studio Phone 模擬器，以及進行偵錯。 從 [目標裝置]  清單選取裝置或模擬器。  

###  <a name="BKMK_Choose_the_debugger_to_use"></a> 選擇要使用的偵錯工具  
 根據預設，Visual Studio 會在 C# 與 Visual Basic 應用程式中對 Managed 程式碼進行偵錯。  

 針對 C# 與 Visual Basic 應用程式，您可以選擇在您的應用程式中對 Managed 與原生 C/C++ 程式碼進行偵錯。 請選取 [ **啟用 Unmanaged 程式碼偵錯** ] 核取方塊，將機器碼納入您的偵錯工作階段中。  

 根據預設，Visual Studio 會在您的 C++ 應用程式中對機器碼進行偵錯。  

 針對 C++ 應用程式，您可以選擇對您應用程式元件中的特定程式碼類型進行偵錯，並且 (或不要) 對機器碼進行偵錯。 您在應用程式專案的 [ **偵錯** ] 屬性頁面之 [ **偵錯工具類型** ] 清單中，指定要偵錯的程式碼。  

 從 [應用程式程序]  清單中，選擇下列其中一個偵錯工具：  

|||  
|-|-|  
|**僅限指令碼**|在您的應用程式中偵錯 JavaScript 程式碼。 Managed 程式碼與機器碼都會被忽略。|  
|**僅限原生**|在您的應用程式中偵錯原生 C/C++程式碼。 Managed 程式碼與 JavaScript 程式碼都會被忽略。|  
|**僅限 Managed**|在您的應用程式中偵錯 Managed 程式碼。 JavaScript 程式碼與原生 C/C++ 程式碼都會被忽略。|  
|**混合 (Managed 與原生)**|在您的應用程式中偵錯原生 C/C++ 程式碼與 Managed 程式碼。 JavaScript 程式碼會被忽略。|  
|**僅限 GPU**|對在圖形處理器 (GPU) 上執行的原生 C++ 程式碼進行偵錯。|  

 ![僅適用於 Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")  

 針對 Windows Phone 市集應用程式，您也可以從 [背景工作處理序] 選擇要用於背景處理序的偵錯工具。  

###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a> (選擇性) 延遲開始偵錯工作階段  
 根據預設，Visual Studio 會在您開始偵錯時立即啟動應用程式。 您也可以僅開始偵錯工作階段，而延遲啟動您的應用程式。 如果您選擇此選項，當應用程式從 [開始] 畫面或由啟用合約啟動，或是由其他處理序或方法啟動時，即會在偵錯工具中啟動。 在應用程式本身並未執行時，若要偵錯背景工作，您也會延遲應用程式的啟動。  

 若要延遲啟動應用程式，您可以：  

-   針對 Visual C# 與 Visual Basic 應用程式，請在 [ **偵錯** ] 屬性頁上選取 [ **不啟動，但在我的程式碼啟動時進行偵錯** ]。  

-   針對 Visual C++ 應用程式，請從 [ **偵錯** ] 屬性頁上的 [ **啟動應用程式** ] 清單中選擇 [ **是** ]。  

###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> (選擇性) 停用網路回送  
 ![僅適用於 Windows](../debugger/media/windows-only-content.png "windows_only_content")  

 基於安全性考量，不允許以標準模式安裝的 Windows 市集應用程式，對於其安裝所在的裝置進行網路呼叫。 根據預設，Visual Studio 部署會針對部署應用程式建立此規則的豁免。 此豁免可讓您測試在單一機器上的通訊程序。 在將您的應用程式提交至 Windows 市集之前，您應該在沒有豁免的情況下測試您的應用程式。  

 若要移除網路回送豁免：  

-   針對 Visual C# 與 Visual Basic 應用程式，清除 [ **偵錯** ] 屬性頁上的 [ **允許網路回送** ] 核取方塊。  

-   針對 Visual C++ 應用程式，請從 [ **偵錯** ] 屬性頁上的 [ **允許網路回送** ] 清單中選擇 [ **否** ]。  

###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> (選擇性) 當您開始偵錯時重新安裝應用程式  
 若要診斷 Visual C# 或 Visual Basic 應用程式的安裝與初始組態問題，請選擇 [ **偵錯** ] 屬性頁上的 [ **解除安裝再重新安裝我的套件**  ]，以便在開始偵錯時重新建立原始安裝。 Visual C++ 專案無法使用這個選項。  

###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> (選擇性) 停用驗證需求以啟動遠端偵錯工具  
 ![僅適用於 Windows](../debugger/media/windows-only-content.png "windows_only_content")  

 根據預設，您必須提供認證才能執行遠端偵錯工具。  

> [!IMPORTANT]
>  您可以選擇在 [非驗證] 模式下執行遠端偵錯工具，但非常不建議您使用這個模式。 在此模式中執行時不具有網路安全性。 只有在確定網路沒有面臨惡意或攻擊流量的風險時，才能選擇非驗證模式。  

 若要移除驗證需求：  

1. 針對 Visual C# 與 Visual Basic 應用程式，清除 [ **偵錯** ] 屬性頁上的 [ **使用驗證** ] 核取方塊。  

2. 針對 Visual C++ 應用程式，請從 [ **偵錯** ] 屬性頁上的 [ **需要驗證** ] 清單中選擇 [ **否** ]。  

   [本主題內容](#BKMK_In_this_topic)  

##  <a name="BKMK_Start_the_debugging_session"></a> 開始偵錯工作階段  

###  <a name="BKMK_Start_debugging__F5_"></a> 開始偵錯 (F5)  
 當您選擇**開始偵錯**(鍵盤： F5) 上**偵錯** 功能表中，Visual Studio 會啟動應用程式附加偵錯工具。 執行會持續到中斷點為止，若以手動方式暫停執行，就會發生例外狀況，或結束應用程式。  

###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> 開始偵錯 (F5)，但延遲啟動應用程式  
 您可以將應用程式設定成以偵錯模式執行，但卻是藉由偵錯工具以外的方式啟動。 例如，您可能會希望在應用程式從 [開始] 功能表啟動時進行偵錯，或是偵錯應用程式中的背景處理程序而不啟動應用程式。若要延遲啟動應用程式，請執行下列作業：  

- 在應用程式的 [ **偵錯** ] 屬性頁上 (在 Visual C++ 中為 [**偵錯** ])  

  -   針對 Visual C# 與 Visual Basic 應用程式，請選擇 [ **不啟動，但在我的程式碼啟動時進行偵錯**]。  

  -   針對 Visual C++ 應用程式，請從 [ **啟動應用程式** ] 清單中選擇 [ **是** ]。  

- 選擇**開始偵錯**上**偵錯**功能表 (鍵盤： F5)。  

- 從 [開始] 功能表、執行合約或透過其他程序啟動您的應用程式。  

  應用程式會以偵錯模式啟動。 執行會持續到中斷點為止，若以手動方式暫停執行，就會發生未處理的例外狀況，或結束應用程式。  

  。 如需有關偵錯背景工作的詳細資訊，請參閱 <<c0> [ 觸發程序暫止、 繼續及背景事件的 Windows 市集)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)。  

###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> 在偵錯工具中啟動已安裝的應用程式  
 使用 F5 開始偵錯時，Visual Studio 會建置並部署應用程式、將應用程式設定成以偵錯模式執行，然後再啟動應用程式。 若要啟動已安裝在裝置上的應用程式，請使用 [偵錯已安裝的應用程式套件] 對話方塊。 當您必須偵錯從 Windows 市集安裝的應用程式，或者有應用程式的原始程式檔，卻沒有應用程式的 Visual Studio 專案時，這個方式就很有用。 例如，您可能會有未使用 Visual Studio 專案或方案的自訂建置系統。  

 應用程式可以安裝在本機裝置，也可以安裝在遠端裝置上。  您可以立即啟動應用程式，也可以設定應用程式，使其藉由其他處理序或方式啟動 (例如從 [開始] 功能表或透過啟用合約) 後再於偵錯工具中執行。如果您只希望偵錯背景處理程序而不啟動應用程式，還可以將應用程式設定成以偵錯模式執行。 如需詳細資訊，請參閱 <<c0> [ 觸發程序暫止、 繼續及背景事件的 Windows 市集)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)。  

 若要將已安裝的應用程式設定成以偵錯模式執行，請執行下列作業：  

> [!NOTE]
>  以下程序必須在應用程式未執行時實施。  

1. 在 [ **偵錯** ] 功能表上，選擇 [ **偵錯 Installed App Package**]。  

2. 從清單中選擇下列其中一個選項：  


   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **本機電腦**  |                                                                                                                在本機電腦上對目前工作階段中的應用程式進行偵錯。 請參閱[本機電腦上的執行 Windows 市集應用程式](../debugger/run-windows-store-apps-on-the-local-machine.md)。                                                                                                                 |
   |   **模擬器**    | 在 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 應用程式的 Visual Studio 模擬器中進行應用程式偵錯。 模擬器是可讓您對本機電腦上無法使用的裝置功能 (例如觸控筆勢與裝置旋轉) 進行偵錯的桌面視窗。 請參閱[在模擬器中的執行 Windows 市集應用程式](../debugger/run-windows-store-apps-in-the-simulator.md)。 |
   | **遠端電腦** |                          在透過內部網路連接到本機電腦的裝置上，或使用乙太網路纜線直接連接的裝置上，對應用程式進行偵錯。 若要遠端偵錯，必須在遠端裝置上安裝並執行 Visual Studio 遠端工具。 請參閱[在遠端電腦上的執行 Windows 市集應用程式](../debugger/run-windows-store-apps-on-a-remote-machine.md)。                           |


3. 從 [ **已安裝的應用程式套件** ] 清單中選擇應用程式。  

4. 從 [ **偵錯這種程式碼類型** ] 清單中選擇要使用的偵錯引擎。  

5. (選擇性) 選擇 [ **不啟動，但在我的程式碼啟動時進行偵錯** ]，如此當其他方法啟動應用程式時，即可偵錯應用程式，或者偵錯背景處理程序。  

   當您按一下 [ **開始**] 時，就會啟動應用程式或是將其設定成以偵錯模式執行。  

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> 將偵錯工具附加至執行中的應用程式  
 若要將偵錯工具附加至 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 應用程式，您必須使用 [Debuggable Package 管理員] 將應用程式設定成以偵錯模式執行。 [Debuggable Package 管理員] 會隨 Visual Studio 遠端工具一起安裝。  

 當您需要偵錯已安裝的應用程式 (例如從 [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]安裝的應用程式) 時，將偵錯工具附加至應用程式將有所幫助。 當您具有應用程式的原始程式檔，但沒有應用程式的 Visual Studio 專案時，就必須進行附加。 例如，您可能會有未使用 Visual Studio 專案或方案的自訂建置系統。  

 要將偵錯工具附加至應用程式，必須執行下列步驟：  

1.  將應用程式設定成以偵錯模式執行。 此動作必須在應用程式未執行時完成。  

2.  啟動應用程式。 您可以從 [開始] 畫面、執行合約，或透過其他方法啟動應用程式。  

3.  將偵錯工具附加至執行中的應用程式。  

####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> 將應用程式設定成以偵錯模式執行  

1.  在已安裝應用程式的裝置上，安裝 Visual Studio 遠端工具。 請參閱 [安裝遠端工具](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools)。  

2.  在 [開始] 畫面上搜尋 `Debuggable Package Manager` ，並加以啟動。  

     針對 AppxDebug Cmdlet 適當設定的 PowerShell 視窗隨即出現。  

3.  若要啟用應用程式的偵錯功能，您必須指定此應用程式的 PackageFullName 識別項。 若要檢視包含 PackageFullName 的完整應用程式清單，請在 PowerShell 命令提示字元中輸入 `Get-AppxPackage` 。  

4.  在 PowerShell 命令提示字元中，輸入 `Enable-AppxDebug` *PackageFullName* ，其中 *PackageFullName* 是應用程式的 PackageFullName 識別項。  

####  <a name="BKMK_Attach_the_debugger"></a> 附加偵錯工具  
 若要附加偵錯工具：  

1. 在 [ **偵錯** ] 功能表上，選擇 [ **附加至處理序**]  

    [附加至處理序]  對話方塊隨即出現。  

2. 若要附加至遠端裝置上的應用程式，請在 [ **限定詞** ] 方塊中指定遠端裝置。 您可以：  

   -   在 [ **限定詞** ] 方塊中輸入名稱。  

   -   選擇 [ **限定詞** ] 方塊中的向下箭號，然後從您之前附加的裝置清單中選擇裝置。  

   -   選擇 [ **尋找** ]，以從本機子網路上的裝置清單中選取裝置。  

3. 在 [ **附加至** ] 方塊中指定要偵錯的程式碼類型。  

    選擇 [ **選取** ]，然後執行下列其中一項作業：  

   -   選擇 [ **自動判斷要偵錯的程式碼類型**]  

   -   選擇 [ **偵錯這些程式碼類型** ]，然後從清單中選擇一或多個類型。  

4. 在 [ **可使用的處理序**  ] 清單中，選擇應用程式處理序。  

5. 選擇 [ **附加**]。  

   Visual Studio 會將偵錯工具附加至處理序。 執行會持續到中斷點為止，若以手動方式暫停執行，就會發生未處理的例外狀況，或結束應用程式。  

   [本主題內容](#BKMK_In_this_topic)  

## <a name="see-also"></a>另請參閱  
 [Debug apps in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [巡覽偵錯工作階段 (Xaml 和 C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)



