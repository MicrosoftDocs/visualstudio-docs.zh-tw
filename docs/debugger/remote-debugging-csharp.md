---
title: 遠端 Debug a C#或 VB 專案 |Microsoft Docs
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
ms.openlocfilehash: 3490cab7c902dcdf1a7d0095eb69dd44de47a727
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211123"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>在 Visual Studio 中C#遠端偵錯或 Visual Basic 專案
若要對已部署在不同電腦上的 Visual Studio 應用程式進行偵測，請在您部署應用程式的電腦上安裝並執行遠端工具，將您的專案設定為從 Visual Studio 連接到遠端電腦，然後執行您的應用程式。

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

## <a name="remote_csharp"></a>遠端 debug 專案
偵錯工具無法將 Visual C# 或 Visual Basic 傳統型應用程式部署到遠端電腦，但您還是可以對其遠端偵錯，如下所示。 下列程式假設您想要在名為 MJO 的電腦上進行調試**程式**，如下圖所示。

1. 建立名為 **MyWpf** 的 WPF 專案。

2. 在程式碼某處設定容易達到的中斷點。

    例如，您可能會在按鈕處理常式中設定中斷點。 若要這麼做，請開啟 Mainwindow.xaml，並從 [工具箱] 加入按鈕控制項，然後按兩下按鈕以開啟它的處理常式。

3. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇 [屬性]。

4. 在 [屬性] 頁面上，選擇 [偵錯] 索引標籤。

    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")

5. 確認 [工作目錄] 文字方塊為空白。

6. 選擇 [**使用遠端電腦**]，然後在文字方塊中輸入**yourmachinename： port** 。 （埠號碼會顯示在 [遠端偵錯程式] 視窗中。 每個 Visual Studio 版本中的埠號碼會遞增2）。

    在此範例中，請使用：
    ::: moniker range=">=vs-2019"
    **MJO-DL： 4024** on Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **MJO-DL： 4022** on Visual Studio 2017
    ::: moniker-end

7. 請確定未選取 [啟用原生程式碼偵錯]。

8. 建置專案。

9. 在遠端電腦上建立資料夾，其路徑與 Visual Studio 電腦上的 [偵錯] 資料夾相同： **\<來源路徑>\MyWPF\MyWPF\bin\Debug**。

10. 從 Visual Studio 電腦複製您剛才建置的可執行檔到遠端電腦上新建立的資料夾。

    > [!CAUTION]
    > 請勿對程式碼進行變更或重建（或者您必須重複此步驟）。 您複製到遠端電腦的可執行檔必須完全符合您的本機來源和符號。

    您可以手動複製專案、使用 Xcopy、Robocopy、Powershell 或其他選項。

11. 請確定遠端偵錯程式正在目的電腦上執行（如果不是，請在 [**開始**] 功能表中搜尋**遠端偵錯程式**）。 [遠端偵錯程式] 視窗看起來像這樣。

     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")

12. 在 Visual Studio 中，開始偵錯 ([偵錯] > [開始偵錯]，或 **F5**)。

13. 如果出現提示，請輸入網路認證以連線到遠端電腦。

     必要的認證會根據您的網路安全性設定而有所不同。 例如，在網域電腦上，您可以輸入您的功能變數名稱和密碼。 在非網域電腦上，您可能會輸入電腦名稱稱和有效的使用者帳戶名稱（例如<strong>MJO-DL\name@something.com</strong>），以及正確的密碼。

     您應該會看到 WPF 應用程式主視窗已在遠端電腦上開啟。

14. 如有必要，請採取動作來叫用中斷點。 您應該會看到中斷點為作用中。 如果不是的話，則應用程式的符號尚未載入。 重試，如果無法解決問題，請取得有關載入符號的資訊，以及如何在[瞭解符號檔和 Visual Studio 的符號設定](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)進行疑難排解。

15. 在 Visual Studio 的電腦上，您應該會看到執行過程在中斷點停止。

    如果您有應用程式需要使用的任何非程式碼檔案，則需要將它們包含在 Visual Studio 專案中。 建立其他檔案的專案資料夾 (在 [方案總管]中，按一下 [新增] > [新增資料夾])。 然後將檔案新增至資料夾 (在 [方案總管] 中，按一下 [新增] > [現有的項目]，然後選取檔案)。 在每個檔案的 [屬性] 頁面上，將 [複製到輸出目錄] 設定為 [一律複製]。

## <a name="set-up-debugging-with-remote-symbols"></a>設定遠端符號偵錯

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>另請參閱
- [Visual Studio 偵錯](../debugger/index.yml)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [設定 Windows 防火牆進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)
- [在執行 IIS 的遠端電腦上對 ASP.NET 進行遠端偵錯](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)