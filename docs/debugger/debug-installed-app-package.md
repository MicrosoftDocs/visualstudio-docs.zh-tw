---
title: 偵錯已安裝的 UWP 應用程式套件 |Microsoft Docs
ms.custom: ''
ms.date: 11/07/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 10e10b512dc8deb63db7ade2075347d9e6405b6b
ms.sourcegitcommit: cdcbf254db737d42275e95de4ffc4f8c14e87e00
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57428709"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>偵錯在 Visual Studio 中的已安裝的 UWP 應用程式套件

Visual Studio 可以偵錯已安裝的 Windows 10 電腦和 Xbox、 HoloLens、 和 IoT 裝置上的通用 Windows 平台 (UWP) 應用程式套件。

>[!NOTE]
>在手機上不支援 visual Studio 偵錯已安裝的 UWP 應用程式。

如需偵錯 UWP 應用程式的詳細資訊，請參閱部落格文章[偵錯已安裝的應用程式套件](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/)並[建置通用 Windows App (UWP)](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/)。

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>偵錯在本機電腦上的已安裝的 UWP 應用程式

1. 在 Visual Studio 中，選取**偵錯** > **其他偵錯目標** > **偵錯 Installed App Package**。

1. 在**偵錯 Installed App Package**  對話方塊底下**連線類型**，選取**本機電腦**。

1. 底下**已安裝的應用程式套件**、 選取您想要偵錯的應用程式，或在搜尋方塊中輸入其名稱。 非執行安裝的應用程式套件，會顯示下**未執行**，並執行應用程式正在**執行**。

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. 如有必要，變更  下的程式碼類型**偵錯此程式碼類型**，然後選取 其他選項。
   - 選取 **不啟動，但啟動時，將我的程式碼進行偵錯**開始偵錯應用程式啟動。 開始偵錯時啟動應用程式是偵錯中的控制路徑的有效辦法[不同的啟動方法](/windows/uwp/xbox-apps/automate-launching-uwp-apps)，例如，使用自訂參數的通訊協定啟用。

1. 選取 **開始**，或如果應用程式正在執行中，選取**附加**。

> [!NOTE]
> 您也可以附加至任何執行的 UWP 或其他應用程式的程序選取**偵錯** > **附加至處理序**Visual Studio 中。 您不需要原始的 Visual Studio 專案，將附加至執行中處理序，但載入應用程式的符號將有助於大幅進行偵錯的處理程序，您不需要的原始程式碼時。 請參閱[偵錯工具中指定符號和原始程式檔](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

## <a name="remote"></a> 偵錯在遠端電腦或裝置上的已安裝的 UWP 應用程式

第一次 Visual Studio 偵錯已安裝的 UWP 應用程式在 Windows 10 裝置上遠端 post-Creator's Update Windows 10 電腦，它會在目標裝置上安裝遠端偵錯工具。

1. [啟用開發人員模式](/windows/uwp/get-started/enable-your-device-for-development)Visual Studio 電腦和遠端裝置或電腦上。

1. 如果您要連接到遠端電腦執行前 Creator's Update Windows 10、windows[手動安裝並啟動遠端偵錯工具](../debugger/remote-debugging.md)遠端電腦上。

1. 在 Visual Studio 電腦上，選取**偵錯** > **其他偵錯目標** > **偵錯 Installed App Package**。

1. 中**偵錯 Installed App Package**  對話方塊底下**連線類型**，選取**遠端機器**或**裝置**。

   如果您選取**裝置**，您的電腦必須實際連線到 Windows 10 裝置。

   如果電腦位址不旁邊會出現在遠端電腦**地址**，選取**變更**。

   1. 在 **遠端連線** 對話方塊中的 下一步**位址**，輸入名稱或您想要連接到電腦的 IP 位址。

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      如果偵錯工具無法連線到遠端電腦使用的電腦名稱，請改為使用的 IP 位址。 使用 Xbox、 HoloLens、 或 IoT 裝置的 IP 位址。
   1. 選取驗證選項旁**驗證模式**。

      對於大多數的應用程式，請保留預設值，**通用 （未加密的通訊協定）**。
   1. 選取 **選取**。

1. 底下**已安裝的應用程式套件**、 選取您想要偵錯的應用程式，或在搜尋方塊中輸入其名稱。 非執行安裝的應用程式套件，會顯示下**未執行**，並執行應用程式正在**執行**。

1. 如有必要，變更  下的程式碼類型**偵錯此程式碼類型**，然後選取 其他選項。
   - 選取 **不啟動，但啟動時，將我的程式碼進行偵錯**開始偵錯應用程式啟動。 開始偵錯時啟動應用程式是偵錯中的控制路徑的有效辦法[不同的啟動方法](/windows/uwp/xbox-apps/automate-launching-uwp-apps)，例如，使用自訂參數的通訊協定啟用。

1. 選取 **開始**，或如果應用程式正在執行中，選取**附加**。

當您開始第一次的已連接 Xbox、 HoloLens、 或 IoT 裝置上已安裝的應用程式套件偵錯時，Visual Studio 會安裝正確版本的目標裝置的遠端偵錯工具。 安裝遠端偵錯工具可能需要一些時間和訊息**啟動遠端偵錯工具**它發生時，會顯示。

>[!NOTE]
>目前，Xbox 或 HoloLens 裝置重新啟動應用程式偵錯工具附加，如果它正在執行。

如需有關遠端部署的 UWP 應用程式的詳細資訊，請參閱[部署和偵錯的 UWP 應用程式](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)並[偵錯的 UWP 應用程式，在遠端電腦上](run-windows-store-apps-on-a-remote-machine.md)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 偵錯](../debugger/index.md)
- [偵錯工具功能導覽](../debugger/debugger-feature-tour.md)
- [遠端偵錯](../debugger/remote-debugging.md)
- [設定 Windows 防火牆以進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)