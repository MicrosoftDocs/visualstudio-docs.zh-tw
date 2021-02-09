---
title: 將已安裝的 UWP 應用程式套件進行偵錯工具 |Microsoft Docs
description: 在 Windows 10 電腦、Xbox 和物聯網 (IoT) 裝置的 Visual Studio 中，將已安裝的通用 Windows 平臺 (UWP) 應用程式套件。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: e77d74e0d7d0094918ecbd4e86cdfe5d15e511bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857515"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>在 Visual Studio 中將已安裝的 UWP 應用程式套件進行 Debug 錯

Visual Studio 可以在 Windows 10 電腦、Xbox、HoloLens 和 IoT 裝置上，將安裝的通用 Windows 平臺 (UWP) 應用程式套件。

>[!NOTE]
>手機不支援已安裝 UWP 應用程式的 Visual Studio 偵錯工具。

如需有關如何偵測 UWP 應用程式的詳細資訊，請參閱有關將 [已安裝的應用程式套件](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) 和 [組建通用 Windows 應用程式 (UWP) ](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/)的 blog 文章。

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>在本機電腦上將已安裝的 UWP 應用程式進行偵錯工具

1. 在 Visual Studio 中，選取 [**調試** 程式] 會偵測  >    >  **已安裝的應用程式套件**。

1. 在 [偵測 **已安裝的應用程式套件** ] 對話方塊的 [連線 **類型**] 底下，選取 [ **本機電腦**]。

1. 在 [ **已安裝的應用程式套件**] 下，選取您要進行偵錯工具的應用程式，或在 [搜尋] 方塊中輸入其名稱。 **未** 執行的已安裝應用程式套件會出現在 [未執行] 下，而且 **執行中的** 應用程式正在執行中。

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. 如有必要，請在 [ **Debug this code type**] 下變更程式碼類型，然後選取 [其他選項]。
   - 當應用程式啟動時，請選取 [ **不啟動，但在我的程式碼啟動** 時開始進行偵錯工具]。 當應用程式啟動時開始偵錯工具，是從 [不同的啟動方法](/windows/uwp/xbox-apps/automate-launching-uwp-apps)（例如使用自訂參數啟動通訊協定），對控制路徑進行自訂的有效方式。

1. 選取 [ **開始**]，或如果應用程式正在執行，請選取 [ **附加**]。

> [!NOTE]
> 您也可以在 Visual Studio 中選取 [ **Debug**  >  **附加至進程**]，以附加至任何執行中的 UWP 或其他應用程式進程。 您不需要將原始 Visual Studio 專案附加到執行中的進程，但是在對您沒有原始程式碼的程式進行偵錯工具時，載入應用程式的符號將會有很大的説明。 請參閱 [在偵錯工具中指定符號和原始程式](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)檔。

## <a name="debug-an-installed-uwp-app-on-a-remote-computer-or-device"></a><a name="remote"></a> 在遠端電腦或裝置上進行已安裝的 UWP 應用程式的偵錯工具

第一次 Visual Studio 在 Windows 10 裝置上或遠端建立者的更新 Windows 10 電腦上，將已安裝的 UWP 應用程式進行偵錯工具時，它會在目標裝置上安裝遠端偵錯程式。

1. 在 Visual Studio 電腦和遠端裝置或電腦上[啟用開發人員模式](/windows/uwp/get-started/enable-your-device-for-development)。

1. 如果您要連線到執行預先建立者更新 Windows 10 的遠端電腦，請在遠端電腦上 [手動安裝並啟動遠端偵錯程式](../debugger/remote-debugging.md) 。

1. 在 Visual Studio 電腦上，選取 [**調試**  >    >  **程式] 已安裝的應用程式封裝** 的 [偵錯工具]。

1. 在 [偵測 **已安裝的應用程式套件** ] 對話方塊的 [連線 **類型**] 底下，選取 [ **遠端電腦** 或 **裝置**]。

   如果您選取 [ **裝置**]，則電腦必須實際連接到 Windows 10 裝置。

   若是遠端電腦，如果 [ **位址**] 旁沒有出現 [電腦位址]，請選取 [ **變更**]。

   1. 在 [ **遠端** 連線] 對話方塊的 [ **位址**] 旁，輸入您要連接之電腦的名稱或 IP 位址。

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      如果偵錯工具無法使用電腦名稱稱連接到遠端電腦，請改為使用 IP 位址。 使用 Xbox、HoloLens 或 IoT 裝置的 IP 位址。
   1. 選取 **驗證模式** 旁的驗證選項。

      針對大部分的應用程式，保留預設值，即 **通用 (未加密的通訊協定)**。
   1. 選取 [選取]  。

1. 在 [ **已安裝的應用程式套件**] 下，選取您要進行偵錯工具的應用程式，或在 [搜尋] 方塊中輸入其名稱。 **未** 執行的已安裝應用程式套件會出現在 [未執行] 下，而且 **執行中的** 應用程式正在執行中。

1. 如有必要，請在 [ **Debug this code type**] 下變更程式碼類型，然後選取 [其他選項]。
   - 當應用程式啟動時，請選取 [ **不啟動，但在我的程式碼啟動** 時開始進行偵錯工具]。 當應用程式啟動時開始偵錯工具，是從 [不同的啟動方法](/windows/uwp/xbox-apps/automate-launching-uwp-apps)（例如使用自訂參數啟動通訊協定），對控制路徑進行自訂的有效方式。

1. 選取 [ **開始**]，或如果應用程式正在執行，請選取 [ **附加**]。

當您第一次在連線的 Xbox、HoloLens 或 IoT 裝置上開始對已安裝的應用程式套件進行第一次偵錯工具時，Visual Studio 為您的目標裝置安裝正確的遠端偵錯程式版本。 安裝遠端偵錯程式可能需要一些時間，而 **啟動遠端偵錯程式** 的訊息會在發生時顯示。

>[!NOTE]
>目前，Xbox 或 HoloLens 裝置會在已執行的偵錯工具已連接的情況下重新開機應用程式。

如需 UWP 應用程式遠端部署的詳細資訊，請參閱在遠端電腦上 [部署和偵測 uwp 應用](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) 程式，以及 [對 uwp 應用程式進行偵錯工具](run-windows-store-apps-on-a-remote-machine.md)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 偵錯](../debugger/index.yml)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [遠端偵錯](../debugger/remote-debugging.md)
- [設定 Windows 防火牆以進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)