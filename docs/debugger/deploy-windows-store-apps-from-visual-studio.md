---
title: 將 UWP 應用程式部署 |Microsoft Docs
ms.custom: seodec18
ms.date: 01/16/2018
ms.topic: conceptual
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
ms.openlocfilehash: 63726f9f38cdede6c8a0525b74244baac9455aad
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58790377"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>從 Visual Studio 部署 UWP 應用程式

Visual Studio 部署功能建置，並註冊的目標裝置使用 Visual Studio 所建立的 UWP 應用程式。 應用程式的確切註冊方式取決於目標裝置是本機還是遠端：

- 目標是本機 Visual Studio 電腦時，Visual Studio 會從其組建資料夾中註冊應用程式。

- 目標是遠端裝置時，Visual Studio 會將必要檔案複製至遠端電腦，並在該裝置上註冊應用程式。

當您使用偵錯您的應用程式，從 Visual Studio 部署便會自動**開始偵錯**選項 (鍵盤：F5) 或**啟動但不偵錯**選項 (鍵盤：CTRL + F5）。 您也可以手動部署應用程式。 手動部署適用於下列情況：

- 本機或遠端電腦上進行臨機操作測試。

- 部署將啟動另一個您要偵錯之應用程式的應用程式。

- 部署應用程式，以另一個應用程式或另一種方法啟動該應用程式時，對其進行偵錯。

##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> 如何將 UWP 應用程式部署
 手動部署應用程式是一個簡單的流程：

1.  如果您部署至遠端裝置，請在應用程式啟始專案的屬性專案頁面中指定裝置的名稱或 IP 位址。 (本主題會進一步列出這項作業的步驟)。

2.  在偵錯工具 Visual Studio 工具列上，從 [開始偵錯]  按鈕旁邊的下拉式清單中選擇部署目標。

     ![在本機電腦上執行](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3.  在 [建置]  功能表上，選擇 [部署] 

##  <a name="BKMK_How_to_specify_a_remote_device"></a> 如何指定遠端裝置

**必要條件**

在 Windows 10 的遠端裝置，您必須啟用[開發人員模式](/windows/uwp/get-started/enable-your-device-for-development)。 在執行 Creator's Update 的 Windows 10 裝置上安裝或更新版本，遠端工具會自動部署您的應用程式時。 如需詳細資訊，請參閱 <<c0> [ 偵錯已安裝的應用程式套件](../debugger/debug-installed-app-package.md)。

> [!NOTE]
> 在預先建立者更新版本的 Windows 10，適用於 Visual Studio 的遠端工具必須安裝在遠端裝置上，且遠端偵錯工具必須執行。

部署使用遠端偵錯工具網路通道，將應用程式檔案傳送至遠端裝置。

#### <a name="to-specify-a-remote-device"></a>指定遠端裝置

1. 在啟始專案的 [偵錯] 屬性頁上，指定遠端部署目標的名稱或 IP 位址。

2. 若要開啟 [偵錯] 屬性頁，請在 [方案總管] 中選擇專案，然後從捷徑功能表中選擇 [屬性]  。

3. 然後選擇屬性頁視窗上的 [偵錯]  節點。

4. 針對**目標裝置**，選取**遠端機器**。

5. 底下**遠端電腦**，按一下**尋找**。

6. 您可以輸入的名稱或 IP 位址的遠端裝置，或者您可以選擇將裝置從**遠端連線** 對話方塊。

    ![選取遠端偵錯工具連接 對話方塊](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    **遠端連線**對話方塊會顯示本機子網路和透過乙太網路纜線直接連接到 Visual Studio 電腦的任何裝置上的裝置。

   **在 視覺效果中指定遠端裝置C++專案頁面**

   ![C&#43; &#43;的專案進行遠端偵錯的屬性](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. 從 [ **要啟動的偵錯工具** ] 清單選擇 [ **遠端偵錯工具** ]。

8. 在 [電腦名稱]  方塊中，輸入遠端裝置的網路名稱。 或者，您可以選擇方塊中的向下箭頭，以從 [選取遠端偵錯工具連接] 對話方塊中選取裝置。

   **在 Visual C# 和 Visual Basic 專案頁面中指定遠端裝置**

   ![受管理的遠端偵錯專案屬性](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. 從 [ **目標裝置** ] 清單選擇 [ **遠端電腦** ]。

10. 在 [ **遠端電腦** ] 方塊中輸入遠端裝置的網路名稱，或按一下 [ **尋找** ]，從 [ **選取遠端偵錯工具連接** ] 對話方塊選擇裝置。

##  <a name="BKMK_Deployment_options"></a> 部署選項

您可以在啟始專案的 [偵錯] 屬性頁上設定下列部署選項。

**允許網路回送**

基於安全性理由，UWP 或[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]以標準方式安裝應用程式不允許進行到其安裝所在裝置的網路呼叫。 根據預設，Visual Studio 部署會針對部署應用程式建立此規則的豁免。 此豁免可讓您測試在單一機器上的通訊程序。 在將您的應用程式提交至 [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]之前，您應該在沒有豁免的情況下測試您的應用程式。

移除應用程式中的網路回送豁免：

- 在C#和 Visual Basic 偵錯 屬性頁面上，清除**允許網路 Loopback**核取方塊。

- 在C++偵錯屬性頁，設定**允許網路 Loopback**值**No**。

**不啟動，但啟動時，將我的程式碼進行偵錯 (C#和 Visual Basic) / 啟動應用程式 (C++)**

設定部署在應用程式啟動時自動啟動偵錯工作階段：

- 在C#和 Visual Basic 偵錯屬性頁上，檢查**不啟動，但啟動時，將我的程式碼進行偵錯**核取方塊。

- 在C++偵錯屬性頁，設定**啟動應用程式**值**是**。

## <a name="see-also"></a>另請參閱

- [進階遠端部署選項](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [對已安裝的應用程式套件進行偵錯](../debugger/debug-installed-app-package.md)
- [從 Visual Studio 執行應用程式](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)
