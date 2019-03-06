---
title: 附加至執行中處理序偵錯工具 |Microsoft Docs
ms.custom: seodec18
ms.date: 09/27/2018
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
ms.openlocfilehash: 4b8b0d507328022746682142c8d0720ba0de3fe0
ms.sourcegitcommit: cdcbf254db737d42275e95de4ffc4f8c14e87e00
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57428761"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>使用 Visual Studio 偵錯工具附加至執行中處理序
您可以將 Visual Studio 偵錯工具附加至本機或遠端電腦上執行的處理序。 此程序執行之後，請選取**偵錯** > **připojit k procesu**或按**Ctrl**+**Alt** +**P**在 Visual Studio 中，並使用**附加至處理序**對話方塊，即可將偵錯工具附加至處理程序。

您可以使用**附加至處理序**偵錯在本機或遠端電腦上執行的應用程式，同時偵錯多個處理序、 偵錯在 Visual Studio 中建立的應用程式或您未使用從 Visual Studio 啟動任何應用程式進行偵錯附加偵錯工具。 比方說，如果您正在執行的應用程式，而不偵錯工具，並叫用例外狀況，您可以接著將偵錯工具附加至執行應用程式的處理序並開始偵錯。

如需在 Visual Studio 中的基本偵錯資訊，請參閱[第一次查看偵錯工具](../debugger/debugger-feature-tour.md)。

