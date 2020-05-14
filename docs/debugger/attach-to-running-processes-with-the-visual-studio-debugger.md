---
title: 使用偵錯工具附加至執行中進程 |Microsoft Docs
ms.custom: seodec18
ms.date: 04/14/2020
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 075f5b0df703e31ea265085f422567a4fb5298a4
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385485"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>使用 Visual Studio 偵錯工具附加至執行中處理序
您可以將 Visual Studio 偵錯工具附加至本機或遠端電腦上執行的處理序。 行程執行後,選擇 **「調試** > **附加到行程」** 或在可視化工作室中按**Ctrl**+**Alt**+**P,** 並使用 **「附加到行程」** 對話框將調試器附加到進程。

您可以使用 **「附加到行程」** 在本地或遠端電腦上調試正在執行的應用、同時除錯多個程序、除錯未在 Visual Studio 建立的應用程式,或除錯未從 Visual Studio 啟動的任何應用,並附加了除錯器。 例如,如果您運行的應用時沒有調試器並遇到異常,則可以將除錯器附加到運行應用的進程並開始調試。

> [!TIP]
> 不確定是否將 **「附加到進程」** 用於調試方案? 請參考[常見除錯機制](#BKMK_Scenarios)。

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a>附加到本地電腦上的執行的程序

要快速重新附加到以前附加到的行程,請參閱[重新附加到行程](#BKMK_reattach)。

您可以在遠端電腦上執行試行程,請參考[遠端電腦上的行程](#BKMK_Attach_to_a_process_on_a_remote_computer)。

::: moniker range=">= vs-2019"
在 Linux Docker 容器上調試 .NET Core 行程,請參閱[附加到 Linux Docker 容器](#BKMK_Linux_Docker_Attach)。
::: moniker-end

**要附加到本地電腦上的程序,請:**

1. 在可視化工作室中,選擇**調試** > **附加到行程**(或按**Ctrl**+**Alt**+**P)** 以打開 **「附加到行程**」對話框。

   **連接類型**應設置為 **"預設**" **連接目標**應為本地電腦名稱。

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. 在 **「可用行程**」清單中,尋找並選擇要附加到的進程或進程。

   - 要快速選擇流程,請在 **『篩選器過程』** 框中鍵入其名稱或首字母。

   - 如果您不知道行程名稱,請瀏覽清單,或檢視某些常見程序名稱[的常見除錯方案](#BKMK_Scenarios)。

   >[!TIP]
   >當 **「附加到行程」** 對話框打開時,行程可以在後台啟動和停止,因此正在運行的行程清單可能並不總是最新的。 您可以隨時選擇 **「刷新」** 以查看目前清單。

3. 在「**附加到**」欄位中,請確保列出計畫調試的代碼類型。 預設**的"自動**"設置適用於大多數應用類型。

   要手動選擇代碼類型:
   1. 按一下 [選取]。 
   1. 在**選擇代碼類型對話**框中,選擇 **「除錯這些程式類型**」 。
   1. 選擇要調試的代碼類型。
   1. 選取 [確定]  。

4. 選取 [附加]****。

>[!NOTE]
>您可以將附加到多個應用進行調試,但調試器中一次只有一個應用處於活動狀態。 您可以在可視化工作室**調試位置**工具列或 **「進程」** 視窗中設置活動應用。

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>附加遠端電腦上的行程

您還可以在「**附加到行程」** 對話框中選擇遠端電腦,查看該電腦上執行的可用進程的清單,並附加到一個或多個調試進程。 遠端除錯器 (*msvsmon.exe*) 必須在遠端電腦上執行. 有關詳細資訊,請參閱[遠端除錯](../debugger/remote-debugging.md)。

有關除錯已部署到IIS的應用程式ASP.NET的更多完整說明,請參閱[遠端IIS電腦上的遠端調試ASP.NET。](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)

**要附加到遠端電腦上的執行的程序,請:**

1. 在可視化工作室中,選擇**調試** > **附加到行程**(或按**Ctrl**+**Alt**+**P)** 以打開 **「附加到行程**」對話框。

2. 在大多數情況下,**連接類型**應為 **「預設**」。 在 **'連接目標**' 方塊中, 使用以下方法之一選擇遠端電腦:

   - 選擇**連接目標**旁邊的下拉箭頭,然後從下拉清單中選擇計算機名稱。
   - 在 **'連線'目標**框中鍵入電腦名稱,然後按**Enter**。

     驗證 Visual Studio 是否將所需的連接埠加入到電腦名稱,該埠以格式顯示:**\<遠端電腦名稱>:連接埠**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > 如果無法使用遠端電腦名稱進行連接,請嘗試使用 IP 和埠位址(例如)。 `123.45.678.9:4022` 4024 是 Visual Studio 2019 x64 遠端調試器的預設埠。 有關其他遠端除錯器埠分配,請參閱[遠端除錯器連接埠分配](remote-debugger-port-assignments.md)。

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > 如果無法使用遠端電腦名稱進行連接,請嘗試使用 IP 和埠位址(例如)。 `123.45.678.9:4022` 4022 是 Visual Studio 2017 x64 遠端調試器的預設埠。 有關其他遠端除錯器埠分配,請參閱[遠端除錯器連接埠分配](remote-debugger-port-assignments.md)。

     ::: moniker-end

   - 選擇**連接目標**「框旁邊的 **」尋找**「按鈕以開啟 **」遠端連接**「對話框。 **遠端連線對話**框列出了本地子網上或直接連接到電腦的所有裝置。 您可能需要在伺服器上[打開 UDP 連接埠 3702](../debugger/remote-debugger-port-assignments.md)才能發現遠端裝置。 選擇所需的電腦或設備,然後按一下「**選擇**」。

   > [!NOTE]
   > **連接類型**設置在調試會話之間保留。 只當與該目標成功建立除錯連線時,**連接目標**設定才會在除錯工作階段之間保留。

3. 按下 **「刷新**」以填充 **「可用行程**」 清單。

    >[!TIP]
    >當 **「附加到行程」** 對話框打開時,行程可以在後台啟動和停止,因此正在運行的行程清單可能並不總是最新的。 您可以隨時選擇 **「刷新」** 以查看目前清單。

4. 在 **「可用行程**」清單中,尋找並選擇要附加到的進程或進程。

   - 要快速選擇流程,請在 **『篩選器過程』** 框中鍵入其名稱或首字母。

   - 如果您不知道行程名稱,請瀏覽清單,或檢視某些常見程序名稱[的常見除錯方案](#BKMK_Scenarios)。

   - 要查找在所有使用者帳戶下運行的行程,**請選擇「從所有使用者顯示行程**」 「複選框。

     >[!NOTE]
     >如果您嘗試附加至未受信任的使用者帳戶所擁有的處理序，會出現安全性警告對話方塊確認訊息。 有關詳細資訊,請參閱[安全警告:附加到不受信任的用戶擁有的進程可能很危險。如果以下資訊看起來可疑或不確定,請不要附加到此過程](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)。

5. 在「**附加到**」欄位中,請確保列出計畫調試的代碼類型。 預設**的"自動**"設置適用於大多數應用類型。

   要手動選擇代碼類型:
   1. 按一下 [選取]。 
   1. 在**選擇代碼類型對話**框中,選擇 **「除錯這些程式類型**」 。
   1. 選擇要調試的代碼類型。
   1. 選取 [確定]  。

6. 選取 [附加]****。

>[!NOTE]
>您可以將附加到多個應用進行調試,但調試器中一次只有一個應用處於活動狀態。 您可以在可視化工作室**調試位置**工具列或 **「進程」** 視窗中設置活動應用。

在某些情況下,當您在遠端桌面(終端服務)工作階段中調試時,「**可用行程**」清單不會顯示所有可用進程。 如果以使用者帳戶有限的使用者身份運行 Visual Studio,**則"可用進程**"清單不會顯示工作階段 0 中正在執行的進程。 工作階段 0 用於服務和其他伺服器程序,包括*w3wp.exe*。 您可藉由使用系統管理員帳戶來執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，或是從伺服器主控台 (而非終端機服務工作階段) 執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，來解決這個問題。

如果這些解決方法都沒有效，則第三個選項是從 Windows 命令列執行 `vsjitdebugger.exe -p <ProcessId>` 以附加至處理序。 您可以使用*tlist.exe*確定行程 ID。 若要取得 *tlist.exe*，您可以從 [WDK 和 WinDbg 下載](/windows-hardware/drivers/download-the-wdk)來下載並安裝適用於 Windows 的偵錯工具。

::: moniker range=">= vs-2019"


## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>使用 SSH 連線到 Linux 執行的 .NET 核心行程

有關詳細資訊,請參閱使用[SSH 在 Linux 上執行的遠端除錯 .NET 內核](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)。

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a>附加到 Linux Docker 容器執行的程序

您可以使用 **「附加到行程」** 對話框將 Visual Studio 除錯器附加到本地或遠端電腦上的 Linux .NET Core Docker 容器執行的行程。

> [!IMPORTANT]
> 要使用此功能,必須安裝 .NET 核心跨平臺開發工作負荷,並具有對原始程式碼的本地訪問許可權。

**要附加到 Linux Docker 容器中的正在執行的程序,請:**

1. 在可視化工作室中,選擇**調試>附加到行程 (CTRL_ALT_P)** 以打開 **「附加到行程**」對話框。

![附加到程序選單](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. 將**連接類型**設定為**Docker(Linux 容器)。**
3. 選擇 **「尋找..."** 可透過 **「選擇 Docker 容器」** 對話框設定**連接目標**。

    您可以在本地或遠端除錯 Docker 容器進程。
    
    **要在本地調試 Docker 容器進程,**
    1. 將**Docker CLI 主機**設定為**本地電腦**。
    1. 選擇要從清單中附加到的正在執行的容器,然後按 **「確定**」。
    
    ![選擇 Docker 容器選單](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. 要遠端除錯 Docker 容器行程:**
    
    > [!NOTE] 
    > 有兩個選項用於遠端連接到 Docker 容器中的正在執行的進程。 如果本地電腦上未安裝 Docker 工具,則使用 SSH 的第一個選項是理想的選擇。  如果確實在本地安裝了 Docker 工具,並且具有設定為接受遠端請求的 Docker 守護行程,請使用 Docker 守護程序嘗試第二個選項。

    1. ***要透過 SSH 連線到遠端電腦:***
        1. 選擇 **"添加..."** 以連接到遠程系統。<br/>
        ![連線到遠端系統](../debugger/media/connect-remote-system.png "連線到遠端系統")
        1. 選擇一個正在執行的容器,在成功連接到 SSH 或守護行程並命中 **「確定」** 後附加到該容器。

    
    1. ***將目標設定為透過[Docker 伺服程式](https://docs.docker.com/engine/reference/commandline/dockerd/)執行行程的遠端容器***
        1. 在**Docker 主機(可選)** 下指定守護程序位址(即透過 TCP、IP 等),然後單擊刷新連結。
        1. 選擇一個正在運行的容器,在成功連接到守護程序並命中 **「確定**」後附加到該容器。

4. 從**可用行程**清單中選擇相應的容器進程,然後選擇 **「附加」** 以在 Visual Studio 中開始除錯 C# 容器行程!

    ![已完成的 Docker 附加選單](../debugger/media/docker-attach-complete.png "已完成 Linux Docker 附加選單")
    

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a><a name="BKMK_Windows_Docker_Attach"></a>附加到 Windows Docker 容器執行的程序

您可以使用「**附加到行程」** 對話框將 Visual Studio 除錯器附加到本地電腦上的 Windows Docker 容器執行的行程。

> [!IMPORTANT]
> 要將此功能與 .NET Core 行程一起使用,您必須安裝 .NET 核心跨平臺開發工作負荷,並具有對原始程式碼的本地存取許可權。

**要附加到 Windows Docker 容器中的正在執行的程序,請:**

1. 在可視化工作室中,選擇**調試>附加到行程**(或**CTRL_ALT_P)** 以打開 **「附加到行程**」對話方塊。

   ![附加到程序選單](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. 將**連接類型**設定為**Docker(Windows 容器)。**
3. 選擇 **「尋找」 來**使用 **「選擇 Docker 容器」** 對話框設定**連接目標**。

    > [!IMPORTANT]
    > 目標進程必須具有與運行的 Docker Windows 容器相同的處理器體系結構。
    
   通過 SSH 將目標設定為遠端容器當前不可用,並且只能使用 Docker 守護行程來完成。
    
    ***將目標設定為透過[Docker 伺服程式](https://docs.docker.com/engine/reference/commandline/dockerd/)執行行程的遠端容器***
    1. 在**Docker 主機(可選)** 下指定守護程序位址(即透過 TCP、IP 等),然後單擊刷新連結。 

    1. 選擇成功連接到守護後要附加到的正在運行的容器,然後選擇"確定"。
    
4. 從**可用程序**清單中選擇相應的容器進程,然後選擇 **「附加」** 以開始除錯 C# 容器進程。

    ![已完成的 Docker 附加選單](../debugger/media/docker-attach-complete-windows.png "已完成 Windows Docker 附加選單")
    

5.  從可用程序清單中選擇相應的容器進程,然後選擇 **「附加」** 以開始除錯 C# 容器進程。


::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a>重新附加到行程

通過選擇**調試** > **重新附加到行程****(Shift**+**Alt**+**P),** 您可以快速重新附加到以前附加到的進程。 選擇此命令時,調試器將立即嘗試附加到附加到您附加到的最後一個進程,首先嘗試匹配以前的進程 ID,如果失敗,則與上一個行程名稱匹配。 如果未找到匹配項,或者多個進程具有相同的名稱,則將打開 **「附加到行程**」對話框,以便您可以選擇正確的進程。

> [!NOTE]
> 「**重新附加到行程」** 命令可從 Visual Studio 2017 中開始。

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a>常見的除錯方案

為了説明您確定是否使用 **「附加到行程**」以及要附加到的進程,下表顯示了一些常見的調試方案,其中包含指向更多說明的連結(如果可用)。 (該列表並非詳盡無遺。

對於某些應用類型(如通用 Windows 應用 (UWP) 應用),您不會直接附加到行程名稱,而是在 Visual Studio 中使用 **「調試已安裝的應用程式包**」選單選項(請參閱表)。

偵錯工具若要附加至以 C++ 撰寫的程式碼，該程式碼必須發出 `DebuggableAttribute`。 您可以使用 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) 連結器選項連結，將其自動加入程式碼。

對於用戶端腳本調試,必須在瀏覽器中啟用腳本調試。 要在 Chrome 上調試用戶端腳本,請選擇**JavaScript(Chrome)** 或**JavaScript(微軟邊緣 - 鉻)** 作為代碼類型,並且根據您的應用類型,您可能需要關閉所有 Chrome 實例並在調試`chrome.exe --remote-debugging-port=9222`模式下啟動瀏覽器(從命令行鍵入 )。 在早期版本的 Visual Studio 中,Chrome 的文本調試器是**Web 工具套件**。

要快速選擇要附加到的視覺工作室中的正在運行的進程,請在「視覺工作室」中鍵入**Ctrl**+**Alt**+**P,** 然後鍵入行程名稱的第一個字母。

|狀況|除錯方法|程序名稱|備註及連結|
|-|-|-|-|
|iIS 伺服器上的遠端除錯ASP.NET 4或 4.5|使用遠端工具並**附加到流程**|*w3wp.exe*|請參考[遠端 IIS 電腦上的遠端除錯ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|IIS 伺服器上的遠端除錯ASP.NET核心|使用遠端工具並**附加到流程**|*w3wp.exe*或*dotnet.exe*|從 .NET Core 3 開始 *,w3wp.exe*行程用於預設[的應用內託管模型](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models)。 有關應用部署,請參閱[發佈到 IIS](/aspnet/core/host-and-deploy/iis/)。 有關詳細資訊,請參閱[遠端 IIS 計算機上的遠端調試ASP.NET酷睿](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach)|
|除錯本地 IIS 伺服器上的用戶端文稿,用於受支援的應用類型 |使用**額外的流程**|*chrome.exe,**微軟EdgeCP.exe,* 或*iexplore.exe*|必須啟用腳本調試。 對於 Chrome,您還必須在調試模式下運行`chrome.exe --remote-debugging-port=9222`Chrome( 從命令行鍵入),並在 **「附加到**」欄位中選擇**JAVAScript(Chrome)。**|
|在本地電腦上調試 C#、視覺基礎或C++應用|使用標準除錯(**F5)** 或**附加到行程**|*\<應用程式名稱>.exe*|在大多數情況下,使用標準除錯而不是**附加到行程**。|
|遠端除錯 Windows 桌面應用程式|遠端工具|N/A| 請參考[遠端除錯 C# 或視覺化基本應用程式](../debugger/remote-debugging-csharp.md)或[遠端除錯C++應用](../debugger/remote-debugging-cpp.md)|
|除錯 .NET Linux 上的核心|使用**額外的流程**|*dotnet.exe*|使用 SSH,請參閱[使用 SSH 在 Linux 執行遠端除錯 .NET 內核](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)。 |
|在沒有除錯器的情況下啟動應用後,在本地電腦上調試ASP.NET應用|使用**額外的流程**|*iiexpress.exe*|這可能有助於使應用載入速度更快,例如(例如)分析時。 |
|在伺服器程序中除錯其他支援的應用類型|如果伺服器是遠端的,請使用遠端工具並**附加到行程**|*鉻.exe,* *iexplore.exe,* 或其他過程|如有必要,請使用資源監視器來幫助標識該過程。 請參閱[遠端偵錯](../debugger/remote-debugging.md)。|
|遠端除錯通用 Windows 應用 (UWP)、OneCore、HoloLens 或 IoT 應用|針對已安裝的應用程式套件進行偵錯|N/A|請參閱[除錯已安裝的應用程式](debug-installed-app-package.md),而不是使用**附加到行程**|
|除錯通用 Windows 應用 (UWP)、OneCore、HoloLens 或 IoT 應用,而這些應用不是從可視化工作室啟動的|針對已安裝的應用程式套件進行偵錯|N/A|請參閱[除錯已安裝的應用程式](debug-installed-app-package.md),而不是使用**附加到行程**|

## <a name="use-debugger-features"></a>使用除錯器功能

要在附加到進程時使用 Visual Studio 調試器的全部功能(如命中斷點),應用必須完全匹配本地源和符號。 也就是說,除錯器必須能夠載入正確的[符號 (.pdb) 檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。 默認情況下,這需要調試生成。

對於遠端調試方案,必須在 Visual Studio 中打開原始碼(或原始碼的副本)。 遠端電腦上的已編譯應用二進位檔必須與本地電腦上的相同版本。

在某些本地調試方案中,如果應用存在正確的符號檔,則可以在 Visual Studio 中調試,無法訪問源。 默認情況下,這需要調試生成。 關於詳細資訊,請參閱[指定符號與來源檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> 針對附加錯誤進行疑難排解
 當偵錯工具附加至執行中的處理序時，該處理序可以包含一種或多種程式碼類型。 偵錯工具可附加的程式碼類型會在 [選取程式碼類型] **** 對話方塊中顯示並供您選取。

 有時候，偵錯工具可以成功附加至一種程式碼類型，而無法附加至另一種程式碼類型。 如果您嘗試附加至遠端電腦上正在執行的處理序，可能會發生這種狀況。 遠端電腦可能為某些程式碼類型安裝了遠端偵錯元件，但沒有安裝其他程式碼類型的遠端偵錯元件。 如果您嘗試附加至兩個或多個處理序以進行直接的資料庫偵錯，也可能會發生這種狀況。 (SQL 偵錯僅支援附加至單一處理序)。

 如果調試器能夠附加到某些(但不是全部)代碼類型,則會看到一條消息,標識哪些類型未附加。

 如果偵錯工具成功附加到至少一種程式碼類型，您可以繼續偵錯該處理序。 您只能偵錯已附加成功的程式碼類型。 進程中的未附加代碼仍將運行,但您將無法設置斷點、查看資料或對該代碼執行其他調試操作。

 如果想要有關調試器未能附加到代碼類型的更具體資訊,請嘗試僅重新附加到該代碼類型。

 **取得程式碼類型為何無法附加的相關資訊：**

1. 與處理序中斷連結。 在**調試**功能表上,選擇 **「全部分離**」。。

1. 重新附加到進程,僅選擇未附加的代碼類型。

    1. 在 [附加至處理序]**** 對話方塊的 [可使用的處理序]**** 清單中，選取該處理序。

    2. 選取 [選取] ****。

    3. 在 [選取程式碼類型] **** 對話方塊中，選取 [偵錯這些程式碼類型] **** 以及之前附加失敗的程式碼類型。 取消選擇其他代碼類型。

    4. 選取 [確定]  。

    5. 在「**附加到行程」** 對話方塊中,選擇 **「附加**」。

    這時，該附加將完全失敗，您將取得特定的錯誤訊息。

## <a name="see-also"></a>另請參閱

- [對多重處理序進行偵錯](../debugger/debug-multiple-processes.md)
- [及時調試](../debugger/just-in-time-debugging-in-visual-studio.md)
- [遠端偵錯](../debugger/remote-debugging.md)
