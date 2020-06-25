---
title: 在遠端電腦上對 UWP 應用程式進行調試 |Microsoft Docs
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
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 3d208c59f08ddeb5a322d174a2c6b56dd901c2c4
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348115"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>在遠端電腦上從 Visual Studio 中偵測 UWP 應用程式

您可以使用 Visual Studio，在另一部電腦或裝置上執行、偵測、分析和測試通用 Windows 平臺（UWP）應用程式。 當 Visual Studio 電腦不支援觸控、地理位置或實體方向等 UWP 特有的功能時，在遠端電腦上執行 UWP 應用程式特別有用。

## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> 必要條件

若要在遠端裝置上從 Visual Studio 中偵測 UWP 應用程式：

- Visual Studio 專案必須設定為進行遠端偵錯程式。
- 遠端電腦和 Visual Studio 電腦必須透過網路連接，或直接透過 USB 或 Ethernet 纜線連接。 不支援透過網際網路偵錯。
- 您必須在 Visual Studio 電腦和遠端電腦上[開啟開發人員模式](/windows/uwp/get-started/enable-your-device-for-development)。
- 遠端電腦必須執行 Visual Studio 遠端工具。
  - 有些 Windows 10 版本會自動啟動並執行遠端工具。 否則，請[安裝並執行 Visual Studio 遠端工具](#BKMK_download)。
  - Windows Mobile 10 裝置不需要或不支援遠端工具。

## <a name="configure-a-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a>設定遠端偵錯程式的 Visual Studio 專案
<a name="BKMK_DirectConnect"></a>您可以使用專案**屬性**來指定要連接的遠端裝置。 這些設定會因程式設計語言而有所不同。

> [!CAUTION]
> 根據預設，屬性頁會將**通用（未加密的通訊協定）** 設定為 Windows 10 遠端連線的**驗證類型**。 您可能需要設定 [**無驗證**]，才能連接到遠端偵錯程式。 **通用（未加密的通訊協定）** 和**沒有驗證**通訊協定沒有網路安全性，因此在開發與遠端機器之間傳遞的資料會很容易受到攻擊。 僅針對您確定不具有惡意或惡意流量風險的信任網路，選擇這些驗證類型。
>
>如果您選擇 [ **Windows 驗證**] 作為 [**驗證類型**]，則必須在進行偵錯工具時登入遠端電腦。 遠端偵錯程式也必須在**Windows 驗證**模式下執行，與 Visual Studio 機上的使用者帳戶相同。

### <a name="configure-a-c-or-visual-basic-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a>設定遠端偵錯程式的 c # 或 Visual Basic 專案

1. 在 Visual Studio**方案總管**中選取 c # 或 Visual Basic 專案，然後選取 [**屬性**] 圖示，按**Alt** + **enter**鍵，或按一下滑鼠右鍵並選擇 [**屬性**]。

1. 選取 [偵錯]**** 索引標籤。

1. 在 [**目標裝置**] 下，選取遠端電腦的**遠端電腦**，或直接連線的 Windows Mobile 10 裝置的**裝置**。

1. 若為遠端電腦，請在 [**遠端電腦**] 欄位中輸入網路名稱或 IP 位址，或選取 [**尋找**] 在 [[遠端連線] 對話方塊](#remote-connections)中搜尋該裝置。

    ![用於遠端偵錯的 Managed 專案屬性](../debugger/media/vsrun_managed_projprop_remote.png "受控的 Debug 專案屬性")

### <a name="configure-a-c-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a>設定遠端偵錯程式的 c + + 專案

1. 選取 Visual Studio**方案總管**中的 c + + 專案，然後選取 [**屬性**] 圖示，按**Alt** + **enter**鍵，或按一下滑鼠右鍵並選擇 [**屬性**]。

1. 選取 [**調試**] 索引標籤。

3. 在 **[要啟動的偵錯工具**] 下，針對 [遠端電腦] 選取 [**遠端電腦**]，或針對直接連線的 Windows Mobile 10 裝置選取 [**裝置**]。

1. 若為遠端電腦，請在 [**電腦名稱稱**] 欄位中輸入或選取網路名稱或 IP 位址，或按一下下拉式方塊，然後選取 [**尋找**] 在 [[遠端連線] 對話方塊](#remote-connections)中搜尋該裝置。

    ![用於遠端偵錯的 C++ 專案屬性](../debugger/media/vsrun_cpp_projprop_remote.png "C + + 調試專案屬性")

### <a name="use-the-remote-connections-dialog-box"></a><a name="remote-connections"></a>使用 [遠端連線] 對話方塊

在 [**遠端**連線] 對話方塊中，您可以藉由選取 [四捨五入-箭號重新整理] 圖示，來搜尋特定的遠端電腦名稱稱或 IP 位址，或自動偵測連接。 對話方塊只會搜尋目前正在執行遠端偵錯程式之本機子網上的裝置。 並非所有裝置都可以在 [**遠端連線**] 對話方塊中偵測到。

 ![[遠端連線] 對話方塊](../debugger/media/vsrun_selectremotedebuggerdlg.png "[遠端連線] 對話方塊")

>[!TIP]
>如果您無法依名稱連接到遠端裝置，請嘗試使用其 IP 位址。 若要判斷 IP 位址，請在遠端裝置上的命令視窗中輸入**ipconfig** 。 IP 位址會顯示為**IPv4 位址**。

## <a name="download-and-install-the-remote-tools-for-visual-studio"></a><a name="BKMK_download"></a> 下載並安裝 Visual Studio 遠端工具

若要 Visual Studio 來對遠端電腦上的應用程式進行偵錯工具，遠端電腦必須執行 Visual Studio 遠端工具。

- Windows Mobile 10 裝置不需要或不支援遠端工具。
- 執行建立者更新（版本1703）和更新版本、Windows 10 Xbox、IoT 和 HoloLens 裝置的 windows 10 電腦，會在您部署應用程式時自動安裝遠端工具。
- 在預先建立者的更新 Windows 10 電腦上，您必須先手動下載、安裝及執行遠端電腦上的遠端工具，然後再開始進行偵錯工具。

**若要下載並安裝遠端工具：**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="configure-the-remote-tools"></a><a name="BKMK_setup"></a>設定遠端工具

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="debug-uwp-apps-remotely"></a><a name="BKMK_RunRemoteDebug"></a>從遠端對 UWP 應用程式進行調試

遠端偵錯功能的運作方式與本機調試相同。

1. 在預先建立者的 Windows 10 更新版本上，請確定遠端偵錯監視（*msvsmon.exe*）正在遠端裝置上執行。

1. 在 Visual Studio 電腦上，請確定工具列上的綠色箭號旁出現正確的 [調試目標] （**遠端電腦**或**裝置**）。

1. 選取 [**調試**程式]  >  [**開始**] [調試]、按**F5**，或選取工具列上的綠色箭號，以開始進行調試。

   專案會重新編譯，然後在遠端裝置上部署和啟動。 偵錯工具會在中斷點暫停執行，而您可以逐步執行、跳過和跳出程式碼。

1. 如有需要，請選取 [ **Debug**] [停止偵測]，  >  **Stop Debugging**或按**Shift** + **F5**停止偵錯工具並關閉遠端應用程式。

## <a name="see-also"></a>另請參閱
- [進階遠端部署選項](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [使用 Visual Studio 測試 UWP 應用程式](/visualstudio/test/create-and-run-unit-tests-for-a-store-app-in-visual-studio/)
- [在 Visual Studio 中對 UWP App 進行偵錯](debugging-windows-store-and-windows-universal-apps.md)
