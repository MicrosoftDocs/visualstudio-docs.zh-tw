---
title: 啟動 UWP 應用程式的偵測會話 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/20/2018
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
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: c4504dda362c8a50f33168a12839e894a14316d7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72436013"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>啟動 UWP 應用程式 的偵錯工作階段

本文說明如何為通用 Windows 平臺（UWP）應用程式啟動 Visual Studio 的偵測會話。 UWP 應用程式可以用 XAML 和C++xaml 和C#/Visual Basic 撰寫。 若要開始偵測 UWP 應用程式，請設定偵錯工具，並選擇啟動應用程式的方式。

::: moniker range=">=vs-2019"
> [!NOTE]
> 從 Visual Studio 2019 開始，已不再支援適用于 HTML 和 JavaScript 的 UWP 應用程式。
::: moniker-end
::: moniker range="vs-2017"
在 Visual Studio 2017 中，本文中所顯示的大部分命令和選項也適用于 HTML 和 JavaScript 的 UWP 應用程式。 當受控和C++應用程式之間的命令不同時，JavaScript 應用程式通常與C++ UWP 應用程式的命令相同。
::: moniker-end

## <a name="BKMK_The_easy_way_to_start_debugging"></a>從 [Visual Studio] 工具列開始調試

設定和啟動調試最簡單的方式是從 [標準 Visual Studio] 工具列。

![從工具列進行 Debug](../debugger/media/vsrun_select_target_device.png)

1. 從 [**標準** **] 工具列**上的 [設定] 下拉式清單中，選取 [ **Debug**]。

1. 從 [**平臺**] 下拉式清單中，選取要為其建立的目標平臺。

1. 從綠色箭號旁邊的下拉式清單中，選取 [debug] 目標。 您可以選擇本機電腦、直接連線的裝置、本機 Visual Studio 模擬器、遠端裝置或模擬器。

1. 若要開始進行調試，請選取工具列上的綠色**開始**箭號，或選取 [ **Debug**]  > **開始進行調試**，或按**F5**。

   Visual Studio 會建置附加了偵錯工具的應用程式，並加以啟動。

偵錯工具會繼續進行，直到到達中斷點、手動暫止執行、發生未處理的例外狀況，或應用程式結束為止。

### <a name="BKMK_Choose_the_deployment_target"></a>部署目標選項

您可以在 [Visual Studio] 工具列或專案的 [偵錯工具] 屬性頁中設定偵錯工具目標。 選取下列其中一個選項：

|||
|-|-|
|**本機電腦**|在本機電腦上對目前工作階段中的應用程式進行偵錯。|
|**模擬器**|在適用于 UWP 應用程式的 Visual Studio 模擬器中，對應用程式進行 Debug。 模擬器是一個桌面視窗，可模擬本機電腦上可能不存在的裝置功能（例如觸控手勢和裝置輪替）。 只有當您的應用程式的**目標平臺最低版本**小於或等於本機電腦上的作業系統時，才可以使用 [模擬器] 選項。 如需詳細資訊，請參閱[在模擬器中執行 UWP 應用程式](../debugger/run-windows-store-apps-in-the-simulator.md)。|
|**遠端電腦**|在透過網路或 Ethernet 纜線連線到本機電腦的裝置上，對應用程式進行 Debug。 您必須在遠端裝置上安裝並執行 Visual Studio 遠端工具。 如需詳細資訊，請參閱[在遠端電腦上執行 UWP 應用程式](../debugger/run-windows-store-apps-on-a-remote-machine.md)。|
|**裝置**|在 USB 連線的裝置上，對應用程式進行偵錯工具。 裝置必須為開發人員解除鎖定，且螢幕已解除鎖定。|
|**行動模擬器**|啟動模擬器名稱中指定的模擬器、部署應用程式，然後開始進行偵錯工具。 模擬器只能在已啟用 Hyper-v 的電腦上使用。|

## <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>在專案屬性頁中設定調試

若要設定其他偵錯工具選項，請使用專案的 [偵錯工具屬性] 頁面。

**若要開啟調試屬性：**

1. 在**方案總管**中選取專案，然後選取 [**屬性**] 圖示，或以滑鼠右鍵按一下專案，然後選取 [**屬性**]。

