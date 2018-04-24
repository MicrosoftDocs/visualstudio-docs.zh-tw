---
title: Visual Studio 中啟動的 UWP 應用程式的偵錯工作階段 |Microsoft 文件
ms.custom: ''
ms.date: 01/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
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
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: b298e2b17f1aa8805e0ab896c6978744c6c3bd53
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="start-a-debugging-session-for-a-uwp-app-in-visual-studio"></a>Visual Studio 中啟動的 UWP 應用程式的偵錯工作階段
  
 本主題描述如何啟動偵錯工作階段以 XAML 和 Visual c + +、 Visual C# 或 Visual Basic 撰寫的 UWP 應用程式，用於以 HTML 和 JavaScript 撰寫的 UWP 應用程式。 要對應用程式進行偵錯，必須設定偵錯工作階段並選擇應用程式的啟動方式。  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a> 開始偵錯的簡易方式  
  
1.  在 Visual Studio 中開啟應用程式方案。  
  
2.  選擇 f5 鍵。  
  
 Visual Studio 會建置附加了偵錯工具的應用程式，並加以啟動。 執行會持續到中斷點為止，若以手動方式暫停執行，就會發生未處理的例外狀況，或結束應用程式。  
  
##  <a name="BKMK_Choose_the_build_configuration_options"></a> 選擇組建組態選項  
  
1.   從下拉式清單旁邊的清單**開始偵錯**偵錯工具的按鈕**標準**工具列上，選擇**偵錯**。  
  
2.  從 [ **平台** ] 清單中選擇要為其建置的目標平台。  
  
##  <a name="BKMK_Choose_the_deployment_target"></a> 選擇部署目標  
  
您可以部署和偵錯 Visual Studio 電腦、 連接的裝置、 本機電腦、 遠端裝置或模擬器上的 Visual Studio 模擬器上的 UWP 應用程式。 從下拉式清單中選取部署目標，右邊**平台**偵錯工具的目標**標準**工具列。
  
![選擇部署目標](../debugger/media/vsrun_select_target_device.png)  
  
選擇下列其中一個選項：  
  
|||  
|-|-|  
|**本機電腦**|在本機電腦上對目前工作階段中的應用程式進行偵錯。|  
|**模擬器**|偵錯用於 UWP 應用程式的 Visual Studio 模擬器中的應用程式。 模擬器是可讓您偵錯裝置功能的桌面視窗 — 例如觸控筆勢與裝置旋轉 —，可能無法使用本機電腦上。 這個選項才可用如果您的應用程式**目標平台最小。版本**小於或等於您的開發電腦上的作業系統。 請參閱[在模擬器中執行的 UWP 應用程式](../debugger/run-windows-store-apps-in-the-simulator.md)。|  
|**遠端電腦**|在透過內部網路連接到本機電腦的裝置上，或使用乙太網路纜線直接連接的裝置上，對應用程式進行偵錯。 若要遠端偵錯，Visual Studio 遠端工具必須是遠端裝置上安裝並執行。 請參閱[遠端電腦上執行的 UWP 應用程式](../debugger/run-windows-store-apps-on-a-remote-machine.md)。|  
|**裝置**|USB 連接的裝置上的應用程式進行偵錯。 裝置必須是開發人員解除鎖定，並具有已解除鎖定螢幕。|  
|**行動裝置的模擬器**|模擬器啟動模擬器名稱中指定的設定、 部署應用程式，並開始偵錯。 只有在啟用 HYPER-V 機器上使用模擬器。|  

##  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> 選擇 其他偵錯選項  

如果您需要設定其他偵錯選項，開啟 專案屬性頁。
  
1.  在 [方案總管] 中選取專案。 在捷徑功能表上選擇 [ **屬性**]。  
  
