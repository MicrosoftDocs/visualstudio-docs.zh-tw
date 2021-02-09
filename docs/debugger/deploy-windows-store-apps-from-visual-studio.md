---
title: 部署 UWP 應用程式 |Microsoft Docs
description: 從 Visual Studio 部署通用 Windows 平臺 (UWP) 應用程式。 指定要部署的本機或遠端目標裝置。 瞭解部署選項。
ms.custom: SEO-VS-2020, seodec18
ms.date: 01/16/2018
ms.topic: conceptual
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
ms.openlocfilehash: 6d8819f92e19960aefc7e485acb2fb7fa827b6ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872166"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>從 Visual Studio 部署 UWP 應用程式

Visual Studio 部署功能會建立並註冊在目標裝置上使用 Visual Studio 所建立的 UWP 應用程式。 應用程式的確切註冊方式取決於目標裝置是本機還是遠端：

- 目標是本機 Visual Studio 電腦時，Visual Studio 會從其組建資料夾中註冊應用程式。

- 目標是遠端裝置時，Visual Studio 會將必要檔案複製至遠端電腦，並在該裝置上註冊應用程式。

當您使用下列選項從 Visual Studio 偵錯應用程式時，會自動進行部署：[開始偵錯] 選項 (快速鍵：F5) 或 [啟動但不偵錯] 選項 (快速鍵：CTRL + F5)。 您也可以手動部署應用程式。 手動部署適用於下列情況：

- 本機或遠端電腦上進行臨機操作測試。

- 部署將啟動另一個您要偵錯之應用程式的應用程式。

- 部署應用程式，以另一個應用程式或另一種方法啟動該應用程式時，對其進行偵錯。

## <a name="how-to-deploy-a-uwp-app"></a><a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> 如何部署 UWP 應用程式
 手動部署應用程式是一個簡單的流程：

1. 如果您部署至遠端裝置，請在應用程式啟始專案的屬性專案頁面中指定裝置的名稱或 IP 位址。 (本主題會進一步列出這項作業的步驟)。

2. 在偵錯工具 Visual Studio 工具列上，從 [開始偵錯]  按鈕旁邊的下拉式清單中選擇部署目標。

     ![執行於本機電腦](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3. 在 [建置]  功能表上，選擇 [部署] 

## <a name="how-to-specify-a-remote-device"></a><a name="BKMK_How_to_specify_a_remote_device"></a> 如何指定遠端裝置

**先決條件**

在 Windows 10 遠端裝置上，您必須啟用 [開發人員模式](/windows/uwp/get-started/enable-your-device-for-development)。 在執行 Creator 更新或更新版本的 Windows 10 裝置上，當您部署應用程式時，會自動安裝遠端工具。 如需詳細資訊，請參閱 [Debug 已安裝的應用程式套件](../debugger/debug-installed-app-package.md)。

> [!NOTE]
> 在 Windows 10 的預先建立者更新版本上，必須在遠端裝置上安裝 Visual Studio 遠端工具，而且必須執行遠端偵錯程式。

部署使用遠端偵錯工具網路通道，將應用程式檔案傳送至遠端裝置。

#### <a name="to-specify-a-remote-device"></a>指定遠端裝置

1. 在啟始專案的 [偵錯] 屬性頁上，指定遠端部署目標的名稱或 IP 位址。

2. 若要開啟 [偵錯] 屬性頁，請在 [方案總管] 中選擇專案，然後從捷徑功能表中選擇 [屬性]  。

3. 然後選擇屬性頁視窗上的 [偵錯]  節點。

4. 針對 [ **目標裝置**]，選取 [ **遠端電腦**]。

5. 在 [ **遠端電腦**] 底下，按一下 [ **尋找**]。

6. 您可以輸入遠端裝置的名稱或 IP 位址，也可以從 [ **遠端連線** ] 對話方塊中選擇裝置。

    ![[選取遠端偵錯工具連接] 對話方塊](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    [ **遠端** 連線] 對話方塊會顯示區域網路子網上的裝置，以及透過乙太網路纜線直接連線到 Visual Studio 電腦的任何裝置。

   **在 c + + 專案頁面中指定遠端裝置**

   ![遠端偵錯程式的 C&#43;&#43; 專案屬性](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. 從 [ **要啟動的偵錯工具** ] 清單選擇 [ **遠端偵錯工具** ]。

8. 在 [電腦名稱]  方塊中，輸入遠端裝置的網路名稱。 或者，您可以選擇方塊中的向下箭頭，以從 [選取遠端偵錯工具連接] 對話方塊中選取裝置。

   **在 Visual C# 和 Visual Basic 專案頁面中指定遠端裝置**

   ![用於遠端偵錯的 Managed 專案屬性](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. 從 [ **目標裝置** ] 清單選擇 [ **遠端電腦** ]。

10. 在 [ **遠端電腦** ] 方塊中輸入遠端裝置的網路名稱，或按一下 [ **尋找** ]，從 [ **選取遠端偵錯工具連接** ] 對話方塊選擇裝置。

## <a name="deployment-options"></a><a name="BKMK_Deployment_options"></a> 部署選項

您可以在啟始專案的 [偵錯] 屬性頁上設定下列部署選項。

**允許網路回送**

基於安全性考慮， [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 不允許以標準方式安裝的 UWP 或應用程式對其安裝所在的裝置進行網路呼叫。 根據預設，Visual Studio 部署會從這個已部署的應用程式規則建立免套用原則。 這個免套用原則可讓您在單一電腦上測試通訊程序。 在將您的應用程式提交至 [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]之前，您應該在沒有豁免的情況下測試您的應用程式。

從 App 移除網路回送豁免：

- 在 [c #] 和 [Visual Basic Debug] 屬性頁上，清除 [ **允許網路回送** ] 核取方塊。

- 在 [c + + Debug] 屬性頁上，將 [ **允許網路回送** 值] 設定為 [ **否**]。

**請勿啟動，但會在程式碼啟動 (c # 和 Visual Basic) /啟動應用程式 (c + + 時進行偵錯工具)**

將部署設定成在啟動 App 時自動啟動偵錯工作階段：

- 在 [c #] 和 [Visual Basic Debug] 屬性頁上，核取 [ **不啟動，但在我的程式碼啟動時進行調試** ] 核取方塊。

- 在 [c + + Debug] 屬性頁上，將 [**啟動應用程式**] 值設定為 **[是]**

## <a name="see-also"></a>另請參閱

- [進階遠端部署選項](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [對已安裝的應用程式套件進行偵錯](../debugger/debug-installed-app-package.md)
- [從 Visual Studio 執行應用程式](debugging-windows-store-and-windows-universal-apps.md)