1. 在 [**屬性**] 窗格的左側：

   - 針對C#和 Visual Basic 應用程式，請選取 [ **Debug**]。

     ![C#和 Visual Basic 專案 debug 屬性頁](../debugger/media/dbg_csvb_debugpropertypage.png)

   - 針對C++應用程式，選取 [設定] [**屬性**] [ > **調試**程式]。

     ![C++UWP 應用程式的偵錯工具屬性頁](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="BKMK_Choose_the_debugger_to_use"></a> 選擇要使用的偵錯工具

對於C#和 Visual Basic 應用程式，Visual Studio 預設會將受控碼進行調試。 您可以選擇要對其他或其他程式碼類型進行偵錯工具。 您也可以針對屬於專案一部分的任何背景工作，設定**偵錯工具類型**的值。

在C++ [應用程式] 中，預設 Visual Studio 調試機器碼。 您可以選擇針對特定類型的程式碼（而不是或除了機器碼）進行偵錯工具。

**若要指定要進行偵錯工具的程式碼類型：**

- 針對C#和 Visual Basic 應用程式，請從 [**調試**程式**類型] 下的**[**應用程式類型**] 和 [**背景處理類型**] 下拉式清單中選取下列其中一個偵錯工具。

- 針對C++應用程式，請從 [**調試**程式] 屬性頁上的 [調試**程式類型**] 下拉式清單中選取下列其中一個偵錯工具。

|||
|-|-|
|**僅限 Managed**|在您的應用程式中偵錯 Managed 程式碼。 JavaScript 程式碼與原生 C/C++ 程式碼都會被忽略。|
|**僅限原生**|在您的應用程式中偵錯原生 C/C++程式碼。 Managed 程式碼與 JavaScript 程式碼都會被忽略。|
|**混合 (Managed 與原生)**|在您的應用程式中偵錯原生 C/C++ 程式碼與 Managed 程式碼。 JavaScript 程式碼會被忽略。 在C++專案中，此選項稱為 [ **Managed] 和 [原生**]。|
|**指令碼**|在您的應用程式中偵錯 JavaScript 程式碼。 Managed 程式碼與機器碼都會被忽略。|
|**機器碼加指令碼**|在您的應用C++程式中，對原生 C/Code 和 JavaScript 程式碼進行 Debug。 Managed 程式碼會被忽略。 僅適用C++于專案或背景工作。|
|**僅限 GPU (C++ AMP)**|對在圖形處理器 (GPU) 上執行的原生 C++ 程式碼進行偵錯。 僅適用C++于專案。|

### <a name="BKMK__Optional__Disable_network_loopbacks"></a>停用網路回送（選擇性）

 基於安全性，以標準方式安裝的 UWP 應用程式無法對其安裝所在的裝置進行網路呼叫。 根據預設，Visual Studio 從這個規則豁免部署的應用程式，因此您可以在單一電腦上測試通訊程式。 在您發行應用程式之前，您應該先測試應用程式而不豁免。

**移除網路回送豁免：**

- 對於C#和 Visual Basic 應用程式，請取消選取 [ **Debug** ] 屬性頁上 [**啟動選項**] 下的 [**允許區域網路回送**] 核取方塊。

- 針對C++應用程式，請**從 [偵測] 屬性頁**上的 [**允許區域網路回送**] 下拉式清單選取 [**否**]。

### <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>當您啟動偵錯工具時，請重新安裝應用程式（選擇性）
 若要診斷C#或 Visual Basic 應用程式的安裝問題，請選取 [ **Debug** ] 屬性頁上的 [**卸載再重新安裝我的套件**]。 此選項會在您開始進行調試時重新建立原始安裝。 此選項不適用於C++專案。

### <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>設定遠端偵錯程式的驗證選項

根據預設，當您選取 [**遠端電腦**] 作為部署目標時，您必須提供 Windows 認證來執行遠端偵錯程式。 您可以變更驗證需求。

**通用（未加密的通訊協定）** 驗證模式適用于 IoT、Xbox 和 HoloLens 裝置，以及建立者的更新或更新版本的 Windows 10 電腦。

**若要變更驗證方法：**

- 針對C#和 Visual Basic 應用程式，請在 [ **Debug** ] 屬性頁上，選取 [**遠端電腦**] 做為**目標裝置**。 然後，針對**驗證模式**選取 [**無**] 或 **[通用（未加密的通訊協定）** ]。

- 針對C++應用程式，請選取 [**調試**程式] 下的 [**遠端電腦**]，在 [偵測] 屬性頁上**啟動** 然後，針對 [**驗證類型**] 選取 [**無驗證**] 或 **[通用（未加密通訊協定）** ]。

> [!CAUTION]
> 當您以**無**或**通用（未加密的通訊協定）** 模式執行遠端偵錯程式時，不會有網路安全性。 請只在您確定不會有惡意程式碼或惡意流量風險的信任網路上，選擇這些模式。

## <a name="BKMK_Start_the_debugging_session"></a>調試開始選項

當您選取 [ **Debug** > ] [**開始調試**程式] 或按**F5**時，Visual Studio 會啟動已附加偵錯工具的應用程式。 執行會持續到中斷點為止，若以手動方式暫停執行，就會發生未處理的例外狀況，或結束應用程式。

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>開始進行偵測，但延遲應用程式啟動

根據預設，當您開始進行偵錯工具時，Visual Studio 會立即啟動應用程式。 您也可以將應用程式設定為在「偵測模式」中執行，但在偵錯工具外部啟動應用程式。 例如，您可能想要從 Windows [**開始**] 功能表中，或在應用程式中對背景進程進行偵錯工具啟動。 如果您選擇此選項，應用程式會在啟動時于偵錯工具中啟動。

**若要停用自動啟動應用程式：**

- 針對C#和 Visual Basic 應用程式，請選取 [**不啟動，但在我的程式碼啟動時，** 在**debug** ] 屬性頁上的 [**啟動選項**] 底下進行調試。

- 針對C++應用程式，請從 [**調試**程式] 屬性頁上的 [**啟動應用程式**] 下拉式清單選取 [**否**]

如需有關偵測背景工作的詳細資訊，請參閱[觸發 UWP 應用程式的暫止、繼續和背景事件](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)。

### <a name="BKMK_Start_an_installed_app_in_the_debugger"></a>對已安裝或執行中的 UWP 應用程式進行 Debug

您可以使用 [**已安裝的應用程式套件**]，來對已安裝或正在本機或遠端裝置上執行的 UWP 應用程式進行偵測。 應用程式可能已從 Microsoft Store 安裝，或可能不是 Visual Studio 專案。 例如，應用程式可能會有不會使用 Visual Studio 的自訂群組建系統。

您可以立即啟動已安裝的應用程式，也可以在以另一個方法啟動時，將它設定為在偵錯工具中執行。 如需詳細資訊，請參閱[觸發 UWP 應用程式的暫止、繼續和背景事件](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)。

若要在偵錯工具中啟動已安裝或執行中的 UWP 應用程式，請選取 [ **debug** > ] [**其他 debug 目標**]  > **Debug 已安裝應用程式套件**。 如需詳細指示，請參閱[Debug 已安裝的應用程式套件](../debugger/debug-installed-app-package.md)。

### <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>將偵錯工具附加至執行中的 Windows 8.x 應用程式

若要將偵錯工具附加至 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式，您必須使用 [Debuggable Package 管理員] 將應用程式設定成以偵錯模式執行。 可調試套件管理員會隨 Visual Studio 遠端工具一起安裝。

1. 在安裝應用程式的裝置上安裝 Visual Studio 遠端工具。 如需詳細資訊，請參閱[安裝遠端工具](../debugger/remote-debugging.md)。

1. 在 Windows [**開始**] 畫面中，搜尋並開始可**調試封裝管理員**。

   針對 AppxDebug Cmdlet 適當設定的 PowerShell 視窗隨即出現。

1. 指定應用程式的 PackageFullName 識別碼。

   1. 若要查看包含所有應用程式 PackageFullName 的清單，請在 PowerShell 命令提示字元中輸入 `Get-AppxPackage`。

   1. 在 PowerShell 命令提示字元中，輸入 `Enable-AppxDebug <PackageFullName>`，其中 \<PackageFullName > 是應用程式的 PackageFullName 識別碼。

1. 選取 [偵錯] > [附加至處理序]。

1. 在 [**附加至進程**] 對話方塊中，于 [**連接目標**] 方塊中指定遠端裝置。

   您可以輸入裝置名稱、從 [連線**目標**] 方塊的下拉式清單中選取它，或選取 [**尋找**] 以在 [**遠端**連線] 對話方塊中尋找裝置。

1. 若要指定您要進行偵錯工具的程式碼類型，請選取 [**附加至**] 方塊旁的 [**選取**]。

1. 在 [**選取程式碼類型**] 對話方塊中，選取下列其中一項：
   - **自動判斷要進行 debug 錯的程式碼類型**，或
   - 請對**這些程式碼類型進行調試**程式，然後從清單中選取一或多個程式碼類型。

1. 在 [**可使用的進程**] 清單中，選取要進行 debug 的應用程式進程。

1. 選取 [**附加**]。

 Visual Studio 會將偵錯工具附加至處理序。 執行會持續到中斷點為止，若以手動方式暫停執行，就會發生未處理的例外狀況，或結束應用程式。

::: moniker range="vs-2017"
> [!NOTE]
> JavaScript 應用程式會在 *wwahost.exe* 處理序的執行個體中執行。 如果有多個 JavaScript 應用程式正在執行，您將需要知道應用程式的*wwahost.exe*進程的數值處理序識別碼（PID），才能附加至其中。
>
> 附加至 JavaScript 應用程式最簡單的方式，就是關閉所有其他 JavaScript 應用程式。 或者，在啟動應用程式之前，您可以記下在 Windows 工作管理員中執行*wwahost.exe*進程的 pid。 當您啟動應用程式時，其*Wwahost.exe* PID 會與您先前記下的不同。
::: moniker-end

## <a name="see-also"></a>請參閱

- [在 Visual Studio 中偵錯應用程式](../debugger/debugging-windows-store-and-windows-universal-apps.md)