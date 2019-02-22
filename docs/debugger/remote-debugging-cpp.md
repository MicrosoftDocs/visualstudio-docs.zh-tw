---
title: 遠端偵錯 Visual c + + 專案 |Microsoft Docs
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 88deb9957766b4e4e0802a1eded352a6ccb04f98
ms.sourcegitcommit: a916ce1eec19d49f060146f7dd5b65f3925158dd
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2019
ms.locfileid: "55231567"
---
# <a name="remote-debugging-a-visual-c-project-in-visual-studio"></a>遠端偵錯 Visual Studio 中的 Visual c + + 專案
若要偵錯在不同電腦上的 Visual Studio 應用程式安裝，您將在其中部署您的應用程式的電腦上執行遠端工具，設定您的專案從 Visual Studio 中，連接到遠端電腦，然後部署並執行您的應用程式。

![遠端偵錯工具元件](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

如需遠端偵錯通用 Windows App (UWP) 的資訊，請參閱[偵錯 Installed App Package](debug-installed-app-package.md)。

## <a name="requirements"></a>需求

遠端偵錯工具會支援在 Windows 7 及更新版本 (不 phone) 和開頭為 Windows Server 2008 Service Pack 2 的 Windows server 的版本。 需求的完整清單，請參閱 <<c0> [ 需求](../debugger/remote-debugging.md#requirements_msvsmon)。

> [!NOTE]
> 不支援透過 proxy 連線的兩部電腦之間的偵錯。 透過高延遲或低頻寬連線，例如撥號網際網路，或透過網際網路偵錯跨國家/地區不建議使用和可能失敗或非常慢。
  
## <a name="download-and-install-the-remote-tools"></a>下載及安裝遠端工具

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
> [!TIP]
> 在某些情況下，它可以是最有效率，若要從檔案共用執行遠端偵錯工具。 如需詳細資訊，請參閱 <<c0> [ 從檔案共用執行遠端偵錯工具](../debugger/remote-debugging.md#fileshare_msvsmon)。
  
## <a name="BKMK_setup"></a> 設定遠端偵錯工具

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果您需要新增額外的使用者的權限變更驗證模式或遠端偵錯工具連接埠號碼，請參閱[設定遠端偵錯工具](../debugger/remote-debugging.md#configure_msvsmon)。

## <a name="remote_cplusplus"></a> 遠端對 Visual C++ 專案進行偵錯  
 在下列程序中，名稱和專案的路徑是 C:\remotetemp\MyMfc，而遠端電腦的名稱是**MJO DL**。  
  
1. 建立名為 **mymfc** 的 MFC 應用程式。  
  
2. 在應用程式某處設定容易達到的中斷點，例如在 **MainFrm.cpp** 其中 `CMainFrame::OnCreate` 的開頭。  
  
3. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取**屬性**。 開啟 [偵錯] 索引標籤。  
  
4. 將 [要啟動的偵錯工具] 設為 [遠端 Windows 偵錯工具]。  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. 對屬性進行下列變更：  
  
   |設定|值|
   |-|-|  
   |遠端命令|C:\remotetemp\mymfc.exe|  
   |工作目錄|C:\remotetemp|  
   |遠端伺服器名稱|MJO DL:*連接埠號碼*|  
   |連線|遠端使用 Windows 驗證|  
   |偵錯工具類型|僅限原生|  
   |部署目錄|C:\remotetemp.|  
   |其他要部署的檔案|C:\data\mymfcdata.txt.|  
  
    如果您部署其他檔案 （選擇性） 時，資料夾必須存在兩台電腦上。  
  
6. 在 [方案總管] 中，以滑鼠右鍵按一下方案，然後選擇**Configuration Manager**。  
  
7. 在 [偵錯] 組態中，選取 [部署] 核取方塊。  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. 開始偵錯 ([偵錯] > [開始偵錯]，或 **F5**)。  
  
9. 可執行檔會自動部署到遠端電腦。  
  
10. 出現提示時，輸入網路認證以連接到遠端電腦。  
  
     您的網路安全性組態的特定所需的認證。 比方說，網域的電腦上，您可能會選擇安全性憑證，或輸入您的網域名稱和密碼。 在非網域電腦上，您可能輸入的機器名稱和有效的使用者帳戶名稱，例如<strong>MJO-DL\name@something.com</strong>，以及正確的密碼。  
  
11. 在 Visual Studio 的電腦上，您應該會看到執行過程在中斷點停止。  
  
    > [!TIP]
    > 或者，您可以另外執行一個步驟來部署檔案。 在 [方案總管] 中，以滑鼠右鍵按一下 [mymfc] 節點，然後選擇 [部署]。
  
    如果您有應用程式所需的非程式碼檔案，您可以指定在**其他要部署的檔案**上**遠端 Windows 偵錯工具**頁面。

    或者，您可以將檔案納入您的專案，並設定**內容**屬性設**是**中**屬性**每個檔案的頁面。 這些檔案會複製到**部署目錄**上指定**遠端 Windows 偵錯工具**頁面。 您也可以變更**項目類型**要**複製檔案**並指定額外的屬性，如果您需要的檔案複製到的子資料夾**部署目錄**。
  
## <a name="set-up-debugging-with-remote-symbols"></a>設定遠端符號偵錯 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)] 
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 偵錯](../debugger/index.md)  
 [偵錯工具簡介](../debugger/debugger-feature-tour.md)   
 [設定 Windows 防火牆以進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [在執行 IIS 的遠端電腦上對 ASP.NET 進行遠端偵錯](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)