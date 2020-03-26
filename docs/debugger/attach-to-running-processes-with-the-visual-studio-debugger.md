---
title: 使用調試器連接到正在運行的進程 |微軟文檔
ms.custom: seodec18
ms.date: 04/08/2019
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
ms.openlocfilehash: b5305be7615e426d7792d8dd3fefb2579e2ab6be
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233050"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>使用 Visual Studio 偵錯工具附加至執行中處理序
您可以將 Visual Studio 偵錯工具附加至本機或遠端電腦上執行的處理序。 進程運行後，選擇 **"調試** > **附加到進程"** 或在視覺化工作室中按**Ctrl**+**Alt**+**P，** 並使用 **"附加到進程"** 對話方塊將調試器附加到進程。

您可以使用 **"附加到進程"** 在本地或遠端電腦上調試正在運行的應用、同時調試多個進程、調試未在 Visual Studio 中創建的應用，或者調試未從 Visual Studio 啟動的任何應用，並附加了調試器。 例如，如果您運行的應用時沒有調試器並遇到異常，則可以將調試器附加到運行應用的進程並開始調試。

> [!TIP]
> 不確定是否將 **"附加到進程"** 用於調試方案？ 請參閱[常見調試方案](#BKMK_Scenarios)。

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a>附加到本地電腦上的正在運行的進程

要快速重新附加到以前附加到的進程，請參閱[重新附加到進程](#BKMK_reattach)。

要在遠端電腦上調試進程，請參閱[附加到遠端電腦上的進程](#BKMK_Attach_to_a_process_on_a_remote_computer)。

::: moniker range=">= vs-2019"
要在 Linux Docker 容器上調試 .NET Core 進程，請參閱[附加到 Linux Docker 容器](#BKMK_Linux_Docker_Attach)。
::: moniker-end

**要附加到本地電腦上的進程，請：**

1. 在視覺化工作室中，選擇**調試** > **附加到進程**（或按**Ctrl**+**Alt**+**P）** 以打開 **"附加到進程**"對話方塊。

   **連線類型**應設置為 **"預設**"。 **連接目標**應為本地電腦名稱稱。

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. 在 **"可用進程**"清單中，查找並選擇要附加到的進程或進程。

   - 要快速選擇流程，請在 **"篩選器過程"** 框中鍵入其名稱或首字母。

   - 如果您不知道進程名稱，請瀏覽清單，或查看某些常見進程名稱[的常見調試方案](#BKMK_Scenarios)。

   >[!TIP]
   >當 **"附加到進程"** 對話方塊打開時，進程可以在後臺啟動和停止，因此正在運行的進程清單可能並不總是最新的。 您可以隨時選擇 **"刷新"** 以查看當前清單。

3. 在"**附加到**"欄位中，請確保列出計畫調試的代碼類型。 預設**的"自動**"設置適用于大多數應用類型。

   要手動選擇代碼類型：
   1. 按一下 **"選擇**"。
   1. 在 **"選擇代碼類型"** 對話方塊中，選擇 **"調試這些代碼類型**"。
   1. 選擇要調試的代碼類型。
   1. 選取 [確定]****。

4. 選取 [附加]****。

>[!NOTE]
>您可以將附加到多個應用進行調試，但調試器中一次只有一個應用處于活動狀態。 您可以在視覺化工作室**調試位置**工具列或 **"進程"** 視窗中設置活動應用。

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>附加到遠端電腦上的進程

您還可以在"**附加到進程"** 對話方塊中選擇遠端電腦，查看該電腦上運行的可用進程的清單，並附加到一個或多個調試進程。 遠端偵錯器 （*msvsmon.exe*） 必須在遠端電腦上運行. 有關詳細資訊，請參閱[遠端偵錯](../debugger/remote-debugging.md)。

有關調試已部署到 IIS 的應用程式ASP.NET的更多完整說明，請參閱[遠端 IIS 電腦上的遠端偵錯ASP.NET。](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)

**要附加到遠端電腦上的正在運行的進程，請：**

1. 在視覺化工作室中，選擇**調試** > **附加到進程**（或按**Ctrl**+**Alt**+**P）** 以打開 **"附加到進程**"對話方塊。

2. 在大多數情況下，**連線類型**應為 **"預設**"。 在 **"連接目標**"框中，使用以下方法之一選擇遠端電腦：

   - 選擇**連接目標**旁邊的下拉箭頭，然後從下拉清單中選擇電腦名稱稱。
   - 在 **"連接"目標**框中鍵入電腦名稱稱，然後按**Enter**。

     驗證 Visual Studio 是否將所需的埠添加到電腦名稱稱，該埠以格式顯示：**\<遠端電腦名稱稱>：埠**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > 如果無法使用遠端電腦名稱稱進行連接，請嘗試使用 IP 和埠位址（例如）。 `123.45.678.9:4022` 4024 是 Visual Studio 2019 x64 遠端偵錯器的預設埠。 有關其他遠端偵錯器埠分配，請參閱[遠端偵錯器埠分配](remote-debugger-port-assignments.md)。

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > 如果無法使用遠端電腦名稱稱進行連接，請嘗試使用 IP 和埠位址（例如）。 `123.45.678.9:4022` 4022 是 Visual Studio 2017 x64 遠端偵錯器的預設埠。 有關其他遠端偵錯器埠分配，請參閱[遠端偵錯器埠分配](remote-debugger-port-assignments.md)。

     ::: moniker-end

   - 選擇 **"連接目標**"框旁邊的 **"查找**"按鈕以打開 **"遠端連線**"對話方塊。 "**遠端連線"** 對話方塊列出了本地子網上或直接連接到電腦的所有設備。 您可能需要在伺服器上[打開 UDP 埠 3702](../debugger/remote-debugger-port-assignments.md)才能發現遠端設備。 選擇所需的電腦或設備，然後按一下"**選擇**"。

   > [!NOTE]
   > **連線類型**設置在調試會話之間保留。 僅當與該目標成功建立調試連接時，**連接目標**設置才會在調試會話之間保留。

3. 按一下 **"刷新**"以填充 **"可用進程**"清單。

    >[!TIP]
    >當 **"附加到進程"** 對話方塊打開時，進程可以在後臺啟動和停止，因此正在運行的進程清單可能並不總是最新的。 您可以隨時選擇 **"刷新"** 以查看當前清單。

4. 在 **"可用進程**"清單中，查找並選擇要附加到的進程或進程。

   - 要快速選擇流程，請在 **"篩選器過程"** 框中鍵入其名稱或首字母。

   - 如果您不知道進程名稱，請瀏覽清單，或查看某些常見進程名稱[的常見調試方案](#BKMK_Scenarios)。

   - 要查找在所有使用者帳戶下運行的進程，**請選中"從所有使用者顯示進程**"核取方塊。

     >[!NOTE]
     >如果您嘗試附加至未受信任的使用者帳戶所擁有的處理序，會出現安全性警告對話方塊確認訊息。 有關詳細資訊，請參閱[安全警告：附加到不受信任的使用者擁有的進程可能很危險。如果以下資訊看起來可疑或不確定，請不要附加到此過程](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)。

5. 在"**附加到**"欄位中，請確保列出計畫調試的代碼類型。 預設**的"自動**"設置適用于大多數應用類型。

   要手動選擇代碼類型：
   1. 按一下 **"選擇**"。
   1. 在 **"選擇代碼類型"** 對話方塊中，選擇 **"調試這些代碼類型**"。
   1. 選擇要調試的代碼類型。
   1. 選取 [確定]****。

6. 選取 [附加]****。

>[!NOTE]
>您可以將附加到多個應用進行調試，但調試器中一次只有一個應用處于活動狀態。 您可以在視覺化工作室**調試位置**工具列或 **"進程"** 視窗中設置活動應用。

在某些情況下，當您在遠端桌面（終端服務）會話中調試時，"**可用進程**"清單不會顯示所有可用進程。 如果以使用者帳戶有限的使用者身份運行 Visual Studio，**則"可用進程**"清單不會顯示會話 0 中正在運行的進程。 會話 0 用於服務和其他伺服器進程，包括*w3wp.exe*。 您可藉由使用系統管理員帳戶來執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，或是從伺服器主控台 (而非終端機服務工作階段) 執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，來解決這個問題。

如果這些解決方法都沒有效，則第三個選項是從 Windows 命令列執行 `vsjitdebugger.exe -p <ProcessId>` 以附加至處理序。 您可以使用*tlist.exe*確定進程 ID。 若要取得 *tlist.exe*，您可以從 [WDK 和 WinDbg 下載](/windows-hardware/drivers/download-the-wdk)來下載並安裝適用於 Windows 的偵錯工具。

::: moniker range=">= vs-2019"


## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>使用 SSH 連接到在 Linux 上運行的 .NET 核心進程

有關詳細資訊，請參閱使用[SSH 在 Linux 上運行的遠端偵錯 .NET 內核](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)。

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a>附加到在 Linux Docker 容器上運行的進程

您可以使用 **"附加到進程"** 對話方塊將 Visual Studio 調試器附加到本地或遠端電腦上的 Linux .NET Core Docker 容器中運行的進程。

> [!IMPORTANT]
> 要使用此功能，必須安裝 .NET 核心跨平臺開發工作負荷，並具有對原始程式碼的本地存取權限。

**要附加到 Linux Docker 容器中的正在運行的進程，請：**

1. 在視覺化工作室中，選擇**調試>附加到進程 （CTRL_ALT_P）** 以打開 **"附加到進程**"對話方塊。

![附加到進程功能表](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. 將**連線類型**設置為**Docker（Linux 容器）。**
3. 選擇 **"查找..."** 可通過 **"選擇 Docker 容器"** 對話方塊設置**連接目標**。

    您可以在本地或遠端偵錯 Docker 容器進程。
    
    **要在本地調試 Docker 容器進程，**
    1. 將**Docker CLI 主機**設置為**本地電腦**。
    1. 選擇要從清單中附加到的正在運行的容器，然後按 **"確定**"。
    
    ![選擇 Docker 容器功能表](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. 要遠端偵錯 Docker 容器進程：**
    
    > [!NOTE] 
    > 有兩個選項用於遠端連線到 Docker 容器中的正在運行的進程。 如果本地電腦上未安裝 Docker 工具，則使用 SSH 的第一個選項是理想的選擇。  如果確實在本地安裝了 Docker 工具，並且具有配置為接受遠端請求的 Docker 守護進程，請使用 Docker 守護進程嘗試第二個選項。

    1. ***要通過 SSH 連接到遠端電腦：***
        1. 選擇 **"添加..."** 以連接到遠端系統。<br/>
        ![連接到遠端系統](../debugger/media/connect-remote-system.png "連接到遠端系統")
        1. 選擇一個正在運行的容器，在成功連接到 SSH 或守護進程並命中 **"確定"** 後附加到該容器。

    
    1. ***將目標設置為通過[Docker 守護進程](https://docs.docker.com/engine/reference/commandline/dockerd/)運行進程的遠端容器***
        1. 在**Docker 主機（可選）** 下指定守護進程位址（即通過 TCP、IP 等），然後按一下刷新連結。
        1. 選擇一個正在運行的容器，在成功連接到守護進程並命中 **"確定**"後附加到該容器。

4. 從**可用進程**清單中選擇相應的容器進程，然後選擇 **"附加"** 以在 Visual Studio 中開始調試 C# 容器進程！

    ![已完成的 Docker 附加功能表](../debugger/media/docker-attach-complete.png "已完成 Linux Docker 附加功能表")
    

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a><a name="BKMK_Windows_Docker_Attach"></a>附加到在 Windows Docker 容器上運行的進程

您可以使用"**附加到進程"** 對話方塊將 Visual Studio 調試器附加到本地電腦上的 Windows Docker 容器中運行的進程。

> [!IMPORTANT]
> 要將此功能與 .NET Core 進程一起使用，您必須安裝 .NET 核心跨平臺開發工作負荷，並具有對原始程式碼的本地存取權限。

**要附加到 Windows Docker 容器中的正在運行的進程，請：**

1. 在視覺化工作室中，選擇**調試>附加到進程**（或**CTRL_ALT_P）** 以打開 **"附加到進程**"對話方塊。

   ![附加到進程功能表](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. 將**連線類型**設置為**Docker（Windows 容器）。**
3. 選擇 **"查找..."** 以使用 **"選擇 Docker 容器"** 對話方塊設置**連接目標**。

    > [!IMPORTANT]
    > 目標進程必須具有與運行的 Docker Windows 容器相同的處理器體系結構。
    
   通過 SSH 將目標設置為遠端容器當前不可用，並且只能使用 Docker 守護進程來完成。
    
    ***將目標設置為通過[Docker 守護進程](https://docs.docker.com/engine/reference/commandline/dockerd/)運行進程的遠端容器***
    1. 在**Docker 主機（可選）** 下指定守護進程位址（即通過 TCP、IP 等），然後按一下刷新連結。 

    1. 選擇成功連接到守護進程後要附加到的正在運行的容器，然後選擇"確定"。
    
4. 從**可用進程**清單中選擇相應的容器進程，然後選擇 **"附加"** 以開始調試 C# 容器進程。

    ![已完成的 Docker 附加功能表](../debugger/media/docker-attach-complete-windows.png "已完成 Windows Docker 附加功能表")
    

5.  從可用進程清單中選擇相應的容器進程，然後選擇 **"附加"** 以開始調試 C# 容器進程。


::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a>重新附加到進程

通過選擇**調試** > **重新附加到進程****（Shift**+**Alt**+**P），** 您可以快速重新附加到以前附加到的進程。 選擇此命令時，調試器將立即嘗試附加到附加到您附加到的最後一個進程，首先嘗試匹配以前的進程 ID，如果失敗，則與上一個進程名稱匹配。 如果未找到匹配項，或者多個進程具有相同的名稱，則將打開 **"附加到進程**"對話方塊，以便您可以選擇正確的進程。

> [!NOTE]
> "**重新附加到進程"** 命令可從 Visual Studio 2017 中開始。

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a>常見的調試方案

為了説明您確定是否使用 **"附加到進程**"以及要附加到的進程，下表顯示了一些常見的調試方案，其中包含指向更多說明的連結（如果可用）。 （該清單並非詳盡無遺。

對於某些應用類型（如通用 Windows 應用 （UWP） 應用），您不會直接附加到進程名稱，而是在 Visual Studio 中使用 **"調試已安裝的應用包**"功能表選項（請參閱表）。

偵錯工具若要附加至以 C++ 撰寫的程式碼，該程式碼必須發出 `DebuggableAttribute`。 您可以使用 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) 連結器選項連結，將其自動加入程式碼。

對於用戶端腳本調試，必須在瀏覽器中啟用腳本調試。 要在 Chrome 上調試用戶端腳本，請選擇**Web 工具組**作為代碼類型，並且根據您的應用類型，您可能需要關閉所有 Chrome 實例並在偵錯模式下啟動瀏覽器（從命令列鍵入`chrome.exe --remote-debugging-port=9222`）。

要快速選擇要附加到的視覺工作室中的正在運行的進程，請在"視覺工作室"中鍵入**Ctrl**+**Alt**+**P，** 然後鍵入進程名稱的第一個字母。

|狀況|調試方法|程序名稱|備註和連結|
|-|-|-|-|
|iIS 伺服器上的遠端偵錯ASP.NET 4 或 4.5|使用遠端工具並**附加到流程**|*w3wp.exe*|請參閱[遠端 IIS 電腦上的遠端偵錯ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|IIS 伺服器上的遠端偵錯ASP.NET核心|使用遠端工具並**附加到流程**|*點net.exe*或*應用程式名稱.exe*|有關應用部署，請參閱[發佈到 IIS](https://docs.asp.net/en/latest/publishing/iis.html)。 有關調試，請參閱[遠端 IIS 電腦上的遠端偵錯ASP.NET核心](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|調試本地 IIS 伺服器上的用戶端腳本，用於受支援的應用類型 |使用**附加到流程**|*chrome.exe，**微軟EdgeCP.exe，* 或*iexplore.exe*|必須啟用腳本調試。 對於 Chrome，您還必須在偵錯模式下運行 Chrome，並在 **"附加到**"欄位中選擇**Webkit 代碼**。|
|在本地電腦上調試 C#、可視基礎或C++應用|使用標準調試 （**F5**） 或**附加到進程**|*\<應用程式名稱>.exe*|在大多數情況下，使用標準調試而不是**附加到進程**。|
|遠端偵錯 Windows 桌面應用|遠端工具|N/A| 請參閱[遠端偵錯 C# 或視覺化基本應用](../debugger/remote-debugging-csharp.md)或[遠端偵錯C++應用](../debugger/remote-debugging-cpp.md)|
|調試 .NET Linux 上的內核|使用**附加到流程**|*dotnet.exe*|要使用 SSH，請參閱[使用 SSH 在 Linux 上運行的遠端偵錯 .NET 內核](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)。 |
|在沒有調試器的情況下啟動應用後，在本地電腦上調試ASP.NET應用|使用**附加到流程**|*iiexpress.exe*|這可能有助於使應用載入速度更快，例如（例如）分析時。 |
|在伺服器進程中調試其他受支援的應用類型|如果伺服器是遠端的，請使用遠端工具並**附加到進程**|*鉻.exe，* *iexplore.exe，* 或其他過程|如有必要，請使用資源監視器來説明標識該過程。 請參閱[遠端偵錯](../debugger/remote-debugging.md)。|
|遠端偵錯通用 Windows 應用 （UWP）、OneCore、HoloLens 或 IoT 應用|針對已安裝的應用程式套件進行偵錯|N/A|請參閱[調試已安裝的應用包](debug-installed-app-package.md)，而不是使用**附加到進程**|
|調試通用 Windows 應用 （UWP）、OneCore、HoloLens 或 IoT 應用，而這些應用不是從視覺化工作室啟動的|針對已安裝的應用程式套件進行偵錯|N/A|請參閱[調試已安裝的應用包](debug-installed-app-package.md)，而不是使用**附加到進程**|

## <a name="use-debugger-features"></a>使用調試器功能

要在附加到進程時使用 Visual Studio 調試器的全部功能（如命中中斷點），應用必須完全符合本地源和符號。 也就是說，調試器必須能夠載入正確的[符號 （.pdb） 檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。 預設情況下，這需要調試生成。

對於遠端偵錯方案，必須在 Visual Studio 中打開原始程式碼（或原始程式碼的副本）。 遠端電腦上的已編譯應用二進位檔案必須與本地電腦上的相同版本。

在某些本地調試方案中，如果應用存在正確的符號檔，則可以在 Visual Studio 中調試，無法訪問源。 預設情況下，這需要調試生成。 有關詳細資訊，請參閱[指定符號和原始檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> 針對附加錯誤進行疑難排解
 當偵錯工具附加至執行中的處理序時，該處理序可以包含一種或多種程式碼類型。 偵錯工具可附加的程式碼類型會在 [選取程式碼類型] **** 對話方塊中顯示並供您選取。

 有時候，偵錯工具可以成功附加至一種程式碼類型，而無法附加至另一種程式碼類型。 如果您嘗試附加至遠端電腦上正在執行的處理序，可能會發生這種狀況。 遠端電腦可能為某些程式碼類型安裝了遠端偵錯元件，但沒有安裝其他程式碼類型的遠端偵錯元件。 如果您嘗試附加至兩個或多個處理序以進行直接的資料庫偵錯，也可能會發生這種狀況。 (SQL 偵錯僅支援附加至單一處理序)。

 如果調試器能夠附加到某些（但不是全部）代碼類型，則會看到一條消息，標識哪些類型未附加。

 如果偵錯工具成功附加到至少一種程式碼類型，您可以繼續偵錯該處理序。 您只能偵錯已附加成功的程式碼類型。 進程中的未附加代碼仍將運行，但您將無法設置中斷點、查看資料或對該代碼執行其他調試操作。

 如果想要有關調試器未能附加到代碼類型的更具體資訊，請嘗試僅重新附加到該代碼類型。

 **取得程式碼類型為何無法附加的相關資訊：**

1. 與處理序中斷連結。 在**調試**功能表上，選擇 **"全部分離**"。

1. 重新附加到進程，僅選擇未附加的代碼類型。

    1. 在 [附加至處理序]**** 對話方塊的 [可使用的處理序]**** 清單中，選取該處理序。

    2. 選取 [選取] ****。

    3. 在 [選取程式碼類型] **** 對話方塊中，選取 [偵錯這些程式碼類型] **** 以及之前附加失敗的程式碼類型。 取消選擇其他代碼類型。

    4. 選取 [確定]****。

    5. 在"**附加到進程"** 對話方塊中，選擇 **"附加**"。

    這時，該附加將完全失敗，您將取得特定的錯誤訊息。

## <a name="see-also"></a>另請參閱

- [對多重處理序進行偵錯](../debugger/debug-multiple-processes.md)
- [及時調試](../debugger/just-in-time-debugging-in-visual-studio.md)
- [遠端偵錯](../debugger/remote-debugging.md)
