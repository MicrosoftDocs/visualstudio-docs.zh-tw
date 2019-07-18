---
title: 開始 UWP 應用程式的偵錯工作階段 |Microsoft Docs
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
ms.openlocfilehash: 7c65662d054b8c3dd9e650fe088f7048cc3b4071
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62930057"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>啟動 UWP 應用程式 的偵錯工作階段

本文說明如何啟動的通用 Windows 平台 (UWP) 應用程式的 Visual Studio 偵錯工作階段。 可以在 XAML 中撰寫 UWP 應用程式和C++，XAML 和C#/Visual Basic。 開始偵錯的 UWP 應用程式，請設定偵錯工作階段，然後選擇 啟動應用程式的方式。

::: moniker range=">=vs-2019"
> [!NOTE]
> 不再支援從 Visual Studio 2019，HTML 和 JavaScript 的 UWP 應用程式。
::: moniker-end
::: moniker range="vs-2017"
在 Visual Studio 2017 中，大部分的命令和本文中所顯示的選項也適用於 UWP 應用程式的 HTML 和 JavaScript。 命令所在不同受管理和C++應用程式，JavaScript 應用程式通常是相同的命令C++UWP 應用程式。
::: moniker-end

## <a name="BKMK_The_easy_way_to_start_debugging"></a>從 Visual Studio 工具列中開始偵錯

若要設定及開始偵錯最簡單的方式是從標準的 Visual Studio 工具列中。

![從工具列的偵錯](../debugger/media/vsrun_select_target_device.png)

1. 從**組態**下拉式清單中**標準**工具列上，選取**偵錯**。

1. 從**平台**下拉式清單中，選取要建置的目標平台。

1. 從綠色箭號旁邊下拉式清單中，選取 [偵錯目標]。 您可以選擇本機電腦，直接連線的裝置、 本機 Visual Studio 模擬器、 遠端裝置或模擬器。

1. 若要開始偵錯，請選取綠色**開始**上的工具列上或選取箭號**偵錯** > **開始偵錯**，或按**F5**.

   Visual Studio 會建置附加了偵錯工具的應用程式，並加以啟動。

偵錯會繼續直到到達中斷點、 您以手動方式暫停執行時，發生未處理的例外狀況，或結束應用程式。

### <a name="BKMK_Choose_the_deployment_target"></a> 部署目標選項

您可以設定偵錯目標，在 Visual Studio 工具列中，或專案的偵錯屬性頁。 選取下列其中一個選項：

|||
|-|-|
|**本機電腦**|在本機電腦上對目前工作階段中的應用程式進行偵錯。|
|**模擬器**|偵錯的 UWP app 的 Visual Studio 模擬器中的應用程式。 模擬器是模擬裝置功能，例如觸控筆勢與裝置旋轉，可能不存在於本機電腦上的桌面視窗。 使用模擬器選項則只有當您的應用程式**目標平台最小值。版本**小於或等於本機電腦上的作業系統。 如需詳細資訊，請參閱 <<c0> [ 在模擬器中的執行 UWP app](../debugger/run-windows-store-apps-in-the-simulator.md)。|
|**遠端電腦**|透過網路或乙太網路纜線連接到本機電腦的裝置上的應用程式進行偵錯。 Visual Studio 遠端工具必須安裝並執行遠端裝置上。 如需詳細資訊，請參閱 <<c0> [ 在遠端電腦上的執行 UWP app](../debugger/run-windows-store-apps-on-a-remote-machine.md)。|
|**裝置**|USB 連接的裝置上的應用程式進行偵錯。 裝置必須是開發人員解除鎖定，且要解除鎖定螢幕。|
|**行動裝置模擬器**|啟動模擬器名稱中指定的模擬器、 部署應用程式，並開始偵錯。 模擬器是只能在已啟用 HYPER-V 機器上使用。|

## <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> 設定專案屬性頁中的偵錯

若要設定額外的偵錯選項，請使用專案的偵錯屬性頁。

**若要開啟偵錯的屬性：**

1. 在 [**方案總管] 中**，選取專案，然後選取**屬性**圖示，或以滑鼠右鍵按一下專案，然後選取**屬性**。

