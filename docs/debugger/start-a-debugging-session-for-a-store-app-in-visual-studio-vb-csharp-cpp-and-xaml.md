---
title: 啟動 UWP 應用程式的偵測會話 |Microsoft Docs
description: 針對通用 Windows 平臺 (UWP) 應用程式啟動 Visual Studio 的偵錯工具。 設定偵錯工具會話，並選擇啟動應用程式的方式。
ms.custom: SEO-VS-2020
ms.date: 11/20/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: d0669f9838073571018eb762e98aa6d907456f12
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386458"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>啟動 UWP 應用程式 的偵錯工作階段

本文說明如何針對通用 Windows 平臺 (UWP) 應用程式啟動 Visual Studio 的偵錯工具會話。 UWP 應用程式可以撰寫成 XAML 和 c + +、XAML 和 c #/Visual Basic。 若要開始對 UWP 應用程式進行偵錯工具，請設定偵錯工具會話，並選擇啟動應用程式的方式。

::: moniker range=">=vs-2019"
> [!NOTE]
> 從 Visual Studio 2019 開始，已不再支援適用于 HTML 和 JavaScript 的 UWP 應用程式。
::: moniker-end
::: moniker range="vs-2017"
在 Visual Studio 2017 中，本文中所顯示的大部分命令和選項也適用于適用于 HTML 和 JavaScript 的 UWP 應用程式。 當 managed 和 c + + 應用程式之間的命令不同時，JavaScript 應用程式通常會與 c + + UWP 應用程式的命令相同。
::: moniker-end

## <a name="start-debugging-from-the-visual-studio-toolbar"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>從 Visual Studio 的工具列啟動調試

設定和啟動偵錯工具的最簡單方式是從標準 Visual Studio 工具列。

![從工具列進行調試](../debugger/media/vsrun_select_target_device.png)

1. 從 [**標準**] 工具列上的 [設定] 下拉式清單中，**選取 [** **Debug**]。

1. 從 [ **平臺** ] 下拉式清單中，選取要建立的目標平臺。

1. 從綠色箭號旁的下拉式清單中，選取 [debug] 目標。 您可以選擇本機電腦、直接連接的裝置、本機 Visual Studio 模擬器、遠端裝置或模擬器。

1. 若要啟動調試，請選取工具列上的綠色 [**開始**] 箭號，或選取 [ **Debug**  >  **開始調試**]，或按 **F5**。

   Visual Studio 會建置附加了偵錯工具的應用程式，並加以啟動。

偵錯工具會繼續進行，直到達到中斷點、手動暫停執行、發生未處理的例外狀況，或應用程式結束為止。

### <a name="deployment-target-options"></a><a name="BKMK_Choose_the_deployment_target"></a> 部署目標選項

您可以在 [Visual Studio] 工具列或專案的 [偵錯工具] 屬性頁中設定偵錯工具的目標。 選取下列其中一個選項：

|Name|描述|
|-|-|
|**本機電腦**|在本機電腦上對目前工作階段中的應用程式進行偵錯。|
|**模擬器**|在適用于 UWP 應用程式的 Visual Studio 模擬器中，為應用程式進行偵錯工具。 模擬器是一個桌面視窗，可模擬本機電腦上可能不存在的裝置功能，例如觸控手勢和裝置旋轉。 只有當您應用程式的 **目標平臺最低版本** 小於或等於本機電腦上的作業系統時，才可使用模擬器選項。 如需詳細資訊，請參閱 [在模擬器中執行 UWP 應用程式](../debugger/run-windows-store-apps-in-the-simulator.md)。|
|**遠端電腦**|在透過網路或乙太網路纜線連接到本機電腦的裝置上，進行應用程式的偵錯工具。 您必須在遠端裝置上安裝並執行 Visual Studio 遠端工具。 如需詳細資訊，請參閱 [在遠端電腦上執行 UWP 應用程式](../debugger/run-windows-store-apps-on-a-remote-machine.md)。|
|**裝置**|在連接 USB 的裝置上進行應用程式的偵錯工具。 裝置必須由開發人員解除鎖定，並將螢幕解除鎖定。|
|**行動模擬器**|開機模擬器名稱中指定的模擬器、部署應用程式，然後開始進行偵錯工具。 模擬器只能在已啟用 Hyper-v 的電腦上使用。|

