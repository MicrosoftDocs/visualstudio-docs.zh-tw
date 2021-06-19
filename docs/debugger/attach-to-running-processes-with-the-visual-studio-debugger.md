---
title: 使用偵錯工具附加至執行中處理序
description: 探索如何將 Visual Studio 偵錯工具附加到本機或遠端電腦上執行中的進程。
ms.custom: SEO-VS-2020
ms.date: 06/12/2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e3836403af80d06a2ecaa7f77cb7f49f0c6f0e8
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389783"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>使用 Visual Studio 偵錯工具附加至執行中處理序

您可以將 Visual Studio 偵錯工具附加至本機或遠端電腦上執行的處理序。 在程式執行之後，選取 [ **Debug**  >  **附加至進程**] 或在 Visual Studio 中按下 **Ctrl** + **Alt** + **p** ，然後使用 [**附加至進程**] 對話方塊，將偵錯工具附加至進程。

您可以使用 [ **附加至進程** ]，在本機或遠端電腦上偵測執行中的應用程式、同時調試多個進程、將未在 Visual Studio 中建立的應用程式進行偵錯工具，或將您未從 Visual Studio 啟動的任何應用程式進行偵錯工具。 例如，如果您在沒有偵錯工具的情況下執行應用程式，並遇到例外狀況，您可以將偵錯工具附加至執行應用程式的進程，並開始進行偵錯工具。

