---
title: 遠端 Debug a Visual C++專案 |Microsoft Docs
ms.custom: remotedebugging
ms.date: 08/14/2018
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
ms.openlocfilehash: 81a5ebba2d14a0e091b3b0bcd78a066ef50ed759
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211106"
---
# <a name="remote-debugging-a-visual-c-project-in-visual-studio"></a>在 Visual Studio 中遠端C++調試視覺化專案
若要在不同的電腦上進行 Visual Studio 應用程式的偵測，請在您要部署應用程式的電腦上安裝並執行遠端工具、將專案設定為從 Visual Studio 連接到遠端電腦，然後部署並執行您的應用程式。

![遠端偵錯程式元件](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

如需遠端偵測通用 Windows 應用程式（UWP）的相關資訊，請參閱[Debug 已安裝的應用程式套件](debug-installed-app-package.md)。

## <a name="requirements"></a>需求

從 Windows Server 2008 Service Pack 2 開始，Windows 7 和更新版本（非電話）和 Windows Server 版本都支援遠端偵錯程式。 如需完整的需求清單，請參閱[需求](../debugger/remote-debugging.md#requirements_msvsmon)。

> [!NOTE]
> 不支援透過 proxy 連線的兩部電腦之間的調試。 不建議透過高延遲或低頻寬的連線（例如撥號網際網路，或透過網際網路跨國家/地區）進行調試，而且可能會失敗，或速度變慢。

## <a name="download-and-install-the-remote-tools"></a>下載及安裝遠端工具

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> 在某些情況下，從檔案共用執行遠端偵錯程式會是最有效率的作法。 如需詳細資訊，請參閱[從檔案共用執行遠端偵錯程式](../debugger/remote-debugging.md#fileshare_msvsmon)。

## <a name="BKMK_setup"></a> 設定遠端偵錯工具

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果您需要為其他使用者新增許可權，請變更遠端偵錯程式的驗證模式或埠號碼，請參閱[設定遠端偵錯程式](../debugger/remote-debugging.md#configure_msvsmon)。

## <a name="remote_cplusplus"></a> 遠端對 Visual C++ 專案進行偵錯
 在下列程式中，專案的名稱和路徑是 C:\remotetemp\MyMfc，而遠端電腦的名稱是**MJO-DL**。

1. 建立名為 **mymfc** 的 MFC 應用程式。

2. 在應用程式某處設定容易達到的中斷點，例如在 **MainFrm.cpp** 其中 `CMainFrame::OnCreate` 的開頭。

3. 在方案總管中，以滑鼠右鍵按一下專案，然後選取 [**屬性**]。 開啟 [偵錯] 索引標籤。

4. 將 [要啟動的偵錯工具] 設為 [遠端 Windows 偵錯工具]。

    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")

5. 對屬性進行下列變更：

   |設定|值|
   |-|-|
   |遠端命令|C:\remotetemp\mymfc.exe|
   |工作目錄|C:\remotetemp|
   |遠端伺服器名稱|MJO-DL：*portnumber*|
   |連線|遠端使用 Windows 驗證|
   |偵錯工具類型|僅限原生|
   |部署目錄|C:\remotetemp.|
   |要部署的其他檔案|C:\data\mymfcdata.txt.|

    如果您部署其他檔案（選擇性），則此資料夾必須存在於兩部電腦上。

6. 在方案總管中，以滑鼠右鍵按一下方案，然後選擇 [ **Configuration Manager**]。

7. 在 [偵錯] 組態中，選取 [部署] 核取方塊。

    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")

8. 開始偵錯 ([偵錯] > [開始偵錯]，或 **F5**)。

9. 可執行檔會自動部署到遠端電腦。

10. 如果出現提示，請輸入網路認證以連線到遠端電腦。

     所需的認證是您的網路安全性設定所特有。 例如，在網域電腦上，您可以選擇安全性憑證，或輸入您的功能變數名稱和密碼。 在非網域電腦上，您可能會輸入電腦名稱稱和有效的使用者帳戶名稱（例如<strong>MJO-DL\name@something.com</strong>），以及正確的密碼。

11. 在 Visual Studio 的電腦上，您應該會看到執行過程在中斷點停止。

    > [!TIP]
    > 或者，您可以另外執行一個步驟來部署檔案。 在 [方案總管] 中，以滑鼠右鍵按一下 [mymfc] 節點，然後選擇 [部署]。

    如果您有應用程式所需的非程式碼檔案，您可以在 [**遠端 Windows 偵錯工具**] 頁面上，將它們指定**于要部署的其他**檔案中。

    或者，您可以在專案中包含檔案，並在每個檔案的 [**屬性**] 頁面中，將 [**內容**] 屬性設定為 **[是]** 。 這些檔案會複製到 [**遠端 Windows 偵錯工具**] 頁面上指定的**部署目錄**。 如果您需要將檔案複製到**部署目錄**的子資料夾，您也可以將**專案類型**變更為 [**複製**檔案]，並指定其他屬性。

## <a name="set-up-debugging-with-remote-symbols"></a>設定遠端符號偵錯

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>另請參閱
- [Visual Studio 偵錯](../debugger/index.yml)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [設定 Windows 防火牆進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)
- [在執行 IIS 的遠端電腦上對 ASP.NET 進行遠端偵錯](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)