---
title: 遠端偵錯 C# 或 VB 專案 |微軟文檔
ms.custom:
- remotedebugging"=
- seodec18
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
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f147acae956ad380c6e85984de29d5316394c0a
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302095"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>在視覺化工作室中遠端偵錯 C# 或視覺化基本專案
要調試已部署于其他電腦上的 Visual Studio 應用程式，請在部署應用的電腦上安裝和運行遠端工具，將專案配置為從 Visual Studio 連接到遠端電腦，然後運行應用。

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

## <a name="remote-debug-the-project"></a><a name="remote_csharp"></a>遠端偵錯專案
偵錯工具無法將 Visual C# 或 Visual Basic 傳統型應用程式部署到遠端電腦，但您還是可以對其遠端偵錯，如下所示。 以下過程假定您希望在名為**MJO-DL**的電腦上調試它，如下圖所示。

1. 建立名為 **MyWpf** 的 WPF 專案。

2. 在程式碼某處設定容易達到的中斷點。

    例如，您可能會在按鈕處理常式中設定中斷點。 為此，請打開 MainWindow.xaml，然後從工具箱中添加按鈕控制項，然後按兩下按鈕以打開它的處理常式。

3. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇 [屬性]****。

4. 在 [屬性]**** 頁面上，選擇 [偵錯]**** 索引標籤。

    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")

5. 確認 [工作目錄]**** 文字方塊為空白。

6. 選擇 **"使用遠端電腦**"，並在文字方塊中鍵入**您的機器名稱：埠**。 （埠號顯示在遠端偵錯器視窗中。 每個版本的 Visual Studio 中的埠號遞增 2。

    在此示例中，使用：
    ::: moniker range=">=vs-2019"
    **MJO-DL：4024**在視覺工作室 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **MJO-DL：4022**在視覺工作室 2017
    ::: moniker-end

7. 請確定未選取 [啟用原生程式碼偵錯]****。

8. 建置專案。

9. 在遠端電腦上建立資料夾，其路徑與 Visual Studio 電腦上的 [偵錯]**** 資料夾相同：**\<來源路徑>\MyWPF\MyWPF\bin\Debug**。

10. 從 Visual Studio 電腦複製您剛才建置的可執行檔到遠端電腦上新建立的資料夾。

    > [!CAUTION]
    > 不要更改代碼或重新生成（或者必須重複此步驟）。 您複製到遠端電腦的可執行檔必須完全符合您的本機來源和符號。

    您可以手動複製專案、使用 Xcopy、Robocopy、Powershell 或其他選項。

11. 確保遠端偵錯器在目的電腦上運行（如果不是，則在 **"開始"** 功能表中搜索**遠端偵錯器**）。 遠端偵錯器視窗如下所示。

     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")

12. 在 Visual Studio 中，開始偵錯 ([偵錯] > [開始偵錯]****，或 **F5**)。

13. 如果出現提示，請輸入網路憑據以連接到遠端電腦。

     所需的憑據因網路的安全配置而異。 例如，在域電腦上，您可以輸入功能變數名稱和密碼。 在非域電腦上，您可以輸入電腦名稱稱和有效使用者帳戶名稱（如<strong>MJO-DL\name@something.com</strong>）以及正確的密碼。

     您應該會看到 WPF 應用程式主視窗已在遠端電腦上開啟。

14. 如有必要，請採取措施命中中斷點。 您應該會看到中斷點為作用中。 如果不是的話，則應用程式的符號尚未載入。 重試，如果不起作用，請獲取有關載入符號的資訊，以及如何在["理解符號檔和 Visual Studio 的符號設置](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)"上排除這些符號的故障。

15. 在 Visual Studio 的電腦上，您應該會看到執行過程在中斷點停止。

    如果您有應用程式需要使用的任何非代碼檔，則需要將它們包含在 Visual Studio 專案中。 為其他檔創建專案資料夾（在**解決方案資源管理器**中，按一下"**添加>新資料夾**"。 然後將檔案新增至資料夾 (在 [方案總管]**** 中，按一下 [新增] > [現有的項目]****，然後選取檔案)。 在每個檔案的 [屬性]**** 頁面上，將 [複製到輸出目錄]**** 設定為 [一律複製]****。

## <a name="set-up-debugging-with-remote-symbols"></a>設定遠端符號偵錯

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>另請參閱
- [Visual Studio 偵錯](../debugger/index.yml)
- [首先查看調試器](../debugger/debugger-feature-tour.md)
- [配置用於遠端偵錯的 Windows 防火牆](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)
- [在遠端 IIS 電腦上對 ASP.NET 進行遠端偵錯](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)