---
title: 遠端偵錯 c + + 專案 |Microsoft Docs
description: 瞭解如何依照下列逐步指示，從遠端電腦進行 Visual Studio c + + 應用程式的偵錯工具。
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
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 9915fdab1d4d0976a199a09a11c815e4966192a5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934646"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Visual Studio 中的遠端偵錯 c + + 專案
若要在不同的電腦上進行 Visual Studio 應用程式的偵錯工具，請在您要部署應用程式的電腦上安裝並執行遠端工具、將專案設定為從 Visual Studio 連線到遠端電腦，然後部署和執行您的應用程式。

![遠端偵錯程式元件](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

如需有關將通用 Windows 應用程式遠端偵錯 (UWP) 的詳細資訊，請參閱 [Debug 已安裝的應用程式套件](debug-installed-app-package.md)。

## <a name="requirements"></a>規格需求

Windows 7 和更新版本上支援遠端偵錯程式， (不是從 Windows Server 2008 Service Pack 2 開始) 和 Windows Server 版本。 如需完整的需求清單，請參閱 [需求](../debugger/remote-debugging.md#requirements_msvsmon)。

> [!NOTE]
> 不支援透過 proxy 連線的兩部電腦之間的偵錯工具。 不建議透過高延遲或低頻寬的連線（例如撥號網際網路，或透過網際網路跨國家/地區）進行偵錯工具，且可能會失敗或可能會變慢。

## <a name="download-and-install-the-remote-tools"></a>下載及安裝遠端工具

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> 在某些情況下，從檔案共用執行遠端偵錯程式可能是最有效率的作法。 如需詳細資訊，請參閱 [從檔案共用執行遠端偵錯程式](../debugger/remote-debugging.md#fileshare_msvsmon)。

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a> 設定遠端偵錯程式

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果您需要為其他使用者新增許可權，請變更遠端偵錯程式的驗證模式或埠號碼，請參閱 [設定遠端偵錯程式](../debugger/remote-debugging.md#configure_msvsmon)。

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a> 遠端偵錯 c + + 專案
 在下列程式中，會 C:\remotetemp\MyMfc 專案的名稱和路徑，而遠端電腦的名稱是 **MJO-DL**。

1. 建立名為 **mymfc** 的 MFC 應用程式。

2. 在應用程式某處設定容易達到的中斷點，例如在 **MainFrm.cpp** 其中 `CMainFrame::OnCreate` 的開頭。

3. 在方案總管中，以滑鼠右鍵按一下專案，然後選取 [ **屬性**]。 開啟 [偵錯] 索引標籤。

4. 將 [要啟動的偵錯工具] 設為 [遠端 Windows 偵錯工具]。

    ![Visual Studio 方案總管屬性中 [偵錯工具] 索引標籤的螢幕擷取畫面。 [要啟動的偵錯工具] 屬性設定為 [遠端 Windows 偵錯工具]。](../debugger/media/remotedebuggingcplus.png)

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

    如果您 (選用) 部署其他檔案，則該資料夾必須存在於這兩部電腦上。

6. 在方案總管中，以滑鼠右鍵按一下方案，然後選擇 [ **設定管理員**]。

7. 在 [偵錯] 組態中，選取 [部署] 核取方塊。

    ![Visual Studio 方案總管中設定管理員的螢幕擷取畫面。 已選取 [偵錯工具] 設定，並已核取 [部署]。](../debugger/media/remotedebugcplusdeploy.png)

8. 開始偵錯 ([偵錯] > [開始偵錯]，或 **F5**)。

9. 可執行檔會自動部署到遠端電腦。

10. 如果出現提示，請輸入網路認證以連接到遠端電腦。

     所需的認證是您網路的安全性設定所特有的。 例如，在網域電腦上，您可以選擇安全性憑證，或輸入您的功能變數名稱和密碼。 在非網域電腦上，您可以輸入電腦名稱稱和有效的使用者帳戶名稱，例如，以及 <strong>MJO-DL\name@something.com</strong> 正確的密碼。

11. 在 Visual Studio 的電腦上，您應該會看到執行過程在中斷點停止。

    > [!TIP]
    > 或者，您可以另外執行一個步驟來部署檔案。 在 [方案總管] 中，以滑鼠右鍵按一下 [mymfc] 節點，然後選擇 [部署]。

    如果您有應用程式所需的非程式碼檔案，您可以在 [**遠端 Windows 偵錯工具**] 頁面上，于 **其他要部署** 的檔案中指定它們。

    或者，您可以將檔案包含在您的專案中，並在每個檔案的 [**屬性**] 頁面中，將 [**內容**] 屬性設定為 **[是]** 。 這些檔案會複製到 [**遠端 Windows 偵錯工具**] 頁面上指定的 **部署目錄**。 如果您需要將檔案複製到 **部署目錄** 的子資料夾，您也可以變更 **專案類型** 來 **複製** 檔案，並在該處指定其他屬性。

## <a name="set-up-debugging-with-remote-symbols"></a>設定遠端符號偵錯

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>另請參閱
- [Visual Studio 偵錯](../debugger/index.yml)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [設定 Windows 防火牆以進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)
- [在遠端 IIS 電腦上對 ASP.NET 進行遠端偵錯](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)