2.  執行此作業以開啟專案的偵錯屬性頁：  
  
    -   針對 Visual C# 與 Visual Basic 應用程式，請選擇 [ **偵錯**]。  
  
         ![C&#35; &#47; VB 專案偵錯屬性頁](../debugger/media/dbg_csvb_debugpropertypage.png)  
  
    -   針對 Visual c + + 和 JavaScript 應用程式中，展開**組態屬性**節點，然後選擇 **偵錯**。  
  
         ![C&#43; &#43; UWP 應用程式偵錯屬性頁](../debugger/media/dbg_cpp_debugpropertypage.png)  

###  <a name="BKMK_Choose_the_debugger_to_use"></a> 選擇要使用的偵錯工具  
根據預設，Visual Studio 會在 C# 與 Visual Basic 應用程式中對 Managed 程式碼進行偵錯。 針對 C# 與 Visual Basic 應用程式，您可以選擇在您的應用程式中對 Managed 與原生 C/C++ 程式碼進行偵錯。 在 c + + 應用程式，Visual Studio 進行偵錯原生程式碼，根據預設。 在 JavaScript 應用程式，Visual Studio 進行偵錯指令碼，根據預設。 
  
如需 c + + 應用程式和 JavaScript 中，您可以選擇偵錯的程式碼應用程式而不是除了原生程式碼元件中的特定類型。 您在應用程式專案的 [ **偵錯** ] 屬性頁面之 [ **偵錯工具類型** ] 清單中，指定要偵錯的程式碼。  
  
從 [應用程式程序]  清單中，選擇下列其中一個偵錯工具：  
  
|||  
|-|-|  
|**僅限 Managed**|在您的應用程式中偵錯 Managed 程式碼。 JavaScript 程式碼與原生 C/C++ 程式碼都會被忽略。|  
|**僅限原生**|在您的應用程式中偵錯原生 C/C++程式碼。 Managed 程式碼與 JavaScript 程式碼都會被忽略。|  
|**混合 (Managed 與原生)**|在您的應用程式中偵錯原生 C/C++ 程式碼與 Managed 程式碼。 JavaScript 程式碼會被忽略。 此選項會在 c + + 專案中，稱為**（Managed 與原生）**。|  
|**僅限指令碼**|在您的應用程式中偵錯 JavaScript 程式碼。 Managed 程式碼與機器碼都會被忽略。|  
|**指令碼與原生**|偵錯原生 C/c + + 程式碼和應用程式中的 JavaScript 程式碼。 Managed 程式碼會被忽略。 適用於僅限 c + + 專案。|  
|**僅限 GPU (c + + AMP)**|對在圖形處理器 (GPU) 上執行的原生 C++ 程式碼進行偵錯。 適用於僅限 c + + 專案。|  

在 C# 和 Visual Basic 應用程式，您也可以設定相同**偵錯工具類型**屬於專案的任何背景工作的值。
  
###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a> (選擇性) 延遲開始偵錯工作階段  
 根據預設，Visual Studio 會在您開始偵錯時立即啟動應用程式。 您也可以僅開始偵錯工作階段，而延遲啟動您的應用程式。 如果您選擇此選項，當應用程式從 [開始] 畫面或由啟用合約啟動，或是由其他處理序或方法啟動時，即會在偵錯工具中啟動。 在應用程式本身並未執行時，若要偵錯背景工作，您也會延遲應用程式的啟動。  
  
 若要延遲啟動應用程式，您可以：  
  
-   針對 Visual C# 與 Visual Basic 應用程式，請在 [ **偵錯** ] 屬性頁上選取 [ **不啟動，但在我的程式碼啟動時進行偵錯** ]。  
  
-   針對 Visual c + + 和 JavaScript 的應用程式，選擇**否**從**啟動應用程式**清單**偵錯**屬性頁。  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> (選擇性) 停用網路回送  
  
 基於安全性理由，UWP 應用程式安裝在標準模式中不是允許進行網路呼叫其安裝所在的裝置。 根據預設，Visual Studio 部署會針對部署應用程式建立此規則的豁免。 此豁免可讓您測試在單一機器上的通訊程序。 提交您的 Microsoft 市集應用程式之前，您應該測試應用程式的豁免。  
  
 若要移除網路回送豁免：  
  
-   針對 Visual C# 和 Visual Basic 應用程式，清除**允許區域網路回送** 核取方塊**偵錯**屬性頁。  
  
-   針對 Visual c + + 和 JavaScript 的應用程式，選擇**否**從**允許區域網路回送**清單**偵錯**屬性頁。  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> (選擇性) 當您開始偵錯時重新安裝應用程式  
 若要診斷 Visual C# 或 Visual Basic 應用程式的安裝與初始組態問題，請選擇 [ **偵錯** ] 屬性頁上的 [ **解除安裝再重新安裝我的套件**  ]，以便在開始偵錯時重新建立原始安裝。 此選項不適用於 Visual c + + 和 JavaScript 專案中。  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> (選擇性) 停用驗證需求以啟動遠端偵錯工具  
  
 根據預設，您必須提供認證才能執行遠端偵錯工具，當您選取**遠端機器**做為部署目標。
  
> [!IMPORTANT]
>  您可以選擇執行遠端偵錯工具使用不需驗證，但不建議您使用這個模式。 在此模式中執行時不具有網路安全性。 只有在確定網路沒有惡意程式碼或惡意傳輸的風險，請選擇 不驗證。  
  
 若要移除驗證需求：  
  
1.  針對 Visual C# 和 Visual Basic 應用程式，選取**遠端機器**為**目標裝置**上**偵錯**屬性頁上，並將其設定**驗證模式**至**無**或**Universal （未加密的通訊協定）**。
  
2.  針對 Visual c + + 和 JavaScript 的應用程式，選取**遠端機器**為**目標裝置**上**偵錯**屬性頁上，並將其設定**需要驗證**至**無**或**Universal （未加密的通訊協定）**。  

    **通用 （未加密的通訊協定）**適用於當您部署到遠端裝置。 目前，這是 IoT 裝置、 Xbox 裝置和 HoloLens 裝置，以及建立者更新或更新版本的電腦。 通用 （未加密的通訊協定） 應該只用於受信任的網路。 偵錯連接容易受到惡意使用者便無法攔截及變更程式開發和遠端電腦之間傳遞資料。  
  
##  <a name="BKMK_Start_the_debugging_session"></a> 開始偵錯工作階段  
  
###  <a name="BKMK_Start_debugging__F5_"></a> 開始偵錯 (F5)  
 當您選擇**開始偵錯**(鍵盤： F5) 上**偵錯**功能表上，Visual Studio 啟動應用程式附加偵錯工具。 執行會持續到中斷點為止，若以手動方式暫停執行，就會發生例外狀況，或結束應用程式。  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> 開始偵錯 (F5)，但延遲啟動應用程式  
 您可以將應用程式設定成以偵錯模式執行，但卻是藉由偵錯工具以外的方式啟動。 比方說，您可能想要偵錯應用程式從 [開始] 功能表啟動或偵錯背景處理應用程式中的，而不啟動應用程式。 若要延遲啟動應用程式，請執行下列動作：  
  
-   在**偵錯**應用程式屬性頁面 (**偵錯**Visual c + + 和 JavaScript)  
  
    -   針對 Visual C# 與 Visual Basic 應用程式，請選擇 [ **不啟動，但在我的程式碼啟動時進行偵錯**]。  
  
    -   針對 Visual c + + 和 JavaScript 的應用程式，選擇**是**從**啟動應用程式**清單。  
  
-   選擇**開始偵錯**上**偵錯**功能表 (鍵盤： F5)。  
  
-   從 [開始] 功能表、執行合約或透過其他程序啟動您的應用程式。  
  
 應用程式會以偵錯模式啟動。 執行會持續到中斷點為止，若以手動方式暫停執行，就會發生未處理的例外狀況，或結束應用程式。  
  
 如需有關偵錯背景工作的詳細資訊，請參閱[觸發程序暫停、 繼續及背景事件用於 UWP 應用程式)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)。  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> 在偵錯工具中啟動已安裝的應用程式  
使用 F5 開始偵錯時，Visual Studio 會建置並部署應用程式、將應用程式設定成以偵錯模式執行，然後再啟動應用程式。 若要啟動已安裝在裝置的應用程式，使用**偵錯已安裝的應用程式套件** 對話方塊。 當您需要偵錯已安裝來自 Microsoft Store 的應用程式，或者有應用程式中，原始程式檔，但沒有應用程式的 Visual Studio 專案時，此程序會很有用。 例如，您可能會有未使用 Visual Studio 專案或方案的自訂建置系統。  
  
應用程式可以安裝在本機裝置，也可以安裝在遠端裝置上。  您可以立即啟動應用程式，也可以設定應用程式，使其藉由其他處理序或方式啟動 (例如從 [開始] 功能表或透過啟用合約) 後再於偵錯工具中執行。如果您只希望偵錯背景處理程序而不啟動應用程式，還可以將應用程式設定成以偵錯模式執行。 如需詳細資訊，請參閱[觸發程序暫停、 繼續及背景事件用於 UWP 應用程式)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)。  
  