> [!TIP]
> 不確定是否要在您的偵錯工具案例中使用 **附加至進程** ？ 請參閱 [常見的調試案例](#BKMK_Scenarios)。

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> 附加至本機電腦上的執行中進程

若要快速重新附加至您先前附加的進程，請參閱重新 [附加至進程](#BKMK_reattach)。

**若要附加至本機電腦上的進程：**

1. 在 Visual Studio 中，選取 [ **Debug**  >  **附加至進程**] (或按 **Ctrl** + **Alt** + **P**) 以開啟 [**附加至進程**] 對話方塊。

1. 檢查 **連線類型**。

   在大部分的情況下，您可以使用 **預設值**。 某些案例可能需要不同的連線類型。 如需詳細資訊，請參閱本文中的其他章節或 [常見的偵錯工具案例](#BKMK_Scenarios)。

1. 將 **連接目標** 設定為本機電腦名稱稱。

   ![[附加至進程] 對話方塊的螢幕擷取畫面，其中的連接目標設定為本機電腦名稱稱。](../debugger/media/DBG_Basics_Attach_To_Process.png)

1. 在 [ **可使用的進程** ] 清單中，尋找並選取您想要附加的進程。

   - 若要快速選取處理常式，請在 [ **篩選進程** ] 方塊中輸入其名稱或第一個字母。

   - 如果您不知道進程名稱，請瀏覽清單，或查看一些常見進程名稱的 [常見調試](#BKMK_Scenarios) 程式。

   >[!TIP]
   >在 [ **附加至進程** ] 對話方塊開啟時，進程可以在背景中啟動和停止，因此執行中進程的清單可能不一定是最新狀態。 您可以隨時 **選取 [** 重新整理]，以查看目前的清單。

1. 在 [ **附加至** ] 欄位中，確定已列出您打算進行 debug 錯的程式碼類型。 預設的 **自動** 設定適用于大部分的應用程式類型。

   如果您使用 **預設** 的連線類型，則可以手動選取您要附加的程式碼類型。 否則，可能會停用 [ **選取** ] 選項。

   手動選取程式碼類型：
   1. 按一下 [選取]。
   1. 在 [ **選取程式碼類型** ] 對話方塊中，選取 [將 **這些程式碼類型進行調試** 程式]。
      如果您嘗試附加至清單中的進程時發生失敗，可以使用 [ [選取程式碼類型](../debugger/select-code-type-dialog-box.md) ] 對話方塊來協助 [疑難排解](#BKMK_Troubleshoot_attach_errors) 問題。
   1. 選取您要進行偵錯工具的程式碼類型。
   1. 選取 [確定]。

1. 選取 [附加]。

>[!NOTE]
>您可以附加至多個應用程式進行偵測，但偵錯工具一次只能有一個作用中的應用程式。 您可以在 [Visual Studio **Debug Location** ] 工具列或 [ **進程** ] 視窗中設定使用中的應用程式。

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> 附加至遠端電腦上的處理常式

您也可以在 [ **附加至進程** ] 對話方塊中選取遠端電腦、查看該電腦上執行的可用進程清單，然後附加至一個或多個處理常式以進行調試。 遠端電腦上必須執行遠端偵錯程式 (*msvsmon.exe*) 。 如需詳細資訊，請參閱 [遠端偵錯](../debugger/remote-debugging.md)程式。

如需有關將已部署至 IIS 的 ASP.NET 應用程式進行偵錯工具的更完整指示，請參閱 [遠端 IIS 電腦上的遠端偵錯程式 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。

**若要附加至遠端電腦上執行中的進程：**

1. 在 Visual Studio 中，選取 [ **Debug**  >  **附加至進程**] (或按 **Ctrl** + **Alt** + **P**) 以開啟 [**附加至進程**] 對話方塊。

1. 檢查 **連線類型**。

   在大部分的情況下，您可以使用 **預設值**。 某些案例（例如，偵錯工具 Linux 或容器化應用程式）需要不同的連線類型。 如需詳細資訊，請參閱本文中的其他章節或 [常見的偵錯工具案例](#BKMK_Scenarios)。

1. 在 [ **連接目標** ] 方塊中，使用下列其中一種方法來選取遠端電腦：

   - 選取 [ **連接目標**] 旁的下拉箭號，然後從下拉式清單中選取電腦名稱稱。
   - 在 [ **連接目標** ] 方塊中輸入電腦名稱稱，然後按 **enter**。

     確認 Visual Studio 將必要的埠新增至電腦名稱稱，其格式如下： **\<remote computer name> :p 從排序 o**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > 如果您無法使用遠端電腦名稱稱進行連接，請嘗試使用 IP 和埠位址 (例如 `123.45.678.9:4022`) 。 4024是 Visual Studio 2019 x64 遠端偵錯程式的預設埠。 如需其他遠端偵錯程式埠指派，請參閱 [遠端偵錯程式埠指派](remote-debugger-port-assignments.md)。

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > 如果您無法使用遠端電腦名稱稱進行連接，請嘗試使用 IP 和埠位址 (例如 `123.45.678.9:4022`) 。 4022是 Visual Studio 2017 x64 遠端偵錯程式的預設埠。 如需其他遠端偵錯程式埠指派，請參閱 [遠端偵錯程式埠指派](remote-debugger-port-assignments.md)。

     ::: moniker-end

   - 選取 [**連接目標**] 方塊旁的 [**尋找**] 按鈕，以開啟 [**遠端連線**] 對話方塊。 [ **遠端** 連線] 對話方塊會列出您的本機子網上的所有裝置，或直接連接到您的電腦。 您可能需要在伺服器上 [開啟 UDP 埠 3702](../debugger/remote-debugger-port-assignments.md) 以探索遠端裝置。 選取您要的電腦或裝置，然後按一下 [ **選取**]。

   > [!NOTE]
   > **連線類型** 設定會在偵測會話之間保持存在。 只有在成功進行與該目標的偵錯工具時， **連接目標** 設定才會在偵測會話之間保存。

3. 按一下 **[** 重新整理] 以填入 **可用的進程** 清單。

    >[!TIP]
    >在 [ **附加至進程** ] 對話方塊開啟時，進程可以在背景中啟動和停止，因此執行中進程的清單可能不一定是最新狀態。 您可以隨時 **選取 [** 重新整理]，以查看目前的清單。

4. 在 [ **可使用的進程** ] 清單中，尋找並選取您想要附加的進程。

   - 若要快速選取處理常式，請在 [ **篩選進程** ] 方塊中輸入其名稱或第一個字母。

   - 如果您不知道進程名稱，請瀏覽清單，或查看一些常見進程名稱的 [常見調試](#BKMK_Scenarios) 程式。

   - 若要尋找在所有使用者帳戶下執行的進程，請選取 [ **顯示所有使用者的進程** ] 核取方塊。

     >[!NOTE]
     >如果您嘗試附加至未受信任的使用者帳戶所擁有的處理序，會出現安全性警告對話方塊確認訊息。 如需詳細資訊，請參閱 [安全性警告：附加至不受信任的使用者所擁有的進程可能會造成危險。如果下列資訊看起來很可疑，或您不確定，請不要附加至此進程](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)。

5. 在 [ **附加至** ] 欄位中，確定已列出您打算進行 debug 錯的程式碼類型。 預設的 **自動** 設定適用于大部分的應用程式類型。

   如果您使用 **預設** 的連線類型，則可以手動選取您要附加的程式碼類型。 否則，可能會停用 [ **選取** ] 選項。

   手動選取程式碼類型：
   1. 按一下 [選取]。
   1. 在 [ **選取程式碼類型** ] 對話方塊中，選取 [將 **這些程式碼類型進行調試** 程式]。
      如果您嘗試附加至清單中的進程時發生失敗，可以使用 [ [選取程式碼類型](../debugger/select-code-type-dialog-box.md) ] 對話方塊來協助 [疑難排解](#BKMK_Troubleshoot_attach_errors) 問題。
   1. 選取 [確定]。

6. 選取 [附加]。

>[!NOTE]
>您可以附加至多個應用程式進行偵測，但偵錯工具一次只能有一個作用中的應用程式。 您可以在 [Visual Studio **Debug Location** ] 工具列或 [ **進程** ] 視窗中設定使用中的應用程式。

在某些情況下，當您在遠端桌面 (終端機服務) 會話中進行偵錯工具時，[ **可使用的進程** ] 清單不會顯示所有可用的進程。 如果您是以受限使用者帳戶的使用者身分執行 Visual Studio，[ **可使用的進程** ] 清單不會顯示在會話0中執行的進程。 會話0用於服務和其他伺服器進程，包括 *w3wp.exe*。 您可藉由使用系統管理員帳戶來執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，或是從伺服器主控台 (而非終端機服務工作階段) 執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，來解決這個問題。

如果這些解決方法都沒有效，則第三個選項是從 Windows 命令列執行 `vsjitdebugger.exe -p <ProcessId>` 以附加至處理序。 您可以使用 *tlist.exe* 來決定處理序識別碼。 若要取得 *tlist.exe*，您可以從 [WDK 和 WinDbg 下載](/windows-hardware/drivers/download-the-wdk)來下載並安裝適用於 Windows 的偵錯工具。

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>使用 SSH 附加至在 Linux 上執行的 .NET Core 進程

如需詳細資訊，請參閱 [使用 SSH 在 Linux 上執行的遠端偵錯程式 .Net Core](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)。

::: moniker range=">= vs-2019"

## <a name="attach-to-a-process-running-on-a-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a> 附加至在 Docker 容器上執行的進程

從 Visual Studio 2019 開始，您可以將 Visual Studio 偵錯工具附加至在 Docker 容器上執行的進程。 針對 Linux .NET Core Docker 容器，請參閱 [附加至在 Linux Docker 容器上執行的進程](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container)。 若為 Windows Docker 容器，請參閱 [附加至在 Windows docker 容器上執行的進程](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-windows-docker-container)。

::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a> 重新附加至進程

您可以藉由選擇 [ **Debug** 重新  >  **附加至進程**] (**Shift** + **Alt** + **P**) ，快速重新附加至您先前附加的進程。 當您選擇此命令時，偵錯工具會立即嘗試附加至您附加的最後一個處理常式，方法是先嘗試比對先前的處理序識別碼，如果失敗，則比對先前的進程名稱。 如果找不到相符專案，或有數個進程具有相同的名稱，將會開啟 [ **附加至進程** ] 對話方塊，讓您可以選取正確的進程。

> [!NOTE]
> 從 Visual Studio 2017 開始，可以使用 [重新 **附加至進程** ] 命令。

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> 常見的調試案例

為了協助您判斷是否要使用 [ **附加至進程** ] 以及要附加的進程，下表顯示一些常見的偵錯工具，並提供更多指示的連結。  (清單不完整。 ) 

針對某些應用程式類型（例如 (UWP) 應用程式的通用 Windows 應用程式），您不會直接附加至進程名稱，但請改用 Visual Studio 中的 [ **已安裝的應用程式套件** ] 功能表選項 (查看資料表) 。

偵錯工具若要附加至以 C++ 撰寫的程式碼，該程式碼必須發出 `DebuggableAttribute`。 您可以使用 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) 連結器選項連結，將其自動加入程式碼。

針對用戶端腳本的偵錯工具，您必須在瀏覽器中啟用腳本偵錯工具。 若要在 Chrome 上偵測用戶端腳本，請選擇 **javascript (chrome)** 或 **javascript (Microsoft Edge-Chromium)** 作為程式碼類型，並視您的應用程式類型而定，您可能需要關閉所有 Chrome 實例，並在偵錯工具模式中， `chrome.exe --remote-debugging-port=9222` 從命令列 (的類型啟動瀏覽器) 。 在舊版 Visual Studio 中，Chrome 的腳本偵錯工具是 **Web 套件**。

若要快速選取要附加的執行中進程，請在 [Visual Studio 中輸入 **Ctrl** + **Alt** + **P**，然後輸入進程名稱的第一個字母。

|狀況|Debug 方法|程序名稱|附注和連結|
|-|-|-|-|
|IIS 伺服器上的遠端偵錯程式 ASP.NET 4 或4。5|使用遠端工具並 **附加至進程**|*w3wp.exe*|請參閱遠端 [IIS 電腦上的遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|IIS 伺服器上的遠端 debug ASP.NET Core|使用遠端工具並 **附加至進程**|*w3wp.exe* 或 *dotnet.exe*|從 .NET Core 3 開始， *w3wp.exe* 進程會用於預設的 [應用程式內裝載模型](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models)。 如需應用程式部署，請參閱 [發行至 IIS](/aspnet/core/host-and-deploy/iis/)。 如需詳細資訊，請參閱 [遠端 IIS 電腦上的遠端偵錯程式 ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach)|
|針對支援的應用程式類型在本機 IIS 伺服器上進行用戶端腳本的偵錯工具 |使用 **附加至進程**|*chrome.exe*、 *MicrosoftEdgeCP.exe* 或 *iexplore.exe*|必須啟用腳本調試。 若是 Chrome，您也必須從命令列執行 Chrome in debug 模式 (類型 `chrome.exe --remote-debugging-port=9222`) ，然後在 [**附加至**] 欄位中選取 [ **JavaScript (Chrome)** ]。|
|在本機電腦上進行 c #、Visual Basic 或 c + + 應用程式的偵錯工具|使用標準的偵錯工具 (**F5**) 或 **附加至進程**|*\<appname>.exe*|在大部分的情況下，請使用標準的偵錯工具，而不是 **附加至進程**。|
|遠端偵錯 Windows 傳統型應用程式|遠端工具|N/A| 請參閱 [遠端偵測 c # 或 Visual Basic 應用程式](../debugger/remote-debugging-csharp.md) 或 [遠端偵錯程式 c + + 應用程式](../debugger/remote-debugging-cpp.md)|
|在 Linux 上對 .NET Core 偵錯|使用 **附加至進程**|*dotnet.exe* 或唯一的進程名稱|若要使用 SSH，請參閱 [使用 ssh 在 Linux 上執行的遠端偵錯 .Net Core](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)。 針對容器化應用程式，請參閱 [附加至在 Docker 容器中執行的進程](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container)。|
|對容器化應用程式進行 Debug|使用 **附加至進程**|*dotnet.exe* 或唯一的進程名稱|請參閱 [附加至在 Docker 容器中執行的進程](../debugger/attach-to-process-running-in-docker-container.md)|
|Linux 上的遠端 debug Python|使用 **附加至進程**|*debugpy*|請參閱 [從 Python 工具遠端附加](../python/debugging-python-code-on-remote-linux-machines.md#attach-remotely-from-python-tools)|
|在沒有偵錯工具的情況下啟動應用程式之後，在本機電腦上進行 ASP.NET 應用程式的偵錯工具|使用 **附加至進程**|*iiexpress.exe*|這有助於讓您的應用程式載入更快，例如在分析時 (例如) 。 |
|在伺服器進程上進行其他支援的應用程式類型的偵錯工具|如果伺服器在遠端，請使用遠端工具，並 **附加至進程**|*chrome.exe*、 *iexplore.exe* 或其他進程|如有必要，請使用資源監視器來協助識別進程。 請參閱[遠端偵錯](../debugger/remote-debugging.md)。|
|將通用 Windows 應用程式遠端偵錯 (UWP) 、OneCore、HoloLens 或 IoT 應用程式|針對已安裝的應用程式套件進行偵錯|N/A|請參閱 [Debug 已安裝的應用程式套件](debug-installed-app-package.md) ，而不是使用 **附加至進程**|
|將通用 Windows 應用程式 (UWP) 、OneCore、HoloLens 或未從 Visual Studio 啟動的 IoT 應用程式進行偵錯工具|針對已安裝的應用程式套件進行偵錯|N/A|請參閱 [Debug 已安裝的應用程式套件](debug-installed-app-package.md) ，而不是使用 **附加至進程**|

## <a name="use-debugger-features"></a>使用偵錯工具功能

若要使用 Visual Studio 偵錯工具的完整功能 (例如在附加至進程時) 叫用中斷點，應用程式必須完全符合您的本機來源和符號。 也就是，偵錯工具必須能夠載入正確的 [符號 ( .pdb) ](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)檔。 根據預設，這需要 debug 組建。

在遠端偵錯程式案例中，您必須將原始程式碼 (或原始程式碼的複本) 已在 Visual Studio 中開啟。 遠端電腦上已編譯的應用程式二進位檔必須來自于本機電腦上的相同組建。

在某些本機的偵錯工具案例中，如果應用程式有正確的符號檔，您就可以在 Visual Studio 中進行 debug，而不需要存取來源。 根據預設，這需要 debug 組建。 如需詳細資訊，請參閱 [指定符號和原始](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)程式檔。

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> 針對附加錯誤進行疑難排解

在某些情況下，偵錯工具可能需要協助以正確地識別要進行偵錯工具的程式碼類型。 如果連接值已正確設定 (您可以在 [ **可使用的進程** ] 清單中查看正確的程式) ，但偵錯工具無法附加，請嘗試在 [ **連線類型** ] 清單中選取最適當的連線類型（例如，如果您要對 Linux 或 Python 應用程式進行偵錯工具）。 如果您使用預設的連線類型，則您也可以選取要連接的特定程式碼類型，如本節稍後所述。

當偵錯工具附加至執行中的處理序時，該處理序可以包含一種或多種程式碼類型。 偵錯工具可附加的程式碼類型會在 [選取程式碼類型] [](../debugger/select-code-type-dialog-box.md) 對話方塊中顯示並供您選取。

有時候，偵錯工具可以成功附加至一種程式碼類型，而無法附加至另一種程式碼類型。 一般來說，這會在下列情況發生：

- 您嘗試附加至遠端電腦上執行的處理常式。 遠端電腦可能為某些程式碼類型安裝了遠端偵錯元件，但沒有安裝其他程式碼類型的遠端偵錯元件。
- 您嘗試附加至兩個或多個進程，以進行直接資料庫的偵錯工具。 (SQL 偵錯僅支援附加至單一處理序)。

如果偵錯工具可以附加至部分（但不是全部）程式碼類型，您會看到一則訊息，指出哪些類型無法附加。

如果偵錯工具成功附加到至少一種程式碼類型，您可以繼續偵錯該處理序。 您只能偵錯已附加成功的程式碼類型。 進程中未附加的程式碼仍會執行，但您將無法在該程式碼上設定中斷點、查看資料或執行其他的偵錯工具。

如果您想要更多有關偵錯工具無法附加至程式碼類型的特定資訊，請嘗試只重新附加至該程式碼類型。

**取得程式碼類型為何無法附加的相關資訊：**

1. 與處理序中斷連結。 在 [ **調試** ] 功能表上選取 [ **全部卸離**]。

1. 重新附加至進程，並只選取無法附加的程式碼類型。

    1. 在 [附加至處理序] 對話方塊的 [可使用的處理序] 清單中，選取該處理序。

    2. 選取 [選取]  。

    3. 在 [選取程式碼類型]  對話方塊中，選取 [偵錯這些程式碼類型]  以及之前附加失敗的程式碼類型。 取消選取其他程式碼類型。

    4. 選取 [確定]。

    5. 在 [ **附加至進程** ] 對話方塊中，選取 [ **附加**]。

    這時，該附加將完全失敗，您將取得特定的錯誤訊息。

## <a name="see-also"></a>另請參閱

- [對多重處理序進行偵錯](../debugger/debug-multiple-processes.md)
- [即時調試](../debugger/just-in-time-debugging-in-visual-studio.md)
- [遠端偵錯](../debugger/remote-debugging.md)