## <a name="configure-debugging-in-the-project-property-page"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> 在專案屬性頁中設定調試

若要設定其他偵錯工具選項，請使用專案的偵錯工具屬性頁面。

**若要開啟調試屬性：**

1. 在 **方案總管** 中，選取專案，然後選取 [ **屬性** ] 圖示，或以滑鼠右鍵按一下專案，然後選取 [ **屬性**]。

1. 在 [ **屬性** ] 窗格的左邊：

   - 若為 c # 和 Visual Basic 應用程式，請選取 [ **Debug**]。

     ![C # 和 Visual Basic 專案調試屬性頁面](../debugger/media/dbg_csvb_debugpropertypage.png)

   - 若是 c + + 應用程式，請選取 [設定 **屬性**]  >  **調試** 程式。

     ![C + + UWP 應用程式偵錯工具屬性頁](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a> 選擇要使用的偵錯工具

針對 c # 和 Visual Basic 應用程式，Visual Studio 預設會將 managed 程式碼進行調試。 您可以選擇要進行其他或其他程式碼類型的偵錯工具。 您也可以針對屬於專案一部分的任何背景工作，設定 **偵錯工具類型** 值。

在 c + + 應用程式中，Visual Studio 預設會將原生程式碼進行調試。 您可以選擇將特定類型的程式碼（而不是）或機器碼（除了機器碼）進行調試。

**若要將程式碼類型指定為 debug：**

- 針對 c # 和 Visual Basic apps，請從 [ **應用程式類型** ] 和 [ **背景** 程式類型] 下拉式清單中的 [偵錯工具 **類型** ] 底下的 [ **調試** 程式類型] 下，選取下列其中一個

- 若是 c + + 應用程式，請從 [**調試** 程式] 屬性頁的 [調試 **程式類型**] 下拉式清單中選取下列其中一個偵錯工具。

|Name|描述|
|-|-|
|**僅限 Managed**|在您的應用程式中偵錯 Managed 程式碼。 JavaScript 程式碼與原生 C/C++ 程式碼都會被忽略。|
|**僅限原生**|在您的應用程式中偵錯原生 C/C++程式碼。 Managed 程式碼與 JavaScript 程式碼都會被忽略。|
|**混合 (Managed 與原生)**|在您的應用程式中偵錯原生 C/C++ 程式碼與 Managed 程式碼。 JavaScript 程式碼會被忽略。 在 c + + 專案中，此選項稱為「 **Managed」和「原生**」。|
|**指令碼**|在您的應用程式中偵錯 JavaScript 程式碼。 Managed 程式碼與機器碼都會被忽略。|
|**機器碼加指令碼**|在您的應用程式中偵測原生 C/c + + 程式碼和 JavaScript 程式碼。 已忽略 Managed 程式碼。 僅適用于 c + + 專案或背景工作。|
|**僅限 GPU (C++ AMP)**|對在圖形處理器 (GPU) 上執行的原生 C++ 程式碼進行偵錯。 僅適用于 c + + 專案。|

### <a name="disable-network-loopbacks-optional"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a> 停用網路回送 (選用) 

 基於安全性，以標準方式安裝的 UWP 應用程式無法對其安裝所在的裝置進行網路呼叫。 根據預設，Visual Studio 豁免已從此規則部署應用程式，因此您可以在單一電腦上測試通訊程式。 在您發行應用程式之前，您應該先測試您的應用程式，而不需豁免。

**移除網路回送豁免：**

- 針對 c # 和 Visual Basic apps，請在 [**調試** 程式] 屬性頁的 [**開始選項**] 下，取消選取 [**允許區域網路回送**] 核取方塊

- 若是 c + + 應用程式，**請從 [** **調試** 程式] 屬性頁的 [**允許區域網路回送**] 下拉式清單中選取 [

### <a name="reinstall-the-app-when-you-start-debugging-optional"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> 當您開始 (選擇性的偵錯工具時，請重新安裝應用程式) 
 若要使用 c # 或 Visual Basic 應用程式診斷安裝問題，請選取 [卸載]，然後在 [**調試** 程式] 屬性頁上 **重新安裝套件**。 此選項會在您開始進行調試時重新建立原始安裝。 C + + 專案無法使用這個選項。

### <a name="set-authentication-options-for-remote-debugging"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> 設定遠端偵錯程式的驗證選項

依預設，當您選取 [ **遠端電腦** ] 作為部署目標時，必須提供 Windows 認證才能執行遠端偵錯程式。 您可以變更驗證需求。

**通用 (未加密的通訊協定)** 驗證模式適用于 IoT、Xbox 和 HoloLens 裝置，以及建立者的更新或更新版本 Windows 10 電腦。

**若要變更驗證方法：**

- 針對 c # 和 Visual Basic 應用程式，請在 [ **調試** 程式] 屬性頁上，選取 [ **遠端電腦** ] 作為 **目標裝置**。 然後，為 **驗證模式** 選取 [**無**] 或 [**通用 (未加密的通訊協定)** 。

- 若是 c + + 應用程式，請選取 [偵錯工具] 底下的 [ **遠端電腦** ]， **以啟動** [ **調試** 程式] 然後，針對 **驗證類型** 選取 [**無驗證**] 或 [**通用 (未加密的通訊協定)** 。

> [!CAUTION]
> 當您在 [ **無** ] 或 [ **通用 (未加密的通訊協定])** 模式中執行遠端偵錯程式時，沒有網路安全性。 請只在您確定的受信任網路上選擇這些模式，而不會有惡意程式碼或惡意流量的風險。

## <a name="debugging-start-options"></a><a name="BKMK_Start_the_debugging_session"></a> 調試開始選項

當您選取 [ **Debug**  >  **開始調試** 程式] 或按 **F5** 時，Visual Studio 會啟動附加偵錯工具的應用程式。 執行會持續到中斷點為止，若以手動方式暫停執行，就會發生未處理的例外狀況，或結束應用程式。

### <a name="start-debugging-but-delay-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> 開始偵錯工具，但延遲應用程式啟動

根據預設，Visual Studio 會在您啟動偵錯工具時立即啟動應用程式。 您也可以將應用程式設定為在 debug 模式中執行，但在偵錯工具之外啟動應用程式。 例如，您可能想要從 Windows [ **開始** ] 功能表，或在應用程式中對背景進程進行偵錯工具啟動。 如果您選擇此選項，則應用程式會在啟動時于偵錯工具中啟動。

**若要停用自動啟動應用程式：**

- 若為 c # 和 Visual Basic 應用程式，請選取 [**不啟動，但** 在偵錯工具的程式碼啟動時，于 **調試** 程式] 屬性 **頁上啟動** 時進行 debug 錯。

- 若是 c + + 應用程式，請從 [**調試** 程式] 屬性頁 **上的 [** **啟動應用程式**] 下拉式清單中選取

如需有關偵錯工具背景工作的詳細資訊，請參閱 [觸發 UWP 應用程式的暫止、繼續及背景事件](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)。

### <a name="debug-an-installed-or-running-uwp-app"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a> 針對已安裝或執行中的 UWP 應用程式進行偵錯工具

您可以使用已 **安裝的已安裝應用程式套件** ，來偵測已安裝或在本機或遠端裝置上執行的 UWP 應用程式。 應用程式可能已從 Microsoft Store 安裝，或可能不是 Visual Studio 專案。 例如，應用程式可能會有不使用 Visual Studio 的自訂群組建系統。

您可以立即啟動已安裝的應用程式，也可以將它設定為在啟動時使用另一個方法來執行偵錯工具。 如需詳細資訊，請參閱 [) 中觸發 UWP 應用程式的暫止、繼續及背景事件 ](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)。

若要在偵錯工具中啟動已安裝或執行中的 UWP 應用程式，**請選取 [** 偵測到  >    >  **已安裝的應用程式封裝** 的其他偵錯工具 如需詳細指示，請參閱 [偵錯工具已安裝的應用程式套件](../debugger/debug-installed-app-package.md)。

### <a name="attach-the-debugger-to-a-running-windows-8x-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> 將偵錯工具附加至執行中的 Windows 8. x 應用程式

若要將偵錯工具附加至 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式，您必須使用 [Debuggable Package 管理員] 將應用程式設定成以偵錯模式執行。 可偵錯套件管理員與 Visual Studio 遠端工具一起安裝。

1. 在安裝應用程式的裝置上安裝 Visual Studio 遠端工具。 如需詳細資訊，請參閱 [安裝遠端工具](../debugger/remote-debugging.md)。

1. 在 Windows [ **開始** ] 畫面中，搜尋並啟動 **可偵錯套件管理員**。

   針對 AppxDebug Cmdlet 適當設定的 PowerShell 視窗隨即出現。

1. 指定應用程式的 PackageFullName 識別碼。

   1. 若要查看包含所有應用程式 PackageFullName 的清單，請 `Get-AppxPackage` 在 PowerShell 提示字元中輸入。

   1. 在 PowerShell 提示字元中，輸入 `Enable-AppxDebug <PackageFullName>` ，其中 \<PackageFullName> 是應用程式的 PackageFullName 識別碼。

1. 選取 [ **Debug**  >  **附加至進程**]。

1. 在 [ **附加至進程** ] 對話方塊中，于 [ **連接目標** ] 方塊中指定遠端裝置。

   您可以輸入裝置名稱，從 [**連接目標**] 方塊的下拉式清單中選取它，或在 [**遠端** 連線] 對話方塊中選取 [**尋找**] 以尋找裝置。

1. 若要指定您要進行偵錯工具的程式碼類型，請選取 [ **附加至** ] 方塊旁的 [ **選取**]。

1. 在 [ **選取程式碼類型** ] 對話方塊中，選取下列其中一項：
   - **自動判斷要進行調試** 程式的程式碼類型，或
   - 將 **這些程式碼類型進行調試** 程式，然後從清單中選取一或多個程式碼類型。

1. 在 [ **可使用的進程**  ] 清單中，選取要進行偵錯工具的應用程式進程。

1. 選取 [附加]。

 Visual Studio 會將偵錯工具附加至處理序。 執行會持續到中斷點為止，若以手動方式暫停執行，就會發生未處理的例外狀況，或結束應用程式。

::: moniker range="vs-2017"
> [!NOTE]
> JavaScript 應用程式會在 *wwahost.exe* 處理序的執行個體中執行。 如果有一個以上的 JavaScript 應用程式正在執行，您必須知道應用程式 *wwahost.exe* 程式的數值處理序識別碼 (PID) 才能附加至該應用程式。
>
> 附加至 JavaScript 應用程式的最簡單方式是關閉所有其他 JavaScript 應用程式。 或者，您可以在啟動應用程式之前，記下在 Windows 工作管理員中執行 *wwahost.exe* 進程的 pid。 當您啟動應用程式時，它的 *wwahost.exe* PID 將會與您先前注明的不同。
::: moniker-end

## <a name="see-also"></a>另請參閱

- [Debug apps in Visual Studio](../debugger/debugging-windows-store-and-windows-universal-apps.md)