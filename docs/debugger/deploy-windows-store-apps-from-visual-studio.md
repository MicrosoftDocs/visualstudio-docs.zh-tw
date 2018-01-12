---
title: "從 Visual Studio 的 UWP 應用程式部署 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 95f009ca761d4d978fb5e5a9323722e5dfc34cb8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>部署 Visual Studio 從 UWP 應用程式
![僅適用於 Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Visual Studio 部署功能建置和註冊的目標裝置上使用 Visual Studio 所建立的 UWP 應用程式。 應用程式的確切註冊方式取決於目標裝置是本機還是遠端：  
  
-   目標是本機 Visual Studio 電腦時，Visual Studio 會從其組建資料夾中註冊應用程式。  
  
-   目標是遠端裝置時，Visual Studio 會將必要檔案複製至遠端電腦，並在該裝置上註冊應用程式。  
  
 會自動進行部署時使用偵錯您的應用程式，從 Visual Studio**開始偵錯**選項 (鍵盤： F5) 或**啟動但不偵錯**選項 (鍵盤： CTRL + F5)。 您也可以手動部署應用程式。 手動部署適用於下列情況：  
  
-   本機或遠端電腦上進行臨機操作測試。  
  
-   部署將啟動另一個您要偵錯之應用程式的應用程式。  
  
-   部署應用程式，以另一個應用程式或另一種方法啟動該應用程式時，對其進行偵錯。
  
##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a>如何部署 UWP 應用程式  
 手動部署應用程式是一個簡單的流程：  
  
1.  如果您部署至遠端裝置，請在應用程式啟始專案的屬性專案頁面中指定裝置的名稱或 IP 位址。 (本主題會進一步列出這項作業的步驟)。  
  
2.  在偵錯工具 Visual Studio 工具列上，從 [開始偵錯]  按鈕旁邊的下拉式清單中選擇部署目標。  
  
     ![在本機電腦上執行](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
3.  在 [建置]  功能表上，選擇 [部署]   
  
##  <a name="BKMK_How_to_specify_a_remote_device"></a> 如何指定遠端裝置  

**必要條件**  
  
在 Windows 10 的遠端裝置，您必須啟用[開發人員模式下](/windows/uwp/get-started/enable-your-device-for-development)。 在執行建立者的更新的 Windows 10 裝置上或更新版本中，遠端工具會自動安裝時部署您的應用程式。 如需詳細資訊，請參閱[偵錯已安裝的應用程式套件](../debugger/debug-installed-app-package.md)。

> [!NOTE]
> 在 Windows 8.1 和 Windows 10 的 pre-建立者的更新版本，適用於 Visual Studio 遠端工具必須安裝在遠端裝置上，必須執行遠端偵錯工具。 在 Windows 8.1，您也必須安裝開發人員授權。
  
部署使用遠端偵錯工具網路通道，將應用程式檔案傳送至遠端裝置。  
  
#### <a name="to-specify-a-remote-device"></a>指定遠端裝置  
  
1.  在啟始專案的 [偵錯] 屬性頁上，指定遠端部署目標的名稱或 IP 位址。  
  
2.  若要開啟 [偵錯] 屬性頁，請在 [方案總管] 中選擇專案，然後從捷徑功能表中選擇 [屬性]  。  
  
3.  然後選擇屬性頁視窗上的 [偵錯]  節點。

4. 如**目標裝置**，選取**遠端機器**。

5. 在下**遠端機器**，按一下 **尋找**。
  
4.  您可以輸入的名稱或 IP 位址的遠端裝置，或者您可以選擇將裝置從**遠端連線** 對話方塊。  
  
     ![選取遠端偵錯工具連接 對話方塊](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
     **遠端連線**對話方塊會顯示本機子網路以及透過乙太網路纜線直接連接至 Visual Studio 電腦的任何裝置上的裝置。  
  
 **在 JavaScript 或 Visual C++ 專案頁面中指定遠端裝置**  
  
 ![C# 43; &#43;專案進行遠端偵錯屬性](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  從 [ **要啟動的偵錯工具** ] 清單選擇 [ **遠端偵錯工具** ]。  
  
2.  在 [電腦名稱]  方塊中，輸入遠端裝置的網路名稱。 或者，您可以選擇方塊中的向下箭頭，以從 [選取遠端偵錯工具連接] 對話方塊中選取裝置。  
  
 **在 Visual C# 和 Visual Basic 專案頁面中指定遠端裝置**  
  
 ![受管理的遠端偵錯專案屬性](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  從 [ **目標裝置** ] 清單選擇 [ **遠端電腦** ]。  
  
2.  在 [ **遠端電腦** ] 方塊中輸入遠端裝置的網路名稱，或按一下 [ **尋找** ]，從 [ **選取遠端偵錯工具連接** ] 對話方塊選擇裝置。  
  
##  <a name="BKMK_Deployment_options"></a> 部署選項  
 您可以在啟始專案的 [偵錯] 屬性頁上設定下列部署選項。  
  
 **允許網路回送**  
 基於安全性理由，UWP 或[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]標準模式安裝的應用程式不允許進行網路呼叫其安裝所在的裝置。 根據預設，Visual Studio 部署會針對部署應用程式建立此規則的豁免。 此豁免可讓您測試在單一機器上的通訊程序。 在將您的應用程式提交至 [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]之前，您應該在沒有豁免的情況下測試您的應用程式。  
  
 移除應用程式中的網路回送豁免：  
  
-   在 [C# 和 VB 偵錯] 屬性頁上，清除 [允許網路回送]  核取方塊。  
  
-   在 [JavaScript 偵錯] 屬性頁上，將 [允許網路回送]  值設定為 [否] 。  
  
 **[不啟動，但在我的程式碼啟動時進行偵錯] (C# 和 VB)/[啟動應用程式] (JavaScript 和 C++)**  
 設定部署在應用程式啟動時自動啟動偵錯工作階段：  
  
-   在 [C# 和 VB 偵錯] 屬性頁上，核取 [不啟動，但在我的程式碼啟動時進行偵錯]  核取方塊。  
  
-   在 [JavaScript 偵錯] 屬性頁上，將 [啟動應用程式]  值設定為 [是] 。  
  
## <a name="see-also"></a>請參閱  
 [偵錯已安裝的應用程式套件](../debugger/debug-installed-app-package.md)。   
 [從 Visual Studio 執行應用程式](../debugger/run-store-apps-from-visual-studio.md)