---
title: 使用偵錯工具附加至執行中進程 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
- C++
- CSharp
- FSharp
- VB
- c++
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 62
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf4d63d7d00e91daa2564992f801896075f73aab
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918938"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>使用 Visual Studio Debugger 附加至執行中處理序
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以將 Visual Studio 偵錯工具附加至本機或遠端電腦上執行的處理序。 在進程執行之後，按一下 [ **Debug]/[附加至進程**] （或按**CTRL + ALT + P**）以開啟 [**附加至進程**] 對話方塊。

您可以使用這項功能來對在本機或遠端電腦上執行的應用程式進行偵錯工具、同時進行多個進程的偵錯工具，或對 Visual Studio 中未建立的應用程式進行 debug。 當您想要對應用程式進行分析，但因為任何原因而未從附加偵錯工具的 Visual Studio 啟動應用程式時，這通常很有用。 例如，如果您在沒有偵錯工具的情況下執行應用程式，並遇到例外狀況，則您可能會附加至執行應用程式的進程以開始進行偵錯工具。

> [!TIP]
> 不確定您是否需要在您的偵錯工具案例中使用 [**附加至進程**]？ 請參閱[常見的調試情況](#BKMK_Scenarios)。 如果您想要對已部署至 IIS 的 ASP.NET 應用程式進行檢查，請參閱遠端[IIS 電腦上的遠端偵錯程式 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。

## <a name="BKMK_Attach_to_a_running_process"></a>附加至本機電腦上正在執行的進程
 若要附加至進程，您必須知道進程的名稱（請參閱[常見](#BKMK_Scenarios)的處理常式名稱）。

1. 在 Visual Studio 中，選取  **Debug/附加至進程** （或按**CTRL + ALT + P**）。

2. 請在 [附加至處理序] 對話方塊的 [可使用的處理序] 清單中，尋找您要附加的程式。

     若要快速選取您想要的處理常式，請輸入進程名稱的第一個字母。 如果您不知道進程名稱，請參閱[常見的偵錯工具案例](#BKMK_Scenarios)。

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     如果該處理序正在不同的使用者帳戶下執行，請選取 [顯示所有使用者的處理序] 核取方塊。

3. 在 [附加至] 方塊中，確定其中已列出您要偵錯的程式碼類型。 預設的 [自動] 設定會自動判斷您要偵錯的程式碼類型。 若要手動設定程式碼類型，請執行下列程序

    1. 按一下 [附加至] 方塊中的 [選取]。

    2. 在 [選取程式碼類型] 對話方塊中，按一下 [偵錯這些程式碼類型] ，然後選取要偵錯的類型。

    3. 按一下 [ **確定**]。

4. 按一下 [附加]。

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> 附加至遠端電腦上的處理序
 若要附加至進程，您必須知道進程的名稱（請參閱[常見](#BKMK_Scenarios)的處理常式名稱）。 如需 ASP.NET 已部署至 IIS 之應用程式的完整指引，請參閱遠端[IIS 電腦上的遠端偵錯程式 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。 若為其他應用程式，您或許可在 [工作管理員] 中找到處理序名稱。

 使用 [附加至處理序] 對話方塊時，您可以選取已針對遠端偵錯設定的其他電腦。 如需詳細資訊，請參閱[遠端偵錯](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)程式。 當您選取了遠端電腦時，您可以檢視該電腦上正在執行的可使用處理序清單，並附加至其中一個或多個處理序進行偵錯。

 **若要選取遠端電腦：**

1. 在 Visual Studio 中，選取  **Debug/附加至進程** （或按**CTRL + ALT + P**）。

2. 在 [附加至處理序] 對話方塊中，從 [傳輸] 清單選取適當的連接類型。 [預設值] 是適合大部分情況的正確設定

   [傳輸] 設定在偵錯工作階段之間持續維持。

3. 利用下列其中一種方法，使用 [限定詞] 清單方塊選擇遠端電腦名稱：

   1. 在 [限定詞] 清單方塊中輸入名稱。

      > [!NOTE]
      > 如果在稍後的步驟中，您無法使用遠端電腦名稱稱進行連接，請使用 IP 位址。 （選取進程之後，通訊埠編號可能會自動出現。 您也可以手動輸入。 在下圖中，4020是遠端偵錯程式的預設埠）。

   2. 按一下附加至 [限定詞] 清單方塊的下拉箭號，然後從下拉式清單中選取電腦名稱。

   3. 按一下 [**限定詞**] 清單旁的 [**尋找**] 按鈕，以開啟 [**選取遠端偵錯程式連接**] 對話方塊。 [選取遠端偵錯工具連接] 對話方塊會列出位於您本機子網路上的所有裝置，以及透過乙太網路纜線直接附加至電腦的裝置。 按一下您想要的電腦或裝置，然後按一下 [選取]。

      [限定詞] 設定只有在使用該限定詞成功產生偵錯連接時，才會在偵錯工作階段之間持續維持。

4. 按一下 [重新整理]。

     [可使用的處理序] 清單會在您開啟 [處理序] 對話方塊時自動顯示。 當對話方塊開啟時，處理序可以在背景中啟動和停止。 但內容不一定是最新的。 您可以隨時按一下 [重新整理]以重新整理該清單，查看目前的處理序清單。

5. 請在 [附加至處理序] 對話方塊的 [可使用的處理序] 清單中，尋找您要附加的程式。

    如果該處理序正在不同的使用者帳戶下執行，請選取 [顯示所有使用者的處理序] 核取方塊。

6. 按一下 [附加]。

## <a name="additional-info"></a>其他資訊

偵錯時，您可以附加至多個程式，但是無論在任何時間，偵錯工具一次只能有一個使用中程式。 您可以在 [偵錯位置] 工具列或 [處理序] 視窗中設定使用中的程式。 如需詳細資訊，請參閱 [如何：設定目前的處理序](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e)。

如果您嘗試附加至未受信任的使用者帳戶所擁有的處理序，會出現安全性警告對話方塊確認訊息。 如需詳細資訊，請參閱[安全性警告： 附加至不受信任的使用者所擁有的處理序可能會造成危險。如果下列資訊看起來有問題，或您不確定，不會附加至這個處理序](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)。

在某些情況下，在遠端桌面 (終端機服務) 工作階段中進行偵錯時，[可使用的處理序] 清單並不會顯示所有可使用的處理序。 如果您是以受限制的使用者身分執行 Visual Studio，則 [可使用的處理序] 清單不會顯示在工作階段 0 中執行的處理序，因為工作階段 0 是用於服務以及其他包括 w3wp.exe 的伺服器處理序。 您可藉由使用系統管理員帳戶來執行 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，或是從伺服器主控台 (而非終端機服務工作階段) 執行 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，來解決這個問題。 如果這兩種方法都無法解決，第三個選項是從 Windows 命令列執行 `vsjitdebugger.exe -p` *ProcessId*來附加至進程。 您可以使用 tlist.exe 來判斷處理序 ID。 若要取得 tlist.exe，您可以從  [WDK 和 WinDbg 下載](/windows-hardware/drivers/dashboard/)來下載並安裝 Debugging Tools for Windows。

## <a name="BKMK_Scenarios"></a>常見的調試情況

為了協助您識別是否需要使用 [**附加至進程**]，以及要附加到哪個進程，這裡會顯示一些常見的偵錯工具案例（不完整的清單）。 有更多可用的指示，我們提供連結。

對於某些應用程式類型（例如 Windows Store 應用程式），您不會直接附加至進程名稱，而是改為使用 [**已安裝的應用程式套件**] 功能表選項（請參閱表格）。

> [!NOTE]
> 如需 Visual Studio 中基本的偵錯工具的詳細資訊，請參閱[開始使用偵錯工具](../debugger/getting-started-with-the-debugger.md)。

|情節|Debug 方法|處理序名稱|附注和連結|
|-|-|-|-|
|在本機電腦上對受控或原生應用程式進行 Debug|使用 [附加至進程] 或 [[標準] 調試](../debugger/getting-started-with-the-debugger.md)程式|*appname*.exe|若要快速存取對話方塊，請使用**CTRL + ALT + P** ，然後輸入處理常式名稱的第一個字母。|
|在沒有偵錯工具的情況下啟動應用程式之後，在本機電腦上的 ASP.NET 應用程式|使用 [附加至進程]|iiexpress .exe|這可能有助於讓應用程式的載入速度更快，例如在分析時（例如）。 |
|IIS 伺服器上的 Remote debug ASP.NET 4 或4。5|使用遠端工具並附加至進程|w3wp.exe|請參閱遠端[IIS 電腦上的遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|IIS 伺服器上的遠端偵錯程式 ASP.NET Core|使用遠端工具並附加至進程|dnx.exe|如需應用程式部署，請參閱[發行至 IIS](https://docs.asp.net/en/latest/publishing/iis.html)。 如需偵錯工具，請參閱遠端[IIS 電腦上的遠端偵錯程式 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|在伺服器進程上，對其他支援的應用程式類型進行偵錯工具|使用遠端工具（如果伺服器為遠端）並附加至進程|iexplore.exe .exe 或其他進程|如有必要，請使用 [工作管理員] 來協助識別進程。 請參閱本主題中的[遠端偵錯](../debugger/remote-debugging.md)和更新的章節|
|對 Windows 傳統型應用程式進行遠端 debug|遠端工具和 F5|N/A| 請參閱[遠端偵錯](../debugger/remote-debugging.md)|
|遠端 debug a Windows 通用（UWP）、OneCore、HoloLens 或 IoT 應用程式|針對已安裝的應用程式套件進行偵錯|N/A|使用**debug/其他 Debug 目標/Debug 已安裝應用程式套件**，而不是**附加至進程**|
|針對您未從 Visual Studio 啟動的 Windows 通用（UWP）、OneCore、HoloLens 或 IoT 應用程式進行 Debug|針對已安裝的應用程式套件進行偵錯|N/A|使用**debug/其他 Debug 目標/Debug 已安裝應用程式套件**，而不是**附加至進程**|

> [!WARNING]
> 若要附加至以 JavaScript 撰寫的 Windows 通用應用程式，您必須先啟用應用程式的偵錯功能。 請參閱 Windows 開發人員中心的 [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) 。

> [!NOTE]
> 偵錯工具若要附加至以 C++ 撰寫的程式碼，該程式碼必須發出 `DebuggableAttribute`。 您可以使用 [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) 連結器選項連結，將其自動加入程式碼。

## <a name="what-debugger-features-can-i-use"></a>我可以使用哪些偵錯工具功能？

當附加至進程時，若要使用 Visual Studio 偵錯工具的完整功能（例如叫用中斷點），可執行檔必須完全符合您的本機來源和符號（也就是偵錯工具必須能夠載入正確的[符號（. pbd）](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)檔案）。 根據預設，這需要 debug 組建。

在遠端偵錯程式案例中，您必須已在 Visual Studio 中開啟原始碼（或原始程式碼的複本）。 遠端電腦上已編譯的應用程式二進位檔必須來自與本機電腦上相同的組建。

在某些本機的偵錯工具中，您可以在 Visual Studio 中進行 debug，而如果應用程式中有正確的符號檔，則不會存取來源（根據預設，這需要 debug 組建）。 如需詳細資訊，請參閱[指定符號和原始](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)程式檔。

## <a name="BKMK_Troubleshoot_attach_errors"></a> 針對附加錯誤進行疑難排解
 當偵錯工具附加至執行中的處理序時，該處理序可以包含一種或多種程式碼類型。 偵錯工具可附加的程式碼類型會在 [選取程式碼類型] 對話方塊中顯示並供您選取。

 有時候，偵錯工具可以成功附加至一種程式碼類型，而無法附加至另一種程式碼類型。 如果您嘗試附加至遠端電腦上正在執行的處理序，可能會發生這種狀況。 遠端電腦可能為某些程式碼類型安裝了遠端偵錯元件，但沒有安裝其他程式碼類型的遠端偵錯元件。 如果您嘗試附加至兩個或多個處理序以進行直接的資料庫偵錯，也可能會發生這種狀況。 (SQL 偵錯僅支援附加至單一處理序)。

 如果偵錯工具能附加至某些程式碼類型 (而非所有程式碼類型)，您可能會看到識別無法附加之類型的訊息。

 如果偵錯工具成功附加到至少一種程式碼類型，您可以繼續偵錯該處理序。 您只能偵錯已附加成功的程式碼類型。 上述範例訊息顯示該指令碼類型附加失敗。 因此，您無法在處理序內偵錯指令碼。 處理序中的指令碼仍可執行，但是您將無法在指令碼內設定中斷點、檢視資料，或執行其他的偵錯作業。

 如果您需要更多相關資訊以了解偵錯工具無法附加至程式碼類型的原因，可以嘗試重新附加至該程式碼。

 **若要取得有關為何無法附加程式碼類型的特定資訊**

1. 與處理序中斷連結。 在 [偵錯] 功能表上按一下 [中斷所有連結]。

2. 重新附加至處理序，並只選取單一程式碼類型。

   1. 在 [附加至處理序] 對話方塊的 [可使用的處理序] 清單中，選取該處理序。

   2. 按一下 [選取]。

   3. 在 [選取程式碼類型] 對話方塊中，選取 [偵錯這些程式碼類型] 以及之前附加失敗的程式碼類型。 清除任何其他程式碼。

   4. 按一下 [ **確定**]。 [選取程式碼類型] 對話框會關閉。

   5. 在 [附加至處理序] 對話方塊中按一下 [附加]。

      這時，該附加將完全失敗，您將取得特定的錯誤訊息。

## <a name="see-also"></a>請參閱
 即時調試[多個進程](../debugger/debug-multiple-processes.md)的[遠端偵錯](../debugger/remote-debugging.md)[程式](../debugger/just-in-time-debugging-in-visual-studio.md)