若要啟動已安裝的應用程式偵錯工具中，選擇**偵錯**，然後**其他偵錯目標**，然後**偵錯已安裝的應用程式套件**。 如需其他指示，請參閱[偵錯已安裝的應用程式套件](../debugger/debug-installed-app-package.md)。

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> 將偵錯工具附加至執行的 UWP 應用程式  

若要執行的 UWP 應用程式進行偵錯，請選擇**偵錯**，然後**其他偵錯目標**，然後**偵錯已安裝的應用程式套件**。 如需其他指示，請參閱[偵錯已安裝的應用程式套件](../debugger/debug-installed-app-package.md)。
  
###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> 將偵錯工具附加至執行中 Windows 8.x 應用程式
 若要將偵錯工具附加至 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式，您必須使用 [Debuggable Package 管理員] 將應用程式設定成以偵錯模式執行。 Debuggable Package 管理員會隨 Visual Studio 遠端工具。  
  
 當您需要偵錯已安裝的應用程式 (例如從 [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]安裝的應用程式) 時，將偵錯工具附加至應用程式將有所幫助。 當您具有應用程式的原始程式檔，但沒有應用程式的 Visual Studio 專案時，就必須進行附加。 例如，您可能會有未使用 Visual Studio 專案或方案的自訂建置系統。  
  
 要將偵錯工具附加至應用程式，必須執行下列步驟：  
  