1. 在左邊**屬性**窗格：

   - 針對C#和 Visual Basic 應用程式，選取**偵錯**。

     ![C#和 Visual Basic 專案偵錯屬性頁](../debugger/media/dbg_csvb_debugpropertypage.png)

   - 針對C++應用程式，選取**組態屬性** > **偵錯**。

     ![C++UWP 應用程式偵錯屬性頁](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="BKMK_Choose_the_debugger_to_use"></a> 選擇要使用的偵錯工具

針對C#和 Visual Basic 應用程式，Visual Studio 會偵錯 managed 程式碼的預設值。 您可以選擇其他的或額外的程式碼類型進行偵錯。 您也可以設定**偵錯工具類型**是專案一部分的任何背景工作的值。

在C++預設應用程式，Visual Studio 偵錯的原生程式碼。 您可以選擇偵錯特定類型的程式碼，或除了原生程式碼。

**若要指定要偵錯的程式碼類型：**

- 針對C#和 Visual Basic 應用程式中，選取從下列偵錯工具的其中一個**應用程式類型**並**背景處理程序類型**底下的下拉式清單**偵錯工具類型**上**偵錯**屬性頁。

- 針對C++應用程式，選取 [從下列偵錯工具的其中一個**偵錯工具類型**上的下拉式清單**偵錯**] 屬性頁。

|||
|-|-|
|**僅限 Managed**|在您的應用程式中偵錯 Managed 程式碼。 JavaScript 程式碼與原生 C/C++ 程式碼都會被忽略。|
|**僅限原生**|在您的應用程式中偵錯原生 C/C++程式碼。 Managed 程式碼與 JavaScript 程式碼都會被忽略。|
|**混合 (Managed 與原生)**|在您的應用程式中偵錯原生 C/C++ 程式碼與 Managed 程式碼。 JavaScript 程式碼會被忽略。 在C++專案中，此選項稱為**Managed 和原生**。|
|**指令碼**|在您的應用程式中偵錯 JavaScript 程式碼。 Managed 程式碼與機器碼都會被忽略。|
|**機器碼加指令碼**|偵錯原生 C /C++程式碼和應用程式中的 JavaScript 程式碼。 Managed 程式碼會被忽略。 提供C++專案或背景工作只。|
|**僅限 GPU (C++ AMP)**|對在圖形處理器 (GPU) 上執行的原生 C++ 程式碼進行偵錯。 提供C++僅限專案。|

### <a name="BKMK__Optional__Disable_network_loopbacks"></a> 停用網路回送 （選擇性）

 為了安全性，以標準方式安裝的 UWP 應用程式無法進行到其安裝所在裝置的網路呼叫。 Visual Studio 豁免部署預設的情況下，這項規則的應用程式，因此您可以測試在單一機器上的通訊程序。 發行您的應用程式之前，您應該測試您的應用程式，而不需要豁免。

**移除網路回送豁免：**

- 針對C#和 Visual Basic 應用程式，取消選取**允許區域網路回送**底下的核取方塊**起始選項**上**偵錯** 屬性頁。

- 視覺效果C++應用程式，選取**No**從**允許本機網路 Loopback**上的下拉式清單**偵錯** 屬性頁。

### <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> 重新安裝應用程式，當您啟動偵錯 （選擇性）
 若要診斷安裝問題C#或 Visual Basic 應用程式，選取**解除安裝再重新安裝我的包裹**上**偵錯** 屬性頁。 當您啟動偵錯時，此選項會重新建立原始安裝。 此選項不適用於C++專案。

### <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> 設定遠端偵錯的驗證選項

根據預設，您必須提供 Windows 認證，才能執行遠端偵錯工具，當您選取**遠端機器**做為部署目標。 您可以變更驗證需求。

**通用 （未加密的通訊協定）** 驗證模式是適用於 IoT、 Xbox 和 HoloLens 裝置，和建立者的更新或更新版本的 Windows 10 電腦。

**若要變更驗證方法：**

- 針對C#和 Visual Basic 應用程式，在**偵錯**屬性頁上，選取**遠端機器**做為**目標裝置**。 然後，選取**無**或**通用 （未加密的通訊協定）** for **Mode**。

- 針對C++應用程式，選取**遠端電腦**底下**偵錯工具啟動**上**偵錯** 屬性頁。 然後，選取**不需要驗證**或**通用 （未加密的通訊協定）** for**驗證類型**。

> [!CAUTION]
> 當您在執行遠端偵錯工具時，會不具有網路安全性**無**或是**通用 （未加密的通訊協定）** 模式。 選擇這些模式，只在您的受信任網路上確定不是從惡意程式碼或惡意流量的風險。

## <a name="BKMK_Start_the_debugging_session"></a> 偵錯的啟動選項

當您選取**偵錯** > **開始偵錯**或按**F5**，Visual Studio 附加偵錯工具啟動應用程式。 執行會持續到中斷點為止，若以手動方式暫停執行，就會發生未處理的例外狀況，或結束應用程式。

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> 開始偵錯，但延遲啟動應用程式

根據預設，Visual Studio 會在只有在您開始偵錯時，立即啟動應用程式。 您也可以設定應用程式，以在偵錯模式中執行，但啟動偵錯工具外部應用程式。 例如，您可能想要偵錯從 Windows 應用程式啟動**啟動** 功能表中或偵錯應用程式中的背景處理程序。 如果您選擇此選項時，應用程式會在啟動偵錯工具中啟動。

**若要停用自動的應用程式啟動：**

- 針對C#和 Visual Basic 應用程式，選取**不啟動，但啟動時，將我的程式碼進行偵錯**底下**起始選項**上**偵錯** 屬性頁。

- 針對C++應用程式，選取**否**從**啟動應用程式**上的下拉式清單**偵錯** 屬性頁。

如需有關偵錯背景工作的詳細資訊，請參閱 <<c0> [ 觸發程序暫止、 繼續及背景事件用於 UWP 應用程式](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)。

### <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> 偵錯已安裝或執行 UWP 應用程式

您可以使用**偵錯 Installed App Package**偵錯已安裝或在本機或遠端裝置上執行的 UWP 應用程式。 應用程式可能已從 Microsoft Store 中，安裝，或可能不是 Visual Studio 專案。 例如，應用程式可能不會使用 Visual Studio 的自訂建置系統。

您可以立即開始安裝的應用程式，或您可以將它設定為偵錯工具啟動另一個方法時執行。 如需詳細資訊，請參閱 <<c0> [ 觸發程序暫止、 繼續及背景事件用於 UWP 應用程式)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)。

若要啟動已安裝或執行 UWP 應用程式偵錯工具中，選取**偵錯** > **其他偵錯目標** > **偵錯 Installed App Package**。 如需詳細指示，請參閱 <<c0> [ 偵錯已安裝的應用程式套件](../debugger/debug-installed-app-package.md)。

### <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> 將偵錯工具附加至執行中 Windows 8.x 應用程式

若要將偵錯工具附加至 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式，您必須使用 [Debuggable Package 管理員] 將應用程式設定成以偵錯模式執行。 Debuggable Package 管理員會隨 Visual Studio 遠端工具。

1. 應用程式已安裝在裝置上安裝適用於 Visual Studio 的遠端工具。 如需詳細資訊，請參閱 <<c0> [ 安裝遠端工具](../debugger/remote-debugging.md)。

1. 在 Windows**開始**畫面上，搜尋並開始**Debuggable Package 管理員**。

   針對 AppxDebug Cmdlet 適當設定的 PowerShell 視窗隨即出現。

1. 指定應用程式的 PackageFullName 識別項。

   1. 若要檢視包含所有應用程式的 PackageFullName 的完整清單，請輸入`Get-AppxPackage`在 PowerShell 提示字元。

   1. 在 PowerShell 提示字元中，輸入`Enable-AppxDebug <PackageFullName>`，其中\<PackageFullName > 是應用程式的 PackageFullName 識別項。

1. 選取 [偵錯] > [附加至處理序]。

1. 在 [ **připojit k procesu**對話方塊方塊中，指定遠端裝置**連線目標**] 方塊中。

   您可以輸入裝置名稱，從下拉式清單中選取它**連線目標**方塊中，或選取**尋找**尋找在裝置**遠端連線** 對話方塊。

1. 若要指定您想要偵錯，旁邊的程式碼的類型**附加至**方塊中，選取**選取**。

1. 在 **選取程式碼類型**對話方塊方塊中，選取其中一個：
   - **自動判斷要偵錯的程式碼類型**，或
   - **偵錯這些程式碼類型**，並從清單中選取一或多個程式碼類型。

1. 在 **可用的處理序**清單中，選取 偵錯的應用程式程序。

1. 選取 **附加**。

 Visual Studio 會將偵錯工具附加至處理序。 執行會持續到中斷點為止，若以手動方式暫停執行，就會發生未處理的例外狀況，或結束應用程式。

::: moniker range="vs-2017"
> [!NOTE]
> JavaScript 應用程式會在 *wwahost.exe* 處理序的執行個體中執行。 如果一個以上的 JavaScript 應用程式正在執行，您必須知道您的應用程式的數字的處理序識別碼 (PID) *wwahost.exe*來附加至它的程序。
>
> 附加至您的 JavaScript 應用程式的最簡單方式是關閉所有其他 JavaScript 應用程式。 或者，您可以記下執行的 Pid *wwahost.exe* Windows 工作管理員 中才啟動應用程式的程序。 當您啟動您的應用程式，其*wwahost.exe* PID 會是不同於您先前記下的一個。
::: moniker-end

## <a name="see-also"></a>另請參閱
- [在 Visual Studio 中偵錯應用程式](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)