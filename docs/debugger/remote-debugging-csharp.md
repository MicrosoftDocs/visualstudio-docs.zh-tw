---
title: "遠端偵錯 C# 或 Visual Studio 中的 VB 專案 |Microsoft 文件"
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords: remote debugging, setup
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
caps.latest.revision: "65"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5bfa2e09d96f383b39eb392d5172cf38d750cef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>遠端偵錯 Visual Studio 中的 C# 或 Visual Basic 專案
偵錯 Visual Studio 應用程式已部署在不同電腦上，安裝和部署您的應用程式的所在的電腦上執行遠端工具，設定您的專案，從 Visual Studio 中，連線到遠端電腦，然後執行您的應用程式。

![遠端偵錯工具元件](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")
  
遠端偵錯通用 Windows 應用程式 (UWP) 的相關資訊，請參閱[偵錯已安裝的應用程式套件](debug-installed-app-package.md)。

## <a name="requirements"></a>需求

遠端偵錯工具會支援 Windows 7 及更新版本 (不 phone) 和版本的 Windows Server 與 Windows Server 2008 Service Pack 2 開始。 如需需求的完整清單，請參閱[需求](../debugger/remote-debugging.md#requirements_msvsmon)。

> [!NOTE]
> 不支援透過 proxy 連線的兩部電腦之間的偵錯。 透過高延遲或低頻寬連線，例如撥號網際網路，或透過網際網路偵錯跨國家/地區不建議使用和可能會失敗或實在。
  
## <a name="download-and-install-the-remote-tools"></a>下載及安裝遠端工具

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> 在某些情況下，它可以是最有效率的檔案共用從執行遠端偵錯工具。 如需詳細資訊，請參閱[從檔案共用執行遠端偵錯工具](../debugger/remote-debugging.md#fileshare_msvsmon)。
  
## <a name="BKMK_setup"></a>設定遠端偵錯工具

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果您需要新增其他的使用者權限變更驗證模式或遠端偵錯工具連接埠號碼，請參閱[設定遠端偵錯工具](../debugger/remote-debugging.md#configure_msvsmon)。
  
## <a name="remote_csharp"></a>遠端偵錯專案
偵錯工具無法將 Visual C# 或 Visual Basic 傳統型應用程式部署到遠端電腦，但您還是可以對其遠端偵錯，如下所示。 下列程序假設您想要在名為的電腦上進行偵錯**MJO DL**，在下圖中所示。
  
1.  建立 WPF 專案，名為**MyWpf**。  
  
2.  在程式碼某處設定容易達到的中斷點。  
  
     例如，您可能會在按鈕處理常式中設定中斷點。 若要這樣做，開啟 MainWindow.xaml 中，並加入按鈕控制項從 [工具箱]，然後按兩下這個按鈕，開啟它的處理常式。
  
3.  在 方案總管 中，以滑鼠右鍵按一下專案，然後選擇 **屬性**。  
  
4.  在**屬性**頁面上，選擇**偵錯** 索引標籤。  
  
     ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5.  請確定**工作目錄**文字方塊是空的。  
  
6.  選擇**使用遠端機器**，然後輸入**MJO-DL:4022**在文字方塊中。 （4022 是遠端偵錯工具視窗中顯示的連接埠號碼。 連接埠號碼遞增每個版本的 Visual Studio 中的 2）。
  
7.  請確定**啟用機器碼偵錯**未選取。  
  
8.  建置專案。  
  
9. 是與相同的路徑在遠端電腦上建立資料夾**偵錯**Visual Studio 電腦上的資料夾： **\<來源路徑 > \MyWPF\MyWPF\bin\Debug**。  
  
10. 從 Visual Studio 電腦複製您剛才建置的可執行檔到遠端電腦上新建立的資料夾。
  
    > [!CAUTION]
    >  不變更程式碼或 rebuild （或您必須重複此步驟）。 您複製到遠端電腦的可執行檔必須完全符合您的本機來源和符號。

    您可以手動複製專案，請使用 Xcopy、 Robocopy、 Powershell 或其他選項。
  
11. 請確定目標電腦上執行遠端偵錯工具 (如果沒有，請搜尋**遠端偵錯工具**中**啟動**功能表)。 遠端偵錯工具視窗看起來像這樣。  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. 在 Visual Studio 中，開始偵錯 (**偵錯 > 開始偵錯**，或**F5**)。  
  
13. 如果出現提示，請輸入連接到遠端電腦的網路認證。  
  
     所需的認證是根據您的網路安全性組態而有所不同。 例如，在網域電腦，您可以輸入您的網域名稱和密碼。 在非網域的電腦，您可以輸入電腦名稱，有效的使用者帳戶名稱，例如 **MJO-DL\name@something.com** ，以及正確的密碼。

     您應該會看到 WPF 應用程式的主視窗已開啟遠端電腦上。
  
14. 如有必要，採取動作叫用中斷點。 您應該會看到中斷點為作用中。 如果沒有，則應用程式的符號尚未載入。 重試一次，而如果不行，會取得需載入符號資訊和如何解決在[了解符號檔和 Visual Studio 的符號設定](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx)。
  
15. 在 Visual Studio 的電腦上，您應該會看到執行過程在中斷點停止。
  
 如果您有應用程式所使用的非程式碼檔案，您需要將它們包含在 Visual Studio 專案。 建立其他檔案的專案資料夾 (在**方案總管] 中**，按一下 [**新增 > 新的資料夾**)。 然後將檔案加入資料夾 (在**方案總管] 中**，按一下 [**新增 > 現有項目**，然後選取的檔案)。 在**屬性**頁面上的每個檔案，將**複製到輸出目錄**至**永遠複製**。

## <a name="set-up-debugging-with-remote-symbols"></a>設定遠端符號偵錯 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯](../debugger/index.md)  
 [偵錯工具功能導覽](../debugger/debugger-feature-tour.md)   
 [設定 Windows 防火牆進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)   
 [在執行 IIS 的遠端電腦上對 ASP.NET 進行遠端偵錯](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)