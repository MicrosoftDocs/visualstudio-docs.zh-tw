---
title: Debug 已安裝的 UWP 應用程式套件 |Microsoft Docs
ms.custom: ''
ms.date: 11/07/2018
ms.topic: how-to
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
ms.openlocfilehash: eabc694665bede7d193a360a01c42366568e33c5
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350728"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>在 Visual Studio 中，對已安裝的 UWP 應用程式套件進行 Debug

Visual Studio 可以在 Windows 10 電腦和 Xbox、HoloLens 和 IoT 裝置上，對已安裝的通用 Windows 平臺（UWP）應用程式套件進行 debug。

>[!NOTE]
>手機不支援已安裝 UWP 應用程式的 Visual Studio 偵測。

如需有關偵測 UWP 應用程式的詳細資訊，請參閱有關偵測[已安裝的應用程式套件](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/)和[建立通用 Windows 應用程式（UWP）](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/)的 blog 文章。

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>在本機電腦上對已安裝的 UWP 應用程式進行 Debug

1. 在 Visual Studio 中，**選取 [** 偵測] [  >  **其他 debug 目標**] [偵測  >  **已安裝應用程式套件**]

1. 在 [**已安裝的應用程式套件**] 對話方塊的 [連線**類型**] 底下，選取 [**本機電腦**]。

1. 在 [**已安裝的應用程式套件**] 底下，選取您要進行 debug 的應用程式，或在 [搜尋] 方塊中輸入其名稱。 **未**執行的已安裝應用程式套件出現在 [未執行] 之下，且**執行中的**應用程式正在執行中。

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. 如有必要，請在 [**偵錯工具代碼類型**] 底下變更程式碼類型，然後選取 [其他選項]。
   - 選取 [**不啟動，但在我的程式碼啟動**時進行調試]，以在應用程式啟動時開始進行偵錯工具。 開始在應用程式啟動時進行的偵測是一種有效的方法，可讓您從[不同的啟動方法](/windows/uwp/xbox-apps/automate-launching-uwp-apps)（例如使用自訂參數的通訊協定啟用）來進行控制

1. 選取 [**開始**]，或如果應用程式正在執行，請選取 [**附加**]。

> [!NOTE]
> 您也可以在 Visual Studio 中選取 [**調試**程式] [  >  **附加至進程**]，以附加至任何執行中的 UWP 或其他應用程式進程。 您不需要原始的 Visual Studio 專案，即可附加至執行中的進程，但在對您沒有原始程式碼的進程進行處理時，載入應用程式的符號會有很大的説明。 請參閱[在偵錯工具中指定符號和來源](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)檔案。

## <a name="debug-an-installed-uwp-app-on-a-remote-computer-or-device"></a><a name="remote"></a>在遠端電腦或裝置上對已安裝的 UWP 應用程式進行 Debug

第一次 Visual Studio 在 Windows 10 裝置上或遠端建立後的 windows 10 電腦上，將已安裝的 UWP 應用程式進行調試，它會在目標裝置上安裝遠端偵錯程式。

1. 在 Visual Studio 電腦和遠端裝置或電腦上[啟用開發人員模式](/windows/uwp/get-started/enable-your-device-for-development)。

1. 如果您要連線到執行建立者更新 Windows 10 的遠端電腦，請在遠端電腦上[手動安裝並啟動遠端偵錯程式](../debugger/remote-debugging.md)。

1. 在 Visual Studio 電腦上 **，選取 [** 偵測] [  >  **其他 debug 目標**] [偵測  >  **已安裝應用程式套件**]。

1. 在 [**已安裝的應用程式套件**] 對話方塊的 [連線**類型**] 底下，選取 [**遠端電腦**或**裝置**]。

   如果您選取 [**裝置**]，您的電腦必須實際連線到 Windows 10 裝置。

   若為遠端電腦，如果 [**位址**] 旁沒有顯示電腦位址，請選取 [**變更**]。

   1. 在 [**遠端**連線] 對話方塊的 [**位址**] 旁，輸入您要連接之電腦的名稱或 IP 位址。

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      如果偵錯工具無法使用電腦名稱稱連接到遠端電腦，請改用 IP 位址。 使用 Xbox、HoloLens 或 IoT 裝置的 IP 位址。
   1. 選取 [**驗證模式**] 旁的驗證選項。

      針對大部分的應用程式，保留預設值 [**通用（未加密的通訊協定）**]。
   1. 選取 [選取] 。

1. 在 [**已安裝的應用程式套件**] 底下，選取您要進行 debug 的應用程式，或在 [搜尋] 方塊中輸入其名稱。 **未**執行的已安裝應用程式套件出現在 [未執行] 之下，且**執行中的**應用程式正在執行中。

1. 如有必要，請在 [**偵錯工具代碼類型**] 底下變更程式碼類型，然後選取 [其他選項]。
   - 選取 [**不啟動，但在我的程式碼啟動**時進行調試]，以在應用程式啟動時開始進行偵錯工具。 開始在應用程式啟動時進行的偵測是一種有效的方法，可讓您從[不同的啟動方法](/windows/uwp/xbox-apps/automate-launching-uwp-apps)（例如使用自訂參數的通訊協定啟用）來進行控制

1. 選取 [**開始**]，或如果應用程式正在執行，請選取 [**附加**]。

當您第一次在已連線的 Xbox、HoloLens 或 IoT 裝置上開始對已安裝的應用程式套件進行偵測時，Visual Studio 會為目標裝置安裝正確的遠端偵錯程式版本。 安裝遠端偵錯程式可能需要一些時間，而且**啟動遠端偵錯程式**的訊息會在發生時顯示。

>[!NOTE]
>目前，如果應用程式已在執行中，則 Xbox 或 HoloLens 裝置會重新開機已附加偵錯工具。

如需有關遠端部署 UWP 應用程式的詳細資訊，請參閱[在遠端電腦上](run-windows-store-apps-on-a-remote-machine.md)[部署和偵測 uwp 應用程式](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)和檢查 uwp 應用程式。

## <a name="see-also"></a>另請參閱

- [Visual Studio 偵錯](../debugger/index.yml)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [遠端偵錯](../debugger/remote-debugging.md)
- [設定 Windows 防火牆以進行遠端偵錯程式](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)