---
title: 遠端偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: hero-article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f658c14c75f3ec0e93ed05226a8b1192d73bf478
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880717"
---
# <a name="remote-debugging"></a>Remote Debugging
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[遠端偵錯](https://docs.microsoft.com/visualstudio/debugger/remote-debugging)。  
  
您可以偵錯已部署在不同電腦的 Visual Studio 應用程式。  若要這樣做，您可以使用 Visual Studio 遠端偵錯工具。  
  
 這裡的資訊適用於 Windows 桌面應用程式和 ASP.NET 應用程式。  如需遠端偵錯 Windows 市集應用程式和 Azure 的應用程式的資訊，請參閱[對 Windows 市集和 Azure 應用程式遠端偵錯](#bkmk_winstoreAzure)。  
  
## <a name="get-the-remote-tools"></a>取得遠端工具  
您可以直接在裝置或您想要偵錯，或您的伺服器上的遠端工具可以取得從主機電腦的遠端工具已安裝 Visual studio 下載。

### <a name="to-download-and-install-the-remote-tools"></a>若要下載並安裝遠端工具
  
1.  裝置或伺服器機器，您要偵錯 （而非執行 Visual Studio 的電腦），取得正確的遠端工具版本。

    |版本|連結|注意|
    |-|-|-|
    |Visual Studio 2015 Update 3|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|出現提示時，加入免費的 Visual Studio Dev Essentials 群組，或您只可以使用有效的 Visual Studio 訂用帳戶登入。 然後重新開啟連結如有必要。 一律下載比對 (x，x86、 x64 或 ARM 版本） 您裝置的作業系統版本|
    |Visual Studio 2015 （舊版）|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|出現提示時，加入免費的 Visual Studio Dev Essentials 群組，或您只可以使用有效的 Visual Studio 訂用帳戶登入。 然後重新開啟連結如有必要。|
    |Visual Studio 2013|[遠端工具](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|下載 Visual Studio 2013 文件中的頁面|
    |Visual Studio 2012|[遠端工具](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|下載 Visual Studio 2012 文件中的頁面|
  
2.  在下載頁面上，選擇符合您的作業系統 (x，x86、 x64 或 ARM 版本） 的工具版本，並下載遠端工具。
  
    > [!IMPORTANT]
    >  我們建議您安裝最新的遠端工具版本符合您的 Visual Studio 版本。 不建議使用不相符的版本。  
    >   
    >  此外，您必須安裝具有相同的架構做為您想要將它安裝所在的作業系統的遠端工具。 換句話說，如果您想要偵錯遠端電腦執行 64 位元作業系統上的 32 位元應用程式，您就必須在遠端電腦上安裝 64 位元版本的遠端工具。  
  
3.  當您完成下載可執行檔時，請遵循指示，在遠端電腦上安裝應用程式。 請參閱[安裝指示](#bkmk_setup)

如果您嘗試複製到遠端電腦的遠端偵錯工具 (msvsmon.exe) 並加以執行，請注意，**遠端偵錯工具組態精靈**(**rdbgwiz.exe**) 才會安裝您所下載工具，以及您可能需要使用精靈來建立組態之後，特別是如果您想要以服務方式執行遠端偵錯工具。 如需詳細資訊，請參閱 < [（選擇性） 設定為服務的遠端偵錯工具](#bkmk_configureService)如下。

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>若要從檔案共用執行遠端偵錯工具

您可以找到遠端偵錯工具 (**msvsmon.exe**) Visual Studio 2015 Community、 Professional 或 Enterprise 已安裝的電腦上。 許多情況下，設定遠端偵錯的最簡單方式是從檔案共用執行遠端偵錯工具 (msvsmon.exe)。 如需使用方式限制，請參閱遠端偵錯工具的 [說明] 頁面 (**協助 / 使用量**遠端偵錯工具中)。

1. 尋找**msvsmon.exe**比對您的 Visual Studio 版本的目錄中。 Visual Studio 2015:

      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. 共用**遠端偵錯工具**Visual Studio 電腦上的資料夾。

3. 在遠端電腦上，執行**msvsmon.exe**。 請遵循[安裝指示](#bkmk_setup)。

> [!TIP] 
> 命令列安裝和命令列參考，請參閱 說明網頁**msvsmon.exe**輸入``msvsmon.exe /?``已安裝 Visual studio 的電腦上的命令列中 (或移至**協助 / 使用量**遠端偵錯工具中)。

  
## <a name="supported-operating-systems"></a>Supported Operating Systems  
 遠端電腦必須執行下列作業系統的其中一個：  
  
-   Windows 10  
  
-   Windows 8 或 8.1  
  
-   Windows 7 Service Pack 1  
  
-   Windows Server 2012 或 Windows Server 2012 R2  
  
-   Windows Server 2008 Service Pack 2、Windows Server 2008 R2 Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>支援的硬體組態  
  
-   1.6 GHz 或更快的處理器  
  
-   1 GB RAM (如果在虛擬機器上執行，便需要 1.5 GB)  
  
-   1 GB 可用硬碟空間  
  
-   5400 RPM 硬碟  
  
-   可使用 DirectX 9 且可在 1024 x 768 或更高顯示解析度執行的視訊卡  
  
## <a name="network-configuration"></a>網路組態  
 遠端電腦和 Visual Studio 電腦必須透過網路、工作群組或家用群組等連接，或直接透過乙太網路纜線連接。 不支援透過網際網路偵錯。  
  
## <a name="bkmk_setup"></a>設定遠端偵錯工具  
 您必須在遠端電腦上擁有系統管理權限  
  
1.  尋找遠端偵錯工具應用程式。 (開啟 [開始] 功能表，並搜尋**遠端偵錯工具**。)
  
     如果您在遠端伺服器上執行遠端偵錯工具，您可以以滑鼠右鍵按一下 遠端偵錯工具應用程式，並選擇**系統管理員身分執行**（或者，您可以執行遠端偵錯工具即服務）。如果您不會執行它，在遠端伺服器上，只是正常方式啟動。
  
3.  當您啟動遠端工具第一次 （或在設定之前），則**遠端偵錯組態**對話方塊隨即出現。  
  
     ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
4.  如果 Windows 服務 API 未安裝 （這只能在 Windows Server 2008 R2 上發生），請選擇**安裝** 按鈕。  
  
5.  選取您想要在遠端工具上使用的網路類型。 必須至少選取一種網路類型。 如果此電腦經由網域連線，您就必須選擇第一個項目。 如果此電腦經由工作群組或家用群組連線，您就需要視情況選擇第二個或第三個項目。  
  
6.  選擇**設定遠端偵錯**設定防火牆並啟動此工具。  
  
7.  設定完成時，[遠端偵錯工具] 視窗隨即出現。
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
     遠端偵錯工具目前正在等待連接。 請記下的伺服器名稱和連接埠號碼會顯示，因為您稍後將會在 Visual Studio 中的組態。  
  
 當您完成偵錯 」 和 「 停止遠端偵錯工具的需要時，按一下**檔案] / [結束**視窗上。 您可以重新啟動從**啟動**功能表或從命令列：  
  
 **\<Visual Studio 安裝目錄 > \Common7\IDE\Remote 偵錯工具\\< x86、 x64、 或 Appx\msvsmon.exe**。  
  
## <a name="configure-the-remote-debugger"></a>設定遠端偵錯工具  
 在您第一次啟動遠端偵錯工具後，可以變更其組態的某些部分。
  
-   若要讓其他使用者可以連線到遠端偵錯工具，請選擇**工具 / 權限**。 您必須具有系統管理員權限才能授與或拒絕使用權限。

    > [!IMPORTANT]
    > 您可以從您的 Visual Studio 電腦，使用的使用者帳戶來執行遠端偵錯工具在不同的使用者帳戶下，但您必須將不同的使用者帳戶加入遠端偵錯工具的權限。 

     或者，您可以從命令列啟動遠端偵錯工具 **/allow\<使用者名稱 >** 參數： **msvsmon /allow \< username@computer>**。
  
-   若要變更驗證模式或連接埠號碼，或指定遠端工具的逾時值： 選擇**工具 / 選項**。  
  
     如需預設使用的連接埠號碼的清單，請參閱 < [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)。  
  
     > [!WARNING]
>  您可以選擇在 [非驗證] 模式下執行遠端工具，但非常不建議您使用這個模式。 在這個模式下執行時，不具網路安全性。 只有在確定網路沒有面臨惡意或攻擊流量的風險時，才能選擇非驗證模式。

##  <a name="bkmk_configureService"></a> （選擇性）設定遠端偵錯工具 as a service
 進行偵錯 ASP.NET 和其他伺服器環境中，您必須以系統管理員身分執行遠端偵錯工具或者，如果您想要一律執行中，以服務方式執行遠端偵錯工具。
  
 如果您想要設定遠端偵錯工具 as a service，請遵循下列步驟。  
  
1.  尋找 [遠端偵錯工具組態精靈]  (rdbgwiz.exe)。 (這是和 [遠端偵錯工具] 不同的應用程式)。僅當您安裝遠端工具時，才可使用。 它不會隨 Visual Studio 一同安裝。  
  
2.  開始執行 [組態精靈]。 當第一頁出現時，按一下 [下一步] 。  
  
3.  核取 [以服務方式執行 Visual Studio 2015 遠端偵錯工具]  核取方塊。  
  
4.  加入使用者帳戶的名稱和密碼。  
  
     您可能需要將 [以服務方式登入]  使用者權利加入此帳戶。 (在 [開始]  頁面或視窗 (或在命令提示字元輸入 **secpol** ) 尋找 [本機安全性原則]  (secpol.msc)。 視窗出現時，請按兩下 [使用者權限指派] ，然後在右窗格中尋找 [以服務方式登入]  。 對它按兩下。 將使用者帳戶加入**屬性**視窗，然後按一下**確定**。)按一下 [**下一步]**。  
  
5.  選取您要遠端工具與之通訊的網路類型。 必須至少選取一種網路類型。 如果此電腦經由網域連線，您就必須選擇第一個項目。 如果此電腦經由工作群組或家用群組連線，您就必須選擇第二個或第三個項目。 按 [ **下一步**]。  
  
6.  如果可以啟動服務，您就會看到 [您已順利完成 Visual Studio 遠端偵錯工具組態精靈] 。 如果無法啟動服務，您就會看到 [無法完成 Visual Studio 遠端偵錯工具組態精靈] 。 此頁面也會提供啟動服務所需遵循的一些祕訣。  
  
7.  按一下 [ **完成**]。  
  
 此時 [遠端偵錯工具] 會以服務方式執行。 您可以前往 [控制台] / [服務]  ，然後尋找 [Visual Studio 2015 遠端偵錯工具] 。  
  
 您可以從 [控制台] / [服務] 停止和啟動遠端偵錯工具服務。  

## <a name="remote-debug-an-aspnet-application"></a>遠端偵錯 ASP.NET 應用程式  
 ASP.NET 應用程式部署到執行 IIS 的遠端電腦有不同的步驟，視作業系統和 IIS 的版本而定。 遠端電腦執行 Windows Server 2008 或 Windows Server 2012 IIS 7.5 或更新版本安裝，請參閱[Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。
 
 如果您正在偵錯 ASP.NET Core 應用程式，請參閱[Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html)。 若要發佈 ASP.NET Core 在 IIS 上需要不同的步驟。 一旦您已成功發佈的 ASP.NET Core 應用程式時，您可以從遠端進行偵錯[就像其他 ASP.NET 應用程式](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)，只不過您需要附加至處理程序是 dnx.exe 而不是 w3wp.exe。

## <a name="remote-debug-a-visual-c-project"></a>遠端偵錯 Visual C++ 專案  
 在下列程序中，名稱和專案的路徑是 C:\remotetemp\MyMfc，而遠端電腦的名稱是**MJO DL**。  
  
1.  建立 MFC 應用程式名為**mymfc。**  
  
2.  在應用程式，輕鬆地達到時，例如在某處設定中斷點**MainFrm.cpp**，在開頭`CMainFrame::OnCreate`。  
  
3.  在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取**屬性**。 開啟**偵錯** 索引標籤。  
  
4.  設定**偵錯工具來啟動**要**遠端 Windows 偵錯工具**。  
  
     ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5.  對屬性進行下列變更：  
  
    |設定|值|
    |-|-|  
    |遠端命令|C:\remotetemp\mymfc.exe|  
    |工作目錄|C:\remotetemp|  
    |遠端伺服器名稱|MJO DL:*連接埠號碼*|  
    |連線|遠端使用 Windows 驗證|  
    |偵錯工具類型|僅限原生|  
    |部署目錄|C:\remotetemp.|  
    |其他要部署的檔案|C:\data\mymfcdata.txt.|  
  
     如果您部署其他檔案 （選擇性） 時，資料夾必須存在兩台電腦上。  
  
6.  在 [方案總管] 中，以滑鼠右鍵按一下方案，然後選擇**Configuration Manager**。  
  
7.  針對**偵錯**組態中，選取**部署**核取方塊。  
  
     ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8.  開始偵錯 (**偵錯] / [開始偵錯**，或**F5**)。  
  
9. 可執行檔會自動部署到遠端電腦。  
  
10. 出現提示時，輸入網路認證以連接到遠端電腦。  
  
     您的網路安全性組態的特定所需的認證。 比方說，網域的電腦上，您可能會選擇安全性憑證，或輸入您的網域名稱和密碼。 在非網域電腦上，您可能輸入的機器名稱和有效的使用者帳戶名稱，例如**MJO-DL\name@something.com**，以及正確的密碼。  
  
11. 在 Visual Studio 的電腦上，您應該會看到執行過程在中斷點停止。  
  
    > [!TIP]
    >  或者，您可以另外執行一個步驟來部署檔案。 在 [**方案總管] 中，** 上按一下滑鼠右鍵**mymfc**節點，然後選擇**部署**。  
  
 如果您有應用程式所使用的非程式碼檔案，您需要將它們包含在 Visual Studio 專案。 建立其他檔案的專案資料夾 (在**方案總管**，按一下**新增 / 新的資料夾**。)然後將檔案加入資料夾 (在**方案總管 中**，按一下**新增 / 現有項目**，然後選取檔案。)。 在 **屬性**頁面上的每個檔案，將**複製到輸出目錄**來**永遠複製**。  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>遠端偵錯 Visual C# 或 Visual Basic 專案  
 偵錯工具無法將 Visual C# 或 Visual Basic 傳統型應用程式部署到遠端電腦，但您還是可以對其遠端偵錯，如下所示。 下列程序假設您想要在名為的電腦上進行偵錯**MJO DL**之前圖例所示。
  
1.  建立名為 WPF 專案**MyWpf**。  
  
2.  在程式碼某處設定容易達到的中斷點。  
  
     例如，您可能會在按鈕處理常式中設定中斷點。 若要這樣做，開啟 MainWindow.xaml 中，並新增按鈕控制項從 [工具箱]，然後按兩下 button 以開啟它的處理常式。
  
3.  在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇**屬性**。  
  
4.  在 [**屬性**頁面上，選擇**偵錯**] 索引標籤。  
  
     ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5.  請確定**的工作目錄**文字方塊為空白。  
  
6.  選擇**使用遠端電腦**，然後輸入**MJO-DL:4020**在文字方塊中。 （4020 是遠端偵錯工具視窗中顯示的連接埠號碼）。  
  
7.  請確定**啟用機器碼偵錯**未選取。  
  
8.  建置專案。  
  
9. 路徑相同的遠端電腦上建立資料夾**偵錯**Visual Studio 電腦上的資料夾： **\<來源路徑 > \MyWPF\MyWPF\bin\Debug**。  
  
10. 從 Visual Studio 電腦複製您剛才建置的可執行檔到遠端電腦上新建立的資料夾。
  
    > [!CAUTION]
    >  不變更程式碼或重建 （或您必須重複此步驟）。 您複製到遠端電腦的可執行檔必須完全符合您的本機來源和符號。

    您可以手動複製專案，請使用 Xcopy、 Robocopy、 Powershell 或其他選項。
  
11. 請確定目標電腦上執行遠端偵錯工具。 (如果沒有，請搜尋**遠端偵錯工具**中**開始**功能表。 ) 的遠端偵錯工具視窗看起來像這樣。  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. 在 Visual Studio 中，開始偵錯 (**偵錯] / [開始偵錯**，或**F5**)。  
  
13. 出現提示時，輸入網路認證以連接到遠端電腦。  
  
     必要的認證會視您的網路安全性組態而有所不同。 例如，如果網域的電腦上，您可以輸入您的網域名稱和密碼。 在非網域電腦上，您可能輸入的機器名稱和有效的使用者帳戶名稱，例如**MJO-DL\name@something.com**，以及正確的密碼。

     您應該會看到 WPF 應用程式主視窗已在遠端電腦上開啟。
  
14. 如有必要，採取動作來叫用中斷點。 您應該會看到中斷點為作用中。 如果沒有，則應用程式的符號尚未載入。 重試一次，以及如果不行，請取得需載入符號的資訊，以及如何在進行疑難排解[了解符號檔和 Visual Studio 的符號設定](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx)。
  
15. 在 Visual Studio 的電腦上，您應該會看到執行過程在中斷點停止。
  
 如果您有應用程式所使用的非程式碼檔案，您需要將它們包含在 Visual Studio 專案。 建立其他檔案的專案資料夾 (在**方案總管**，按一下**新增 / 新的資料夾**。)然後將檔案加入資料夾 (在**方案總管 中**，按一下**新增 / 現有項目**，然後選取檔案。)。 在 **屬性**頁面上的每個檔案，將**複製到輸出目錄**來**永遠複製**。
  
## <a name="set-up-debugging-with-remote-symbols"></a>設定遠端符號偵錯  
 您應該能夠使用您在 Visual Studio 電腦產生的符號偵錯程式碼。 當您使用本機符號時，遠端偵錯工具的效能會更好。  如果您必須使用遠端符號，就必須告訴 [遠端偵錯監視] 在遠端電腦上尋找符號。  
  
 從 Visual Studio 2013 Update 2 開始，您可以使用下列的 msvsmon 命令列參數，以便在 Managed 程式碼中使用遠端符號：`Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 如需詳細資訊，請參閱遠端偵錯的說明 (請按**F1**中的遠端偵錯工具 視窗中或按一下**協助 / 使用量**)。 您可以找到更多資訊[.NET 遠端符號載入變更 Visual Studio 2012 和 2013年中](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)  
  
##  <a name="bkmk_winstoreAzure"></a> 遠端偵錯 Windows 市集和 Azure 應用程式  
 如需 Windows 市集應用程式的遠端偵錯資訊，請參閱[偵錯和測試 Windows 市集應用程式，在遠端裝置上從 Visual Studio](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx)。  
  
 如需在 Azure 上偵錯資訊，請參閱其中一個主題：  
  
-   [偵錯雲端服務或在 Visual Studio 中的虛擬機器](http://msdn.microsoft.com/library/azure/ff683670.aspx)  
  
-   [偵錯在 Visual Studio 中的.NET 後端](http://blogs.msdn.com/b/azuremobile/archive/2014/03/14/debugging-net-backend-in-visual-studio.aspx)  
  
-   Azure 網站上的遠端偵錯簡介 ([第 1 部分](http://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/)，[第 2 部分](http://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/)，[第 3 部分](http://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/))。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md)   
 [設定 Windows 防火牆進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [在執行 IIS 的遠端電腦上對 ASP.NET 進行遠端偵錯](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)