1.  將應用程式設定成以偵錯模式執行。 此動作必須在應用程式未執行時完成。  
  
2.  啟動應用程式。 您可以從 [開始] 畫面、執行合約，或透過其他方法啟動應用程式。  
  
3.  將偵錯工具附加至執行中的應用程式。  
  
####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> 將應用程式設定成以偵錯模式執行  
  
1.  應用程式已安裝在裝置上安裝 Visual Studio 遠端工具。 請參閱[安裝遠端工具](../debugger/remote-debugging.md)。  
  
2.  在 [開始] 畫面上搜尋 `Debuggable Package Manager` ，並加以啟動。  
  
     針對 AppxDebug Cmdlet 適當設定的 PowerShell 視窗隨即出現。  
  
3.  若要啟用應用程式的偵錯功能，您必須指定此應用程式的 PackageFullName 識別項。 若要檢視包含 PackageFullName 的完整應用程式清單，請在 PowerShell 命令提示字元中輸入 `Get-AppxPackage` 。  
  
4.  在 PowerShell 命令提示字元中，輸入 `Enable-AppxDebug` *PackageFullName* ，其中 *PackageFullName* 是應用程式的 PackageFullName 識別項。  
  
####  <a name="BKMK_Attach_the_debugger"></a> 附加偵錯工具  
 若要附加偵錯工具：  
  
1.  在 [ **偵錯** ] 功能表上，選擇 [ **附加至處理序**]  
  
     [附加至處理序]  對話方塊隨即出現。  
  
2.  若要附加至遠端裝置上的應用程式，請在 [ **限定詞** ] 方塊中指定遠端裝置。 您可以：  
  
    -   在 [ **限定詞** ] 方塊中輸入名稱。  
  
    -   選擇 [ **限定詞** ] 方塊中的向下箭號，然後從您之前附加的裝置清單中選擇裝置。  
  
    -   選擇 [ **尋找** ]，以從本機子網路上的裝置清單中選取裝置。  
  
3.  在 [ **附加至** ] 方塊中指定要偵錯的程式碼類型。  
  
     選擇 [ **選取** ]，然後執行下列其中一項作業：  
  
    -   選擇 [ **自動判斷要偵錯的程式碼類型**]  
  
    -   選擇 [ **偵錯這些程式碼類型** ]，然後從清單中選擇一或多個類型。  
  
4.  在 [ **可使用的處理序**  ] 清單中，選擇應用程式處理序。  

    > [!NOTE]
    >  不同於其他應用程式類型，JavaScript 應用程式是在 wwahost.exe 處理序的執行個體中執行。 如果在您附加至應用程式時有其他 JavaScript 應用程式正在執行，則需要知道在其中執行應用程式之 wwahost.exe 的數值處理序 ID (PID)。  
    >   
    >  處理此情況的最簡單方式是關閉所有其他 JavaScript 應用程式。 否則，您可以在啟動應用程式之前開啟 Windows 工作管理員，並記下 wwahost.exe 處理序的 ID。 當您指定要附加的處理序**可用的處理序**對話方塊中，應用程式的 wwahost.exe 會有不同於您已記下的 id。  
  
5.  選擇 [ **附加**]。  
  
 Visual Studio 會將偵錯工具附加至處理序。 執行會持續到中斷點為止，若以手動方式暫停執行，就會發生未處理的例外狀況，或結束應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Visual Studio 中的應用程式](../debugger/debug-store-apps-in-visual-studio.md)   