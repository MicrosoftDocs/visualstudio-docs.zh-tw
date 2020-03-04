---
title: 使用偵錯工具附加至執行中進程 |Microsoft Docs
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
ms.openlocfilehash: f2f00cde0c2ea3fad79c0f5ef75f3c33ad7afc22
ms.sourcegitcommit: c98e0ccf236765b44e47095ee52836cb012e3854
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2020
ms.locfileid: "78257185"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>使用 Visual Studio 偵錯工具附加至執行中處理序
您可以將 Visual Studio 偵錯工具附加至本機或遠端電腦上執行的處理序。 在進程執行之後，請選取 [ **Debug** ] > [**附加至進程**]，或在 Visual Studio 中按**Ctrl**+**Alt**+**P** ，然後使用 [**附加至進程**] 對話方塊，將偵錯工具附加至進程。

您可以使用 [**附加至進程**]，在本機或遠端電腦上對執行中的應用程式進行偵測、同時進行多個進程的偵錯工具、在 Visual Studio 中未建立的偵錯工具，或從已附加偵錯工具 Visual Studio 的任何應用程式進行 debug。 例如，如果您在沒有偵錯工具的情況下執行應用程式，並遇到例外狀況，您可以接著將偵錯工具附加至執行應用程式的進程，並開始進行偵錯工具。

