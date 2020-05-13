---
title: 遠端偵錯C++專案 |微軟文檔
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
ms.openlocfilehash: 0173ed557afa47129e0cc92d9ef9b2d94a7b198f
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302109"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>遠端偵錯視覺化工作室中的C++專案
要調試其他電腦上的 Visual Studio 應用程式，請在將部署應用的電腦上安裝和運行遠端工具，將專案配置為從 Visual Studio 連接到遠端電腦，然後部署和運行應用。

![遠端偵錯器元件](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

有關遠端偵錯通用 Windows 應用 （UWP） 的資訊，請參閱[調試已安裝的應用包](debug-installed-app-package.md)。

## <a name="requirements"></a>需求

Windows 7 支援遠端偵錯器，支援從 Windows 伺服器 2008 服務包 2 開始的 Windows 伺服器更新版（不是手機）和版本。 有關需求的完整清單，請參閱[要求](../debugger/remote-debugging.md#requirements_msvsmon)。

> [!NOTE]
> 不支援在通過代理連接的兩台電腦之間進行調試。 不建議通過高延遲或低頻寬連接（如撥號 Internet）或跨國家/地區的 Internet 進行調試，並且可能會失敗或速度過慢，令人無法接受。

## <a name="download-and-install-the-remote-tools"></a>下載及安裝遠端工具

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> 在某些情況下，從檔共用運行遠端偵錯器效率最高。 有關詳細資訊，請參閱[從檔共用運行遠端偵錯器](../debugger/remote-debugging.md#fileshare_msvsmon)。

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a>設置遠端偵錯器

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果需要為其他使用者添加許可權，請更改身份驗證模式或遠端偵錯器的埠號，請參閱[配置遠端偵錯器](../debugger/remote-debugging.md#configure_msvsmon)。

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a>遠端偵錯C++專案
 在以下過程中，專案的名稱和路徑為 C：\遠端temp_MyMfc，遠端電腦的名稱為**MJO-DL**。

1. 建立名為 **mymfc** 的 MFC 應用程式。

2. 在應用程式某處設定容易達到的中斷點，例如在 **MainFrm.cpp** 其中 `CMainFrame::OnCreate` 的開頭。

3. 在解決方案資源管理器中，按右鍵專案並選擇**屬性**。 開啟 [偵錯]**** 索引標籤。

4. 將 [要啟動的偵錯工具]**** 設為 [遠端 Windows 偵錯工具]****。

    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")

5. 對屬性進行下列變更：

   |設定|值|
   |-|-|
   |遠端命令|C:\remotetemp\mymfc.exe|
   |工作目錄|C:\remotetemp|
   |遠端伺服器名稱|MJO-DL：*埠號*|
   |Connection|遠端使用 Windows 驗證|
   |偵錯工具類型|僅限原生|
   |部署目錄|C:\remotetemp.|
   |要部署的其他檔案|C:\data\mymfcdata.txt.|

    如果部署其他檔（可選），則兩台電腦上必須存在該資料夾。

6. 在解決方案資源管理器中，按右鍵解決方案並選擇**組態管理員**。

7. 在 [偵錯]**** 組態中，選取 [部署]**** 核取方塊。

    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")

8. 開始偵錯 ([偵錯] > [開始偵錯]****，或 **F5**)。

9. 可執行檔會自動部署到遠端電腦。

10. 如果出現提示，請輸入網路憑據以連接到遠端電腦。

     所需的憑據特定于網路的安全配置。 例如，在域電腦上，您可以選擇安全證書或輸入功能變數名稱和密碼。 在非域電腦上，您可以輸入電腦名稱稱和有效使用者帳戶名稱（如<strong>MJO-DL\name@something.com</strong>）以及正確的密碼。

11. 在 Visual Studio 的電腦上，您應該會看到執行過程在中斷點停止。

    > [!TIP]
    > 或者，您可以另外執行一個步驟來部署檔案。 在 [方案總管]**** 中，以滑鼠右鍵按一下 [mymfc]**** 節點，然後選擇 [部署]****。

    如果應用程式需要非代碼檔，則可以在 **"遠端 Windows 調試器**"頁上的 **"要部署的其他檔**"中指定這些檔。

    或者，您可以在專案中包含檔，並在每個檔的 **"屬性**"頁中將 **"內容"** 屬性設置為 **"是**"。 這些檔將複製到**遠端 Windows 調試器**頁上指定的**部署目錄**。 如果需要將檔案複製到**部署目錄**的子資料夾，還可以將**專案類型**更改為 **"複製檔**"並在此處指定其他屬性。

## <a name="set-up-debugging-with-remote-symbols"></a>設定遠端符號偵錯

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>另請參閱
- [Visual Studio 偵錯](../debugger/index.yml)
- [首先查看調試器](../debugger/debugger-feature-tour.md)
- [配置用於遠端偵錯的 Windows 防火牆](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)
- [在遠端 IIS 電腦上對 ASP.NET 進行遠端偵錯](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)