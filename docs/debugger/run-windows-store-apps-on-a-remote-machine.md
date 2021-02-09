---
title: 在遠端電腦上進行 UWP 應用程式的偵錯工具 |Microsoft Docs
description: 請參閱如何使用 Visual Studio 在另一部電腦或裝置上遠端執行、偵測、分析和測試通用 Windows 平臺 (UWP) 應用程式。
ms.custom: SEO-VS-2020
ms.date: 10/05/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: f75c1c2420a356a38148f67daab05eadf5a073e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881317"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>從 Visual Studio 在遠端電腦上進行 UWP 應用程式的偵錯工具

您可以使用 Visual Studio，在另一部電腦或裝置上執行、偵測、分析通用 Windows 平臺 (UWP) 應用程式，並進行測試。 當 Visual Studio 電腦不支援觸控、地理位置或實體方向等 UWP 特定功能時，在遠端電腦上執行 UWP 應用程式特別有用。

## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> 必要條件

若要從 Visual Studio 在遠端裝置上進行 UWP 應用程式的偵錯工具：

- Visual Studio 專案必須設定為進行遠端偵錯程式。
- 遠端電腦和 Visual Studio 電腦必須透過網路連接，或直接透過 USB 或乙太網路纜線連接。 不支援透過網際網路偵錯。
- 您必須開啟 Visual Studio 電腦和遠端電腦上的 [開發人員模式](/windows/uwp/get-started/enable-your-device-for-development) 。
- 遠端電腦必須正在執行 Visual Studio 遠端工具。
  - 某些 Windows 10 版本會自動啟動並執行遠端工具。 否則，請 [安裝並執行 Visual Studio 遠端工具](#BKMK_download)。
  - Windows Mobile 10 裝置不需要或支援遠端工具。

## <a name="configure-a-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a> 設定遠端偵錯程式的 Visual Studio 專案
<a name="BKMK_DirectConnect"></a> 您可以使用專案 **屬性** 來指定要連接的遠端裝置。 這些設定會因程式設計語言而有所不同。

> [!CAUTION]
> 根據預設，屬性頁會將 **通用 (未加密的通訊協定)** 設定為 Windows 10 遠端連線的 **驗證類型** 。 您可能需要設定 [ **無驗證** ]，以連線到遠端偵錯程式。 **通用 (未加密的通訊協定)** ，而且 **沒有任何驗證** 通訊協定沒有網路安全性，因此在開發和遠端電腦之間傳遞的資料很容易受到攻擊。 請僅針對您確定不具有惡意或惡意流量風險的受信任網路，選擇這些驗證類型。
>
>如果您選擇 [ **Windows 驗證** ] 做為 **驗證類型**，則必須在進行調試時登入遠端電腦。 遠端偵錯程式也必須在 **Windows 驗證** 模式下執行，與 Visual Studio 電腦上的使用者帳戶相同。

### <a name="configure-a-c-or-visual-basic-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> 設定遠端偵錯程式的 c # 或 Visual Basic 專案

1. 選取 Visual Studio **方案總管** 中的 c # 或 Visual Basic 專案，然後選取 [**屬性**] 圖示，按下 **Alt** + **鍵**，或按一下滑鼠右鍵並選擇 [**屬性**]。

1. 選取 [偵錯] 索引標籤。

1. 在 [ **目標裝置**] 底下，選取遠端電腦的 **遠端** 電腦，或是直接連接之 Windows Mobile 10 裝置的 [ **裝置** ]。

1. 若為遠端電腦，請在 [**遠端電腦**] 欄位中輸入網路名稱或 IP 位址，或在 [[遠端連線] 對話方塊](#remote-connections)中選取 [**尋找**] 來搜尋裝置。

    ![用於遠端偵錯的 Managed 專案屬性](../debugger/media/vsrun_managed_projprop_remote.png "Managed Debug 專案屬性")

### <a name="configure-a-c-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> 設定遠端偵錯程式的 c + + 專案

1. 選取 Visual Studio **方案總管** 中的 c + + 專案，然後選取 [**屬性**] 圖示，按下 **Alt** + **鍵**，或按一下滑鼠右鍵並選擇 [**屬性**]。

1. 選取 [ **調試** ] 索引標籤。

3. 在 **[要啟動的偵錯工具**] 底下，選取遠端電腦的 **遠端** 電腦，或是直接連接之 Windows Mobile 10 裝置的 [ **裝置** ]。

1. 若為遠端電腦，請在 [**電腦名稱稱**] 欄位中輸入或選取網路名稱或 IP 位址，或在 [[遠端連線] 對話方塊](#remote-connections)中選取 [**尋找**] 以搜尋裝置。

    ![用於遠端偵錯的 C++ 專案屬性](../debugger/media/vsrun_cpp_projprop_remote.png "C + + 調試專案屬性")

### <a name="use-the-remote-connections-dialog-box"></a><a name="remote-connections"></a> 使用 [遠端連線] 對話方塊

在 [ **遠端** 連線] 對話方塊中，您可以搜尋特定的遠端電腦名稱稱或 IP 位址，或選取向下箭號的重新整理圖示來自動偵測連接。 此對話方塊只會搜尋目前正在執行遠端偵錯程式之本機子網上的裝置。 並非所有裝置都可以在 [ **遠端連線** ] 對話方塊中偵測到。

 ![遠端連線對話方塊](../debugger/media/vsrun_selectremotedebuggerdlg.png "遠端連線對話方塊")

>[!TIP]
>如果您無法依名稱連接到遠端裝置，請嘗試使用其 IP 位址。 若要判斷 IP 位址，請在遠端裝置上的命令視窗中輸入 **ipconfig** 。 IP 位址會顯示為 **IPv4 位址**。

## <a name="download-and-install-the-remote-tools-for-visual-studio"></a><a name="BKMK_download"></a> 下載並安裝 Visual Studio 遠端工具

若要讓 Visual Studio 在遠端電腦上進行應用程式的偵錯工具，遠端電腦必須執行 Visual Studio 遠端工具。

- Windows Mobile 10 裝置不需要或支援遠端工具。
- Windows 10 電腦執行建立者的更新 (1703 版) 和更新版本，Windows 10 Xbox、IoT 和 HoloLens 裝置會在您部署應用程式時自動安裝遠端工具。
- 在預先建立者的更新 Windows 10 電腦上，您必須先手動下載、安裝及執行遠端電腦上的遠端工具，再開始進行偵錯工具。

**若要下載並安裝遠端工具：**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="configure-the-remote-tools"></a><a name="BKMK_setup"></a> 設定遠端工具

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="debug-uwp-apps-remotely"></a><a name="BKMK_RunRemoteDebug"></a> 遠端偵錯程式的 UWP 應用程式

遠端偵錯的運作方式與本機調試一樣。

1. 在 Windows 10 的預先建立者更新版本上，請確定遠端偵錯監視 (*msvsmon.exe*) 正在遠端裝置上執行。

1. 在 Visual Studio 電腦上，請確定工具列上的綠色箭號旁邊會出現正確的調試目標 (**遠端電腦** 或 **裝置**) 。

1. 選取 [ **Debug**  >  **開始調試** 程式]、按 **F5**，或選取工具列上的綠色箭號，以開始進行偵錯工具。

   專案會重新編譯，然後在遠端裝置上部署和啟動。 偵錯工具會在中斷點暫停執行，而且您可以逐步執行、程式碼和程式碼。

1. 如有必要，請選取 [**調試**  >  程式 **停止**]，或按 **Shift** + **F5** 以停止偵錯工具並關閉遠端應用程式。

## <a name="see-also"></a>另請參閱
- [進階遠端部署選項](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [使用 Visual Studio 測試 UWP 應用程式](../test/unit-test-your-code.md)
- [在 Visual Studio 中對 UWP App 進行偵錯](debugging-windows-store-and-windows-universal-apps.md)