> [!TIP]
> 不確定是否要針對您的偵錯工具使用 [**附加至進程**]？ 請參閱[常見的調試情況](#BKMK_Scenarios)。

## <a name="BKMK_Attach_to_a_running_process"></a>附加至本機電腦上正在執行的進程

若要快速重新附加至您先前附加的進程，請參閱重新[附加至進程](#BKMK_reattach)。

若要在遠端電腦上進行處理常式的偵錯工具，請參閱[附加至遠端電腦上的進程](#BKMK_Attach_to_a_process_on_a_remote_computer)。

::: moniker range=">= vs-2019"
若要在 Linux Docker 容器上進行 .NET Core 程式的偵錯工具，請參閱[附加至 Linux docker 容器](#BKMK_Docker_Attach)。
::: moniker-end

**若要附加至本機電腦上的處理常式：**

1. 在 Visual Studio 中，選取  **Debug** > **附加至進程** （或按**Ctrl**+**Alt**+**P**）以開啟 **附加至進程** 對話方塊。

   **連線類型**應該設定為 [**預設**]。 **連接目標**應該是您的本機電腦名稱稱。

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. 在 [**可使用的進程**] 清單中，尋找並選取您想要附加的進程。

   - 若要快速選取進程，請在 [**篩選器處理**程式] 方塊中輸入其名稱或第一個字母。

   - 如果您不知道進程名稱，請瀏覽清單，或查看一些常見進程名稱的[常見偵錯工具案例](#BKMK_Scenarios)。

   >[!TIP]
   >當 [**附加至進程**] 對話方塊開啟時，進程可以在背景啟動和停止，因此執行中的進程清單可能不一定是最新狀態。 您可以隨時**選取 [** 重新整理]，以查看目前的清單。

3. 在 [**附加至**] 欄位中，請確定您計畫要進行 debug 的程式碼類型已列出。 預設的**自動**設定適用于大部分的應用程式類型。

   若要手動選取程式碼類型：
   1. 按一下 [選取]。
   1. 在 [**選取程式碼類型**] 對話方塊中，選取 [**偵錯工具代碼類型**]。
   1. 選取您要進行偵錯工具的程式碼類型。
   1. 選取 [確定]。

4. 選取 [附加]。

>[!NOTE]
>您可以附加至多個應用程式進行調試，但一次只能有一個應用程式在偵錯工具中作用。 您可以在 [Visual Studio **Debug 位置**] 工具列或 [**進程**] 視窗中設定使用中的應用程式。

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> 附加至遠端電腦上的處理序

您也可以在 [**附加至進程**] 對話方塊中選取遠端電腦、查看該電腦上執行之可用進程的清單，以及附加至一或多個處理常式進行調試。 遠端偵錯程式（*msvsmon*）必須在遠端電腦上執行。 如需詳細資訊，請參閱[遠端偵錯](../debugger/remote-debugging.md)程式。

如需更多有關 ASP.NET 已部署至 IIS 之應用程式的完整指示，請參閱遠端[IIS 電腦上的遠端偵錯程式 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。

**若要附加至遠端電腦上執行中的進程：**

1. 在 Visual Studio 中，選取  **Debug** > **附加至進程** （或按**Ctrl**+**Alt**+**P**）以開啟 **附加至進程** 對話方塊。

2. 在大部分情況下，**連線類型**都應該是**預設值**。 在 [**連接目標**] 方塊中，使用下列其中一種方法來選取遠端電腦：

   - 選取 [**連接目標**] 旁的下拉式箭號，然後從下拉式清單中選取電腦名稱稱。
   - 在 [**連接目標**] 方塊中輸入電腦名稱稱，然後按**enter**。

     確認 Visual Studio 將所需的埠新增至電腦名稱稱，其格式會是： **\<遠端電腦名稱稱 >:p 埠 o**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > 如果您無法使用遠端電腦名稱稱進行連接，請嘗試使用 IP 和埠位址（例如 `123.45.678.9:4022`）。 4024是 Visual Studio 2019 x64 遠端偵錯程式的預設通訊埠。 如需其他遠端偵錯程式埠指派，請參閱[遠端偵錯程式埠指派](remote-debugger-port-assignments.md)。

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > 如果您無法使用遠端電腦名稱稱進行連接，請嘗試使用 IP 和埠位址（例如 `123.45.678.9:4022`）。 4022是 Visual Studio 2017 x64 遠端偵錯程式的預設通訊埠。 如需其他遠端偵錯程式埠指派，請參閱[遠端偵錯程式埠指派](remote-debugger-port-assignments.md)。

     ::: moniker-end

   - 選取 [連線**目標**] 方塊旁的 [**尋找**] 按鈕，以開啟 [**遠端連線**] 對話方塊。 [**遠端**連線] 對話方塊會列出位於您的本機子網上的所有裝置，或直接連接到您的電腦。 您可能需要在伺服器上[開啟 UDP 埠 3702](../debugger/remote-debugger-port-assignments.md) ，以探索遠端裝置。 選取您想要的電腦或裝置，然後按一下 [**選取**]。

   > [!NOTE]
   > [連線**類型**] 設定會在 [調試] 會話之間保持保存。 只有在與該目標進行成功的偵錯工具連線時，才會在偵測會話之間保存**連接目標**設定。

3. 按一下 **[** 重新整理] 以填入 [**可使用的進程**] 清單。

    >[!TIP]
    >當 [**附加至進程**] 對話方塊開啟時，進程可以在背景啟動和停止，因此執行中的進程清單可能不一定是最新狀態。 您可以隨時**選取 [** 重新整理]，以查看目前的清單。

4. 在 [**可使用的進程**] 清單中，尋找並選取您想要附加的進程。

   - 若要快速選取進程，請在 [**篩選器處理**程式] 方塊中輸入其名稱或第一個字母。

   - 如果您不知道進程名稱，請瀏覽清單，或查看一些常見進程名稱的[常見偵錯工具案例](#BKMK_Scenarios)。

   - 若要尋找在所有使用者帳戶下執行的處理常式，請選取 [**顯示所有使用者的進程**] 核取方塊。

     >[!NOTE]
     >如果您嘗試附加至未受信任的使用者帳戶所擁有的處理序，會出現安全性警告對話方塊確認訊息。 如需詳細資訊，請參閱[安全性警告： 附加至不受信任的使用者所擁有的處理序可能會造成危險。如果下列資訊看起來有問題，或您不確定，不會附加至這個處理序](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)。

5. 在 [**附加至**] 欄位中，請確定您計畫要進行 debug 的程式碼類型已列出。 預設的**自動**設定適用于大部分的應用程式類型。

   若要手動選取程式碼類型：
   1. 按一下 [選取]。
   1. 在 [**選取程式碼類型**] 對話方塊中，選取 [**偵錯工具代碼類型**]。
   1. 選取您要進行偵錯工具的程式碼類型。
   1. 選取 [確定]。

6. 選取 [附加]。

>[!NOTE]
>您可以附加至多個應用程式進行調試，但一次只能有一個應用程式在偵錯工具中作用。 您可以在 [Visual Studio **Debug 位置**] 工具列或 [**進程**] 視窗中設定使用中的應用程式。

在某些情況下，當您在遠端桌面（終端機服務）會話中進行偵錯工具時，[**可使用的進程**] 清單不會顯示所有可用的進程。 如果您是以限制使用者帳戶的使用者身分執行 Visual Studio，[**可使用的進程**] 清單不會顯示在會話0中執行的處理常式。 會話0用於服務和其他伺服器進程，包括*w3wp.exe。* 您可藉由使用系統管理員帳戶來執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，或是從伺服器主控台 (而非終端機服務工作階段) 執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，來解決這個問題。

如果這些解決方法都沒有效，則第三個選項是從 Windows 命令列執行 `vsjitdebugger.exe -p <ProcessId>` 以附加至處理序。 您可以使用*tlist.exe*來判斷處理序識別碼。 若要取得 *tlist.exe*，您可以從 [WDK 和 WinDbg 下載](/windows-hardware/drivers/download-the-wdk)來下載並安裝適用於 Windows 的偵錯工具。

::: moniker range=">= vs-2019"

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>使用 SSH 附加至在 Linux 上執行的 .NET Core 進程

如需詳細資訊，請參閱[使用 SSH 在 Linux 上執行的遠端偵錯程式 .Net Core](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)。

## <a name="BKMK_Docker_Attach"></a>附加至在 Linux Docker 容器上執行的進程

您可以使用 [**附加至進程**] 對話方塊，將 Visual Studio 偵錯工具附加至本機或遠端電腦上的 Linux .Net Core Docker 容器中執行的進程。

> [!IMPORTANT]
> 若要使用這項功能，您必須安裝 .NET Core 跨平臺開發工作負載，並具有原始程式碼的本機存取權。

**若要附加至 Linux Docker 容器中的執行中進程：**

1. 在 Visual Studio 中，選取  **Debug > 附加至進程 （CTRL + ALT + P）** 以開啟 **附加至進程** 對話方塊。

![附加至進程功能表](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. 將 [連線**類型**] 設定為 [ **Docker （Linux 容器）** ]。
3. 選取 [**尋找**]，以透過 [**選取 Docker 容器**] 對話方塊來設定連線**目標**。

    您可以在本機或遠端對 Docker 容器進程進行偵錯工具。
    
    **若要在本機上對 Docker 容器進程進行偵錯工具：**
    1. 將**DOCKER CLI 主機**設定為 [**本機電腦**]。
    1. 從清單中選取要附加的執行中容器，然後按 **[確定]** 。
    
    ![選取 Docker 容器功能表](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. 遠端執行 Docker 容器進程的偵錯工具：**
    
    > [!NOTE] 
    > 有兩個選項可讓您從遠端連線到 Docker 容器中的執行中進程。 如果您的本機電腦上未安裝 Docker 工具，第一個選項 [若要使用 SSH] 是理想的選擇。  如果您已在本機安裝 Docker 工具，而且您有已設定為接受遠端要求的 Docker daemon，請使用 Docker daemon 嘗試第二個選項。

    1. ***透過 SSH 連接到遠端電腦：***
        1. 選取 [**新增 ...** ] 以連線到遠端系統。<br/>
        ![連接到遠端系統](../debugger/media/connect-remote-system.png "連接到遠端系統")
        1. 成功連線到 SSH 或背景程式後，選取要附加的執行中容器，然後按 **[確定]** 。

    
    1. ***若要將目標設定為透過[Docker daemon](https://docs.docker.com/engine/reference/commandline/dockerd/)執行進程的遠端容器***
        1. 在 [ **Docker 主機（選擇性）** ] 底下指定 [背景程式位址] （也就是透過 TCP、IP 等），然後按一下 [重新整理] 連結。
        1. 成功連接到背景程式後，選取要附加的執行中容器，然後按 **[確定]** 。

4. 從**可用的進程**清單中選擇對應的容器進程，然後選取 [**附加**] 以C#開始在 Visual Studio 中偵測您的容器進程！

    ![完成的 Docker 附加功能表](../debugger/media/docker-attach-complete.png "完成的 Docker 附加功能表")


::: moniker-end

## <a name="BKMK_reattach"></a>重新附加至進程

您可以藉由選擇 [ **Debug** ] > [重新**附加至進程**] （**Shift**+**Alt**+**P**），快速地重新附加至先前附加的進程。 當您選擇此命令時，偵錯工具會先嘗試比對先前的處理序識別碼，如果失敗，則會比對先前的進程名稱，以立即嘗試附加至您附加的最後一個進程。 如果找不到相符專案，或有數個進程具有相同的名稱，則會開啟 [**附加至進程**] 對話方塊，讓您可以選取正確的進程。

> [!NOTE]
> 從 Visual Studio 2017 開始可使用 [重新**附加至進程**] 命令。

## <a name="BKMK_Scenarios"></a>常見的調試情況

為了協助您判斷是否要使用 [**附加至進程**] 以及要附加到哪個進程，下表顯示一些常見的偵錯工具案例，並提供更多可用的指示連結。 （清單並不完整）。

對於某些應用程式類型（例如通用 Windows App （UWP）應用程式），您不會直接附加至進程名稱，而是改為使用 Visual Studio 中的 [**已安裝的應用程式套件**] 功能表選項（請參閱表格）。

偵錯工具若要附加至以 C++ 撰寫的程式碼，該程式碼必須發出 `DebuggableAttribute`。 您可以使用 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) 連結器選項連結，將其自動加入程式碼。

針對用戶端腳本的偵錯工具，必須在瀏覽器中啟用腳本的偵錯工具。 若要在 Chrome 上進行用戶端腳本的偵錯工具，請選擇 [ **Web 套件**] 做為程式碼類型，然後視您的應用程式類型而定，您可能需要關閉所有 Chrome 實例，並在 [調試] 模式中啟動瀏覽器（從命令列輸入 `chrome.exe --remote-debugging-port=9222`）。

若要快速選取要附加的執行中進程，請在 Visual Studio 中，輸入**Ctrl**+**Alt**+**P**，然後輸入處理常式名稱的第一個字母。

|狀況|Debug 方法|程序名稱|附注和連結|
|-|-|-|-|
|IIS 伺服器上的 Remote debug ASP.NET 4 或4。5|使用遠端工具並**附加至進程**|*w3wp.exe*|請參閱遠端[IIS 電腦上的遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|IIS 伺服器上的遠端偵錯程式 ASP.NET Core|使用遠端工具並**附加至進程**|*dotnet .exe*或*appname .exe*|如需應用程式部署，請參閱[發行至 IIS](https://docs.asp.net/en/latest/publishing/iis.html)。 如需偵錯工具，請參閱遠端[IIS 電腦上的遠端偵錯程式 ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|在本機 IIS 伺服器上，針對支援的應用程式類型進行用戶端腳本的偵錯工具 |使用 [**附加至進程**]|*chrome .exe*、 *MicrosoftEdgeCP*或*iexplore.exe .exe*|必須啟用腳本的調試。 對於 Chrome，您也必須在 [偵錯工具] 模式中執行 Chrome，然後在 [**附加至**] 欄位中選取 [ **Webkit 程式碼**]。|
|在本機C#電腦上的 Debug C++ a、Visual Basic 或 app|使用標準的偵錯工具（**F5**）或 [**附加至進程**]|*應用程式名稱>\<.exe*|在大部分的情況下，請使用標準的偵錯工具，而不是**附加至進程**。|
|對 Windows 傳統型應用程式進行遠端 debug|遠端工具|N/A| 請參閱[遠端 debug C# a 或 Visual Basic 應用程式](../debugger/remote-debugging-csharp.md)或[遠端C++偵錯工具](../debugger/remote-debugging-cpp.md)|
|在 Linux 上對 .NET Core 進行調試|使用 [**附加至進程**]|*dotnet.exe*|若要使用 SSH，請參閱[使用 ssh 在 Linux 上執行的遠端偵錯 .Net Core](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)。 |
|在不使用偵錯工具的情況下啟動應用程式之後，在本機電腦上進行 ASP.NET 應用程式的偵錯工具|使用 [**附加至進程**]|*iiexpress.exe*|這可能有助於讓應用程式的載入速度更快，例如在分析時（例如）。 |
|在伺服器進程上，對其他支援的應用程式類型進行偵錯工具|如果伺服器在遠端，請使用遠端工具，然後**附加至進程**|*chrome .exe*、 *iexplore.exe*或其他進程|如有必要，請使用資源監視器來協助識別進程。 請參閱[遠端偵錯](../debugger/remote-debugging.md)。|
|遠端 debug a 通用 Windows App （UWP）、OneCore、HoloLens 或 IoT 應用程式|針對已安裝的應用程式套件進行偵錯|N/A|請參閱[Debug 已安裝的應用程式套件](debug-installed-app-package.md)，而不是使用 [**附加至進程**]|
|針對您未從 Visual Studio 啟動的通用 Windows 應用程式（UWP）、OneCore、HoloLens 或 IoT 應用程式進行 Debug|針對已安裝的應用程式套件進行偵錯|N/A|請參閱[Debug 已安裝的應用程式套件](debug-installed-app-package.md)，而不是使用 [**附加至進程**]|

## <a name="use-debugger-features"></a>使用偵錯工具功能

若要在附加至進程時使用 Visual Studio 偵錯工具的完整功能（例如命中中斷點），應用程式必須完全符合您的本機來源和符號。 也就是說，偵錯工具必須能夠載入正確的[符號（.pdb）](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)檔案。 根據預設，這需要 debug 組建。

在遠端偵錯程式案例中，您必須已在 Visual Studio 中開啟原始碼（或原始程式碼的複本）。 遠端電腦上已編譯的應用程式二進位檔必須來自與本機電腦上相同的組建。

在某些本機的偵錯工具中，如果應用程式中有正確的符號檔，您可以在 Visual Studio 中進行 debug，而不需要存取來源。 根據預設，這需要 debug 組建。 如需詳細資訊，請參閱[指定符號和原始](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)程式檔。

## <a name="BKMK_Troubleshoot_attach_errors"></a> 針對附加錯誤進行疑難排解
 當偵錯工具附加至執行中的處理序時，該處理序可以包含一種或多種程式碼類型。 偵錯工具可附加的程式碼類型會在 [選取程式碼類型] 對話方塊中顯示並供您選取。

 有時候，偵錯工具可以成功附加至一種程式碼類型，而無法附加至另一種程式碼類型。 如果您嘗試附加至遠端電腦上正在執行的處理序，可能會發生這種狀況。 遠端電腦可能為某些程式碼類型安裝了遠端偵錯元件，但沒有安裝其他程式碼類型的遠端偵錯元件。 如果您嘗試附加至兩個或多個處理序以進行直接的資料庫偵錯，也可能會發生這種狀況。 (SQL 偵錯僅支援附加至單一處理序)。

 如果偵錯工具可以附加至部分（而非全部）的程式碼類型，您會看到一則訊息，指出哪些類型無法附加。

 如果偵錯工具成功附加到至少一種程式碼類型，您可以繼續偵錯該處理序。 您只能偵錯已附加成功的程式碼類型。 進程中未附加的程式碼仍會執行，但您將無法設定中斷點、查看資料，或對該程式碼執行其他的偵錯工具作業。

 如果您想要更多有關偵錯工具為何無法附加至程式碼類型的特定資訊，請嘗試只重新附加至該程式碼類型。

 **取得程式碼類型為何無法附加的相關資訊：**

1. 與處理序中斷連結。 在 [**調試**] 功能表上，選取 [卸**離全部**]。

1. 重新附加至進程，並只選取無法附加的程式碼類型。

    1. 在 [附加至處理序] 對話方塊的 [可使用的處理序] 清單中，選取該處理序。

    2. 選取 [選取]。

    3. 在 [選取程式碼類型] 對話方塊中，選取 [偵錯這些程式碼類型] 以及之前附加失敗的程式碼類型。 取消選取其他程式碼類型。

    4. 選取 [確定]。

    5. 在 [**附加至進程**] 對話方塊中，選取 [**附加**]。

    這時，該附加將完全失敗，您將取得特定的錯誤訊息。

## <a name="see-also"></a>另請參閱

- [對多重處理序進行偵錯](../debugger/debug-multiple-processes.md)
- [Just-In-Time 偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)
- [遠端偵錯](../debugger/remote-debugging.md)