> [!TIP]
> 不確定是否要使用**附加至處理序**偵錯案例嗎？ 請參閱[常見偵錯案例](#BKMK_Scenarios)。

##  <a name="BKMK_Attach_to_a_running_process"></a> 附加至本機電腦上執行的處理序

若要快速重新附加至您先前附加至處理序，請參閱[重新附加至處理序](#BKMK_reattach)。

若要偵錯遠端電腦上的處理序，請參閱[附加至遠端電腦上的處理序](#BKMK_Attach_to_a_process_on_a_remote_computer)。

**若要附加至本機電腦上的處理序：**

1. 在 Visual Studio 中，選取**偵錯** > **připojit k procesu** (或按**Ctrl**+**Alt** + **P**) 以開啟**附加至處理序** 對話方塊。

   **連線類型**應該設定為**預設**。 **連線目標**應該是您本機電腦名稱。

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. 在 **可用的處理序**清單，尋找並選取您要附加至處理程序的處理程序。

   - 若要快速地選取處理程序，請輸入其名稱或中的第一個字母**篩選處理序** 方塊中。

   - 如果您不知道處理程序名稱，瀏覽清單中，或請參閱[常見偵錯案例](#BKMK_Scenarios)的一些常見的程序名稱。

   >[!TIP]
   >處理程序可以啟動和停止在背景工作，而**附加至處理序**對話方塊已開啟，因此執行中處理程序的清單可能不一定總是目前。 您可以選取**重新整理**在任何時間，若要查看目前的清單。

3. 在 **附加至**欄位中，確定已列出您打算進行偵錯的程式碼的類型。 預設值**自動**設定適用於大部分的應用程式類型。

   若要以手動方式選取程式碼類型：
   1. 按一下 [選取] 。
   1. 在 [**選取程式碼類型**] 對話方塊中，選取**偵錯這些程式碼類型**。
   1. 選取您想要偵錯的程式碼類型。
   1. 選取 [確定]。

4. 選取 **附加**。

>[!NOTE]
>您可以附加至多個應用程式進行偵錯，但一次只能有一個應用程式是在偵錯工具中。 您可以在 Visual Studio 中設定使用的應用程式**偵錯位置**工具列或**處理序**視窗。

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> 附加至遠端電腦上的處理序

您也可以選取遠端電腦**附加至處理序** 對話方塊中，檢視可用的處理序在該電腦上執行的清單，並將附加至一或多個處理序進行偵錯。 遠端偵錯工具 (*msvsmon.exe*) 必須在遠端電腦上執行。 如需詳細資訊，請參閱 <<c0> [ 遠端偵錯](../debugger/remote-debugging.md)。

如需更完整的偵錯已部署至 IIS 的 ASP.NET 應用程式的詳細指示，請參閱[遠端偵錯 IIS 的遠端電腦上的 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。

**若要附加至遠端電腦上執行的處理序：**

1. 在 Visual Studio 中，選取**偵錯** > **připojit k procesu** (或按**Ctrl**+**Alt** + **P**) 以開啟**附加至處理序** 對話方塊。

2. **連線類型**應該**預設**對大部分的情況。 在 **連線目標**方塊中，選取 遠端電腦，使用下列方法之一：

   - 選取下拉式箭號旁**連線目標**，並從下拉式清單中選取的電腦名稱。
   - 輸入中的電腦名稱**連線目標** 方塊中。
   
     ::: moniker range="vs-2017"

     > [!NOTE]
     > 如果您無法連線使用的遠端電腦名稱，請嘗試使用的 IP 和連接埠位址 (例如`123.45.678.9:4022`)。 4022 是 Visual Studio 2017 x64 遠端偵錯工具的預設連接埠。 其他遠端偵錯工具的連接埠指派，請參閱[遠端偵錯工具連接埠指派](remote-debugger-port-assignments.md)。

     ::: moniker-end
     
     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > 如果您無法連線使用的遠端電腦名稱，請嘗試使用的 IP 和連接埠位址 (例如`123.45.678.9:4022`)。 4024 是 Visual Studio 2019 x64 遠端偵錯工具的預設連接埠。 其他遠端偵錯工具的連接埠指派，請參閱[遠端偵錯工具連接埠指派](remote-debugger-port-assignments.md)。

     ::: moniker-end

   - 選取 [**尋找**按鈕旁**連線目標**方塊，以開啟**遠端連線**] 對話方塊。 **的遠端連線**對話方塊會列出位於您本機子網路，或直接連接到電腦的所有裝置。 您可能需要[開啟 UDP 連接埠 3702](../debugger/remote-debugger-port-assignments.md)伺服器以探索遠端裝置上。 選取的電腦或裝置，您想要，然後按一下**選取**。

   > [!NOTE]
   > **連線類型**設定偵錯工作階段之間持續維持。 **連線目標**設定目標發生成功的偵錯連接時，才偵錯工作階段之間持續維持。

3. 按一下 **重新整理**填入**可用的處理序**清單。

    >[!TIP]
    >處理程序可以啟動和停止在背景工作，而**附加至處理序**對話方塊已開啟，因此執行中處理程序的清單可能不一定總是目前。 您可以選取**重新整理**在任何時間，若要查看目前的清單。

4. 在 **可用的處理序**清單，尋找並選取您要附加至處理程序的處理程序。

   - 若要快速地選取處理程序，請輸入其名稱或中的第一個字母**篩選處理序** 方塊中。

   - 如果您不知道處理程序名稱，瀏覽清單中，或請參閱[常見偵錯案例](#BKMK_Scenarios)的一些常見的程序名稱。

   - 若要尋找所有的使用者帳戶下執行的處理程序，請選取**顯示的所有使用者處理序**核取方塊。

     >[!NOTE]
     >如果您嘗試附加至未受信任的使用者帳戶所擁有的處理序，會出現安全性警告對話方塊確認訊息。 如需詳細資訊，請參閱[安全性警告： 附加至不受信任的使用者所擁有的處理序可能會造成危險。如果下面的資訊看起來有問題，或者您並不確定，請不要附加至此處理序](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)

5. 在 **附加至**欄位中，確定已列出您打算進行偵錯的程式碼的類型。 預設值**自動**設定適用於大部分的應用程式類型。

   若要以手動方式選取程式碼類型：
   1. 按一下 [選取] 。
   1. 在 [**選取程式碼類型**] 對話方塊中，選取**偵錯這些程式碼類型**。
   1. 選取您想要偵錯的程式碼類型。
   1. 選取 [確定]。

6. 選取 **附加**。

>[!NOTE]
>您可以附加至多個應用程式進行偵錯，但一次只能有一個應用程式是在偵錯工具中。 您可以在 Visual Studio 中設定使用的應用程式**偵錯位置**工具列或**處理序**視窗。

在某些情況下，當您在遠端桌面 （終端機服務） 工作階段中偵錯**可用的處理序**清單不會顯示所有可用的處理序。 如果您的使用者具有受限的使用者帳戶身分執行 Visual Studio**可用的處理序**清單不會顯示在工作階段 0 執行的處理序。 工作階段 0 用於服務以及其他伺服器處理序，包括*w3wp.exe*。 您可藉由使用系統管理員帳戶來執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，或是從伺服器主控台 (而非終端機服務工作階段) 執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，來解決這個問題。

如果這些解決方法都沒有效，則第三個選項是從 Windows 命令列執行 `vsjitdebugger.exe -p <ProcessId>` 以附加至處理序。 您可以使用 *tlist.exe* 來判斷處理序識別碼。 若要取得 *tlist.exe*，您可以從 [WDK 和 WinDbg 下載](/windows-hardware/drivers/download-the-wdk)來下載並安裝適用於 Windows 的偵錯工具。

## <a name="BKMK_reattach"></a> 重新附加至處理程序

您可以快速重新附加至您先前選擇附加至處理程序**偵錯** > **重新附加至處理程序**(**Shift** +**Alt**+**P**)。 當您選擇此命令時，偵錯工具會立即嘗試將附加到最後一個處理序附加至藉由先嘗試比對上一個處理序識別碼，以及如果失敗，藉由比對上一個處理序名稱。 如果找不到任何相符項目，或是數個程序有相同的名稱，**附加至處理序**對話方塊隨即開啟，因此您可以選取正確的處理序。

> [!NOTE]
> **重新附加至處理序**命令是從 Visual Studio 2017 中推出。

## <a name="BKMK_Scenarios"></a> 常見的偵錯案例

若要協助您判斷是否要使用**附加至處理序**和哪些要附加處理序下, 表顯示一些常見偵錯案例中，包含多個指示的連結 （如果可用）。 （清單未全部列出。）

對於某些應用程式類型，例如通用 Windows App (UWP) 應用程式，您不直接附加到處理序名稱，但使用**偵錯 Installed App Package**功能表選項在 Visual Studio 中 （請參閱資料表）。

偵錯工具若要附加至以 C++ 撰寫的程式碼，該程式碼必須發出 `DebuggableAttribute`。 您可以使用 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) 連結器選項連結，將其自動加入程式碼。

針對用戶端指令碼偵錯，必須在瀏覽器中啟用指令碼偵錯。 偵錯在 Chrome 上的用戶端指令碼中，選擇**Webkit**做為程式碼類型，並根據您的應用程式類型而定，您可能需要關閉所有 Chrome 執行個體，並在偵錯模式啟動瀏覽器 (型別`chrome.exe --remote-debugging-port=9222`從命令列)。

若要快速地選取 執行中處理序要在 Visual Studio 中，附加至輸入**Ctrl**+**Alt**+**P**，然後輸入的第一個字母處理序名稱。

|情節|偵錯方法|處理序名稱|附註和連結|
|-|-|-|-|
|遠端偵錯 ASP.NET 4 或 4.5 上 IIS 伺服器|使用遠端工具和**附加至處理序**|*w3wp.exe*|請參閱[遠端偵錯 IIS 的遠端電腦上的 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|在 IIS 伺服器上遠端偵錯 ASP.NET Core|使用遠端工具和**附加至處理序**|*dotnet.exe*|應用程式部署，請參閱[發行至 IIS](https://docs.asp.net/en/latest/publishing/iis.html)。 進行偵錯，請參閱[IIS 的遠端電腦上的遠端偵錯 ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|在本機 IIS 伺服器上，支援的應用程式類型的用戶端指令碼偵錯 |使用**附加至處理序**|*chrome.exe*， *MicrosoftEdgeCP.exe*，或*iexplore.exe*|必須啟用指令碼偵錯。 Chrome 中，您也必須針對執行 Chrome 偵錯模式，然後選取**Webkit 程式碼**中**附加至**欄位。|
|偵錯C#，Visual Basic 或 c + + 在本機電腦上的應用程式|使用任何一種[標準偵錯](../debugger/debugger-feature-tour.md)或**附加至處理序**|\<應用程式名稱>*.exe*|在大部分情況下，會使用標準偵錯而非**附加至處理序**。|
|遠端偵錯 Windows 傳統型應用程式|遠端工具|N/A| 請參閱[遠端偵錯C#或 Visual Basic 應用程式](../debugger/remote-debugging-csharp.md)或是[遠端偵錯 c + + 應用程式](../debugger/remote-debugging-cpp.md)|
|啟動但不偵錯工具的應用程式之後，偵錯在本機電腦上的 ASP.NET 應用程式|使用**附加至處理序**|*iiexpress.exe*|這可能是很有幫助您載入的應用程式更快，這類 （例如） 程式碼剖析時。 |
|在 伺服器處理序上其他支援的應用程式類型進行偵錯|如果遠端伺服器，使用 遠端工具，和**附加至處理序**|*chrome.exe*， *iexplore.exe*，或其他處理程序|如有必要，使用資源監視器來識別處理程序。 請參閱[遠端偵錯](../debugger/remote-debugging.md)。|
|遠端偵錯的通用 Windows App (UWP)、 OneCore、 HoloLens、 或 IoT 應用程式|針對已安裝的應用程式套件進行偵錯|N/A|請參閱[偵錯已安裝的應用程式套件](debug-installed-app-package.md)而不是使用**附加至處理序**|
|您未從 Visual Studio 啟動的通用 Windows App (UWP)、 OneCore、 HoloLens、 或 IoT 應用程式進行偵錯|針對已安裝的應用程式套件進行偵錯|N/A|請參閱[偵錯已安裝的應用程式套件](debug-installed-app-package.md)而不是使用**附加至處理序**|

## <a name="use-debugger-features"></a>使用偵錯工具功能

若要使用完整的功能 （例如叫用中斷點） 的 Visual Studio 偵錯工具附加至處理序，當應用程式必須完全符合您的本機來源和符號。 也就是偵錯工具必須能夠載入正確[符號 (.pdb) 檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。 根據預設，這需要偵錯組建。

遠端偵錯的情況下，您必須擁有原始碼 （或一份原始碼） 已在 Visual Studio 中開啟。 在本機電腦上，在遠端電腦上的已編譯的應用程式二進位碼檔案必須來自同一個組建。

在本機偵錯案例，您可以偵錯在 Visual Studio 中而無法存取來源如果應用程式有正確的符號檔。 根據預設，這需要偵錯組建。 如需詳細資訊，請參閱 <<c0> [ 指定的符號和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

##  <a name="BKMK_Troubleshoot_attach_errors"></a> 針對附加錯誤進行疑難排解
 當偵錯工具附加至執行中的處理序時，該處理序可以包含一種或多種程式碼類型。 偵錯工具可附加的程式碼類型會在 [選取程式碼類型]  對話方塊中顯示並供您選取。

 有時候，偵錯工具可以成功附加至一種程式碼類型，而無法附加至另一種程式碼類型。 如果您嘗試附加至遠端電腦上正在執行的處理序，可能會發生這種狀況。 遠端電腦可能為某些程式碼類型安裝了遠端偵錯元件，但沒有安裝其他程式碼類型的遠端偵錯元件。 如果您嘗試附加至兩個或多個處理序以進行直接的資料庫偵錯，也可能會發生這種狀況。 (SQL 偵錯僅支援附加至單一處理序)。

 如果偵錯工具無法附加至某些，但不是全部的程式碼類型時，您會看到用來識別哪些類型附加失敗的訊息。

 如果偵錯工具成功附加到至少一種程式碼類型，您可以繼續偵錯該處理序。 您只能偵錯已附加成功的程式碼類型。 處理序中未連結的程式碼仍會執行，但您將無法設定中斷點、 檢視資料，或執行其他偵錯的作業，該程式碼。

 如果您想要偵錯工具附加至程式碼類型失敗的原因的更具體資訊，請嘗試重新附加至該程式碼。

 **取得程式碼類型為何無法附加的相關資訊：**

1.  與處理序中斷連結。 在 **偵錯**功能表上，選取**中斷所有連結**。

1.  重新附加至處理程序，只選取程式碼類型附加失敗。

    1.  在 [附加至處理序] 對話方塊的 [可使用的處理序] 清單中，選取該處理序。

    2.  選取 **選取**。

    3.  在 [選取程式碼類型]  對話方塊中，選取 [偵錯這些程式碼類型]  以及之前附加失敗的程式碼類型。 取消選取其他的程式碼類型。

    4.  選取 [確定]。

    5.  在  **připojit k procesu**對話方塊中，選取**附加**。

    這時，該附加將完全失敗，您將取得特定的錯誤訊息。

## <a name="see-also"></a>另請參閱

- [對多重處理序進行偵錯](../debugger/debug-multiple-processes.md)
- [Just-In-Time 偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)
- [遠端偵錯](../debugger/remote-debugging.md)