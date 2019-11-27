---
title: 遠端偵錯 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- CSharp
- FSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 81
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68ebd9ab8c4f9d3cda1371d90a8da459edb1592b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300564"
---
# <a name="remote-debugging"></a>遠端偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以偵錯已部署在不同電腦的 Visual Studio 應用程式。  若要這樣做，您可以使用 Visual Studio 遠端偵錯工具。  
  
 這裡的資訊適用於 Windows 桌面應用程式和 ASP.NET 應用程式。  如需遠端偵錯程式和 Azure 應用程式的相關資訊，請參閱[Windows store 和 azure 應用程式上的遠端](#bkmk_winstoreAzure)偵測。  
  
## <a name="get-the-remote-tools"></a>取得遠端工具  
您可以直接在要進行偵錯工具的裝置或伺服器上下載遠端工具，也可以從已安裝 Visual Studio 的主機電腦取得遠端工具。

### <a name="to-download-and-install-the-remote-tools"></a>下載並安裝遠端工具
  
1. 在您要進行偵錯工具的裝置或伺服器電腦上（而不是執行 Visual Studio 的機器），取得正確版本的遠端工具。

    |版本|連結|附註|
    |-|-|-|
    |Visual Studio 2015 Update 3|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|若出現提示，請加入免費的 Visual Studio Dev Essentials 群組，或者您可以使用有效的 Visual Studio 訂用帳戶登入。 然後視需要重新開啟連結。 一律下載符合您裝置作業系統的版本（x86、x64 或 ARM 版本）|
    |Visual Studio 2015 （較舊版本）|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|若出現提示，請加入免費的 Visual Studio Dev Essentials 群組，或者您可以使用有效的 Visual Studio 訂用帳戶登入。 然後視需要重新開啟連結。|
    |Visual Studio 2013|[遠端工具](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2013 檔中的下載頁面|
    |Visual Studio 2012|[遠端工具](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2012 檔中的下載頁面|
  
2. 在 [下載] 頁面上，選擇符合您作業系統的工具版本（x86、x64 或 ARM 版本），並下載遠端工具。
  
    > [!IMPORTANT]
    > 建議您安裝最新版本的遠端工具，以符合您的 Visual Studio 版本。 不建議使用不相符的版本。  
    >   
    >  此外，您必須安裝與您要安裝的作業系統具有相同架構的遠端工具。 換句話說，如果您想要在執行64位作業系統的遠端電腦上，執行32位應用程式的偵測，您必須在遠端電腦上安裝64位版本的遠端工具。  
  
3. 當您完成下載可執行檔時，請遵循指示，在遠端電腦上安裝應用程式。 請參閱[安裝指示](#bkmk_setup)

如果您嘗試將遠端偵錯程式（msvsmon）複製到遠端電腦並加以執行，請注意，只有當您下載這些工具時，才會安裝**遠端偵錯程式設定 Wizard** （**rdbgwiz.exe**），而且您稍後可能需要使用 Wizard 來進行設定，特別是當您想要遠端偵錯程式以服務方式執行時。 如需詳細資訊，請參閱以下的[（選擇性）將遠端偵錯程式設定為服務](#bkmk_configureService)。

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>從檔案共用執行遠端偵錯程式

您可以在已安裝 Visual Studio 2015 的社區、專業版或企業版的電腦上，找到遠端偵錯程式（**msvsmon**）。 在許多情況下，設定遠端偵錯程式的最簡單方式，就是從檔案共用執行遠端偵錯程式（msvsmon）。 如需使用限制，請參閱遠端偵錯程式的說明頁面（遠端偵錯程式中的說明 **/使用**方式）。

1. 在符合您的 Visual Studio 版本的目錄中尋找**msvsmon。** 針對 Visual Studio 2015：

      **Program Files\Microsoft Visual Studio 14.0 \ Common7\ide\remote debugger Debugger\x86\msvsmon.exe**
      
      **Program Files\Microsoft Visual Studio 14.0 \ Common7\ide\remote debugger Debugger\x64\msvsmon.exe**

2. 共用 Visual Studio 電腦上的 [**遠端偵錯程式**] 資料夾。

3. 在遠端電腦上，執行**msvsmon. exe**。 遵循[安裝指示](#bkmk_setup)。

> [!TIP] 
> 如需命令列安裝和命令列參考，請參閱**msvsmon**的說明頁面，方法是在已安裝 Visual Studio 的電腦上的命令列中輸入 ``msvsmon.exe /?`` （或移至遠端偵錯程式中的 [說明] **/[使用**方式]）。

## <a name="supported-operating-systems"></a>Supported Operating Systems  
 遠端電腦必須執行下列作業系統的其中一個：  
  
- Windows 10  
  
- Windows 8 或 8.1  
  
- Windows 7 Service Pack 1  
  
- Windows Server 2012 或 Windows Server 2012 R2  
  
- Windows Server 2008 Service Pack 2、Windows Server 2008 R2 Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>支援的硬體組態  
  
- 1.6 GHz 或更快的處理器  
  
- 1 GB RAM (如果在虛擬機器上執行，便需要 1.5 GB)  
  
- 1 GB 的可用硬碟空間  
  
- 5400 RPM 硬碟  
  
- 可使用 DirectX 9 且可在 1024 x 768 或更高顯示解析度執行的視訊卡  
  
## <a name="network-configuration"></a>網路組態  
 遠端電腦和 Visual Studio 電腦必須透過網路、工作群組或家用群組等連接，或直接透過乙太網路纜線連接。 不支援透過網際網路偵錯。  
  
## <a name="bkmk_setup"></a>設定遠端偵錯程式  
 您必須在遠端電腦上擁有系統管理權限  
  
1. 尋找遠端偵錯工具應用程式。 （開啟 [開始] 功能表並搜尋**遠端偵錯程式**）。
  
    如果您是在遠端伺服器上執行遠端偵錯程式，您可以用滑鼠右鍵按一下 [遠端偵錯程式] 應用程式，然後選擇 [**以系統管理員身分執行**] （或者，您可以將遠端偵錯程式當做服務執行）。如果您不是在遠端伺服器上執行，只要正常啟動就可以了。
  
2. 當您第一次啟動遠端工具（或設定之前）時，[**遠端偵錯**程式設定 dalog] 方塊隨即出現。  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. 如果未安裝 Windows 服務 API （這只會發生在 Windows Server 2008 R2），請選擇 [**安裝**] 按鈕。  
  
4. 選取您想要在遠端工具上使用的網路類型。 必須至少選取一種網路類型。 如果此電腦經由網域連線，您就必須選擇第一個項目。 如果此電腦經由工作群組或家用群組連線，您就需要視情況選擇第二個或第三個項目。  
  
5. 選擇 [**設定遠端偵錯**] 以設定防火牆並啟動工具。  
  
6. 設定完成時，[遠端偵錯工具] 視窗隨即出現。
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    遠端偵錯程式現在正在等候連接。 記下所顯示的伺服器名稱和埠號碼，因為您稍後將會用到 Visual Studio 中的設定。  
  
   當您完成偵錯工具並需要停止遠端偵錯程式時，請按一下視窗上的 [檔案] **/** [結束]。 您可以從 [**開始**] 功能表或從命令列重新開機它：  
  
   **\<Visual Studio 安裝目錄 > \Common7\IDE\Remote 偵錯工具\\< x86、x64 或 Appx\msvsmon.exe**。  
  
## <a name="configure-the-remote-debugger"></a>設定遠端偵錯工具  
 在您第一次啟動遠端偵錯工具後，可以變更其組態的某些部分。
  
- 若要讓其他使用者能夠連線到遠端偵錯程式，請選擇 [**工具]/[許可權**]。 您必須具有系統管理員權限才能授與或拒絕使用權限。

  > [!IMPORTANT]
  > 您可以在與 Visual Studio 電腦上使用的使用者帳戶不同的使用者帳戶下執行遠端偵錯程式，但必須將不同的使用者帳戶新增至遠端偵錯程式的許可權。 

   或者，您可以從命令列啟動遠端偵錯程式，並使用 **/allow \<username >** 參數： **msvsmon/allow \<username@computer>** 。
  
- 若要變更驗證模式或埠號碼，或指定遠端工具的超時值：選擇 [**工具]/[選項**]。  
  
   如需預設使用的埠號碼清單，請參閱[遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)。  
  
   > [!WARNING]
  > 您可以選擇在 [非驗證] 模式下執行遠端工具，但非常不建議您使用這個模式。 在此模式中執行時不具有網路安全性。 只有在確定網路沒有面臨惡意或攻擊流量的風險時，才能選擇非驗證模式。

## <a name="bkmk_configureService"></a>選擇性將遠端偵錯程式設定為服務
 若要在 ASP.NET 和其他伺服器環境中進行偵錯工具，您必須以系統管理員的身分執行遠端偵錯程式，或者，如果您想要讓它一律執行，請以服務的形式執行遠端偵錯程式。
  
 如果您想要將遠端偵錯程式設定為服務，請遵循下列步驟。  
  
1. 尋找 [遠端偵錯工具組態精靈] (rdbgwiz.exe)。 （這是與遠端偵錯程式不同的應用程式）。只有當您安裝遠端工具時，才可以使用它。 它不會隨 Visual Studio 一同安裝。  
  
2. 開始執行 [組態精靈]。 當第一頁出現時，按一下 [下一步]。  
  
3. 核取 [以服務方式執行 Visual Studio 2015 遠端偵錯工具] 核取方塊。  
  
4. 加入使用者帳戶的名稱和密碼。  
  
    您可能需要將 [以服務方式登入] 使用者權利加入此帳戶。 (在 [開始] 頁面或視窗 (或在命令提示字元輸入 **secpol** ) 尋找 [本機安全性原則] (secpol.msc)。 視窗出現時，請按兩下 [使用者權限指派]，然後在右窗格中尋找 [以服務方式登入] 。 對它按兩下。 將使用者帳戶新增至 [**屬性**] 視窗，然後按一下 **[確定]** ）。按 **[下一步]** 。  
  
5. 選取您要遠端工具與之通訊的網路類型。 必須至少選取一種網路類型。 如果此電腦經由網域連線，您就必須選擇第一個項目。 如果此電腦經由工作群組或家用群組連線，您就必須選擇第二個或第三個項目。 按 [下一步]。  
  
6. 如果可以啟動服務，您就會看到 [您已順利完成 Visual Studio 遠端偵錯工具組態精靈]。 如果無法啟動服務，您就會看到 [無法完成 Visual Studio 遠端偵錯工具組態精靈]。 此頁面也會提供啟動服務所需遵循的一些祕訣。  
  
7. 按一下 **[完成]** 。  
  
   此時 [遠端偵錯工具] 會以服務方式執行。 您可以前往 [控制台] / [服務] ，然後尋找 [Visual Studio 2015 遠端偵錯工具]。  
  
   您可以從 [控制台] / [服務]停止和啟動遠端偵錯工具服務。  

## <a name="remote-debug-an-aspnet-application"></a>遠端偵錯 ASP.NET 應用程式  
 ASP.NET 應用程式部署到執行 IIS 的遠端電腦有不同的步驟，視作業系統和 IIS 的版本而定。 對於執行 Windows Server 2008 或 Windows Server 2012 且已安裝 IIS 7.5 或更新版本的遠端電腦，請參閱遠端[IIS 電腦上的遠端偵錯程式 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。
 
 如果您要偵錯工具 ASP.NET Core 應用程式，請參閱[發行至 IIS](https://docs.asp.net/en/latest/publishing/iis.html)。 在 IIS 上發佈 ASP.NET Core 需要不同的步驟。 成功發佈 ASP.NET Core 應用程式之後，您就可以[像其他 ASP.NET 應用](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)程式一樣從遠端進行調試，但您需要附加的進程是 dnx，而不是 w3wp.exe。

## <a name="remote-debug-a-visual-c-project"></a>遠端偵錯 Visual C++ 專案  
 在下列程式中，專案的名稱和路徑是 C:\remotetemp\MyMfc，而遠端電腦的名稱是**MJO-DL**。  
  
1. 建立名為 **mymfc** 的 MFC 應用程式。  
  
2. 在應用程式某處設定容易達到的中斷點，例如在 **MainFrm.cpp** 其中 `CMainFrame::OnCreate` 的開頭。  
  
3. 在方案總管中，以滑鼠右鍵按一下專案，然後選取 [**屬性**]。 開啟 [偵錯] 索引標籤。  
  
4. 將 [要啟動的偵錯工具] 設為 [遠端 Windows 偵錯工具]。  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. 對屬性進行下列變更：  
  
   |設定|值|
   |-|-|  
   |遠端命令|C:\remotetemp\mymfc.exe|  
   |工作目錄|C:\remotetemp|  
   |遠端伺服器名稱|MJO-DL：*portnumber*|  
   |連線|遠端使用 Windows 驗證|  
   |偵錯工具類型|僅限原生|  
   |部署目錄|C:\remotetemp.|  
   |要部署的其他檔案|C:\data\mymfcdata.txt.|  
  
    如果您部署其他檔案（選擇性），則此資料夾必須存在於兩部電腦上。  
  
6. 在方案總管中，以滑鼠右鍵按一下方案，然後選擇 [ **Configuration Manager**]。  
  
7. 在 [偵錯] 組態中，選取 [部署] 核取方塊。  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. 開始調試（**Debug/Start 調試**，或**F5**）。  
  
9. 可執行檔會自動部署到遠端電腦。  
  
10. 如果出現提示，請輸入網路認證以連線到遠端電腦。  
  
     所需的認證是您的網路安全性設定所特有。 例如，在網域電腦上，您可以選擇安全性憑證，或輸入您的功能變數名稱和密碼。 在非網域電腦上，您可能會輸入電腦名稱稱和有效的使用者帳戶名稱（例如<strong>MJO-DL\name@something.com</strong>）以及正確的密碼。  
  
11. 在 Visual Studio 的電腦上，您應該會看到執行過程在中斷點停止。  
  
    > [!TIP]
    > 或者，您可以另外執行一個步驟來部署檔案。 在 [方案總管] 中，以滑鼠右鍵按一下 [mymfc] 節點，然後選擇 [部署]。  
  
    如果您有應用程式所使用的非程式碼檔案，您需要將它們包含在 Visual Studio 專案。 建立其他檔案的專案資料夾（在**方案總管**中，按一下 [**加入/新增資料夾**]）。然後將檔案新增至資料夾（在**方案總管**中，按一下 [**新增]/[現有專案**]，然後選取檔案。）。 在每個檔案的 [屬性] 頁面上，將 [複製到輸出目錄] 設定為 [一律複製]。  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>遠端偵錯 Visual C# 或 Visual Basic 專案  
 偵錯工具無法將 Visual C# 或 Visual Basic 傳統型應用程式部署到遠端電腦，但您還是可以對其遠端偵錯，如下所示。 下列程式假設您想要在名為 MJO 的電腦上進行調試**程式**，如先前的圖例所示。
  
1. 建立名為 **MyWpf** 的 WPF 專案。  
  
2. 在程式碼某處設定容易達到的中斷點。  
  
    例如，您可能會在按鈕處理常式中設定中斷點。 若要這麼做，請開啟 Mainwindow.xaml，並從 [工具箱] 加入按鈕控制項，然後按兩下按鈕以開啟它的處理常式。
  
3. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇 [屬性]。  
  
4. 在 [屬性] 頁面上，選擇 [偵錯] 索引標籤。  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. 確認 [工作目錄] 文字方塊為空白。  
  
6. 選擇 [**使用遠端電腦**]，然後在文字方塊中輸入**MJO-DL： 4020** 。 （4020是在遠端偵錯程式視窗中顯示的埠號碼）。  
  
7. 請確定未選取 [啟用原生程式碼偵錯]。  
  
8. 建置專案。  
  
9. 在遠端電腦上建立資料夾，其路徑與 Visual Studio 電腦上的 [偵錯] 資料夾相同： **\<來源路徑>\MyWPF\MyWPF\bin\Debug**。  
  
10. 從 Visual Studio 電腦複製您剛才建置的可執行檔到遠端電腦上新建立的資料夾。
  
    > [!CAUTION]
    > 請勿對程式碼進行變更或重建（或者您必須重複此步驟）。 您複製到遠端電腦的可執行檔必須完全符合您的本機來源和符號。

    您可以手動複製專案、使用 Xcopy、Robocopy、Powershell 或其他選項。
  
11. 請確定遠端偵錯程式正在目的電腦上執行。 （如果不是，請在 [**開始**] 功能表中搜尋**遠端偵錯程式**。 ） [遠端偵錯程式] 視窗看起來像這樣。  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. 在 Visual Studio 中，啟動 [調試] （[**Debug]/[開始**] [調試] 或**F5**）。  
  
13. 如果出現提示，請輸入網路認證以連線到遠端電腦。  
  
     必要的認證會根據您的網路安全性設定而有所不同。 例如，在網域電腦上，您可以輸入您的功能變數名稱和密碼。 在非網域電腦上，您可能會輸入電腦名稱稱和有效的使用者帳戶名稱（例如<strong>MJO-DL\name@something.com</strong>）以及正確的密碼。

     您應該會看到 WPF 應用程式主視窗已在遠端電腦上開啟。
  
14. 如有必要，請採取動作來叫用中斷點。 您應該會看到中斷點為作用中。 如果沒有，則應用程式的符號尚未載入。 重試，如果無法解決問題，請取得有關載入符號的資訊，以及如何在[瞭解符號檔和 Visual Studio 的符號設定](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)進行疑難排解。
  
15. 在 Visual Studio 的電腦上，您應該會看到執行過程在中斷點停止。
  
    如果您有應用程式所使用的非程式碼檔案，您需要將它們包含在 Visual Studio 專案。 建立其他檔案的專案資料夾（在**方案總管**中，按一下 [**加入/新增資料夾**]）。然後將檔案新增至資料夾（在**方案總管**中，按一下 [**新增]/[現有專案**]，然後選取檔案。）。 在每個檔案的 [屬性] 頁面上，將 [複製到輸出目錄] 設定為 [一律複製]。
  
## <a name="set-up-debugging-with-remote-symbols"></a>設定遠端符號偵錯  
 您應該能夠使用您在 Visual Studio 電腦產生的符號偵錯程式碼。 當您使用本機符號時，遠端偵錯工具的效能會更好。  如果您必須使用遠端符號，就必須告訴 [遠端偵錯監視] 在遠端電腦上尋找符號。  
  
 從 Visual Studio 2013 Update 2 開始，您可以使用下列的 msvsmon 命令列參數，以便在 Managed 程式碼中使用遠端符號：`Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 如需詳細資訊，請參閱遠端偵錯程式說明（在遠端偵錯程式視窗中按**F1** ，或按一下 [說明] **/[使用**方式]）。 如需詳細資訊，請參閱 [Visual Studio 2012 和 2013 中的 .NET 遠端符號載入變更](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)  
  
## <a name="bkmk_winstoreAzure"></a>在 Windows Store 和 Azure 應用程式上進行遠端偵錯  
 如需有關使用 Windows Store 應用程式進行遠端檢查的詳細資訊，請參閱[從 Visual Studio 在遠端裝置上進行偵錯工具和測試 Windows 儲存應用程式](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx)。  
  
 如需在 Azure 上偵錯資訊，請參閱其中一個主題：  
  
- [在 Visual Studio 中進行雲端服務或虛擬機器的調試](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)  
  
- [在 Visual Studio 中，對 .NET 後端進行調試](https://blogs.msdn.microsoft.com/azuremobile/2014/03/14/debugging-net-backend-in-visual-studio/)  
  
- Azure 網站上的遠端偵錯簡介（[第1部分](https://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/)，第[2](https://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/)部分，[第 3](https://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)部分）。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md)   
 [設定 Windows 防火牆以進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [在執行 IIS 的遠端電腦上對 ASP.NET 進行遠端偵錯](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)
