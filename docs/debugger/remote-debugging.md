---
title: Visual Studio 遠端偵錯 |Microsoft Docs
ms.custom: remotedebugging
ms.date: 07/02/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 46913c1bb671c1986c4f302a84d4183fe17f5878
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38778290"
---
# <a name="remote-debugging"></a>Remote Debugging
您可以偵錯已部署在不同電腦的 Visual Studio 應用程式。 若要這樣做，您可以使用 Visual Studio 遠端偵錯工具。

如需有關遠端偵錯的深入指示，請參閱下列主題。

|情節|連結|
|-|-|-|
|Azure App Service|[快照集偵錯工具](../debugger/debug-live-azure-applications.md)或[遠端偵錯在 Azure 上的 ASP.NET](../debugger/remote-debugging-azure.md)|
|Azure VM|[在 Azure 上對 ASP.NET 進行遠端偵錯](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[偵錯 Azure Service Fabric 應用程式](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[遠端偵錯 ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)或[遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# 或 Visual Basic|[遠端偵錯 C# 或 Visual Basic 專案](../debugger/remote-debugging-csharp.md)|
|C++|[對 C++ 專案進行遠端偵錯](../debugger/remote-debugging-cpp.md)|
|通用 Windows App (UWP)|[在遠端電腦上執行 UWP app](../debugger/run-windows-store-apps-on-a-remote-machine.md)或[偵錯已安裝的應用程式套件](../debugger/debug-installed-app-package.md)|

如果您只想要下載並安裝遠端偵錯工具，而不需要任何額外的指示，針對您的案例，請遵循這篇文章中的步驟。

## <a name="download-and-install-the-remote-tools"></a>下載並安裝遠端工具

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="unblock_msvsmon"></a> 解除封鎖 Windows Server 上的遠端工具下載

在 Windows Server 上的 Internet Explorer 中的預設安全性設定可以讓它更耗時下載元件，例如遠端工具。

* Internet Explorer 中，它會防止您從開啟網站，並存取 web 資源，除非明確允許包含資源的網域上啟用增強式的安全性設定 （也就是受信任）。 雖然您可以停用此設定，但我們不建議它因為這會造成安全性風險。

* 在 Windows Server 2016 中設定的預設值**網際網路選項** > **安全性** > **網際網路** >  **自訂層級** > **下載**也會停用檔案的下載。 如果您選擇下載直接在 Windows Server 上的遠端工具，您必須啟用檔案下載。

若要下載 Windows Server 上的工具，我們建議下列其中一項：

* 下載像是一個執行的 Visual Studio，在不同電腦上的遠端工具，然後複製 *.exe*到 Windows Server 的檔案。

* 執行遠端偵錯工具[從檔案共用](#fileshare_msvsmon)Visual Studio 電腦上。

* 下載直接在 Windows Server 上的遠端工具，並接受提示來加入信任的網站。 現代化網站通常會包含許多協力廠商資源，因此這可能會導致大量的提示。 此外，任何重新導向的連結可能需要手動加入。 您可以選擇將部分信任的網站開始下載之前。 移至**網際網路選項 > 安全性 > 受信任的站台 > 網站**然後新增下列站台。

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * 關於： 空白

  針對舊版 my.visualstudio.com 的偵錯工具中，加入這些額外的站台，以確定該登入成功：

  * microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * my.visualstudio.com
  * login.microsoftonline.com
  * login.live.com
  * secure.aadcdn.microsoftonline-p.com
  * msft.sts.microsoft.com
  * auth.gfx.ms
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * query.prod.cms.rt.microsoft.com

    如果您選擇將這些網域加入下載遠端工具時，請選擇**新增**出現提示時。

    ![已封鎖的內容對話方塊](../debugger/media/remotedbg-blocked-content.png)

    當您下載軟體時，您會取得載入各種 web 站台指令碼和資源的權限授與某些其他要求。 My.visualstudio.com，建議您新增其他網域，以確定該登入成功。

## <a name="requirements_msvsmon"></a> 需求

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="fileshare_msvsmon"></a> （選擇性）若要從檔案共用執行遠端偵錯工具

您可以找到遠端偵錯工具 (*msvsmon.exe*) Visual Studio Community、 Professional 或 Enterprise 已安裝的電腦上。 某些情況下，設定遠端偵錯的最簡單方式是從檔案共用執行遠端偵錯工具 (msvsmon.exe)。 如需使用方式限制，請參閱遠端偵錯工具的 [說明] 頁面 (**協助 > 使用量**遠端偵錯工具中)。

1. 尋找*msvsmon.exe*比對您的 Visual Studio 版本的目錄中。 Visual Studio enterprise 2017:

      *程式檔案 (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

      *程式檔案 (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

2. 共用**遠端偵錯工具**Visual Studio 電腦上的資料夾。

3. 在遠端電腦上，執行*msvsmon.exe*從共用資料夾。 請遵循[安裝指示](#bkmk_setup)。

> [!TIP]
> 命令列安裝和命令列參考，請參閱 說明網頁*msvsmon.exe*輸入``msvsmon.exe /?``已安裝 Visual studio 的電腦上的命令列中 (或移至**協助 > 使用量**遠端偵錯工具中)。

## <a name="bkmk_setup"></a> 設定遠端偵錯工具

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure_msvsmon"></a> 設定遠端偵錯工具
在您第一次啟動遠端偵錯工具後，可以變更其組態的某些部分。

-   如果您要新增為連線到遠端偵錯工具，請選擇其他使用者的權限**工具 > 權限**。 您必須具有系統管理員權限才能授與或拒絕使用權限。

     > [!IMPORTANT]
     > 您可以從您的 Visual Studio 電腦，使用的使用者帳戶來執行遠端偵錯工具在不同的使用者帳戶下，但您必須將不同的使用者帳戶加入遠端偵錯工具的權限。

     或者，您可以從命令列啟動遠端偵錯工具 **/allow\<使用者名稱 >** 參數： **msvsmon /allow \< username@computer>**。

-   如果您需要變更驗證模式或連接埠號碼，或指定遠端工具的逾時值： 選擇**工具 > 選項**。

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

     您可能需要新增**做為服務登入**權利加入此帳戶的使用者 (尋找**本機安全性原則**(secpol.msc) 中**啟動**頁面或視窗 (或類型**secpol**在命令提示字元)。 視窗出現時，請按兩下 [使用者權限指派] ，然後在右窗格中尋找 [以服務方式登入]  。 對它按兩下。 將使用者帳戶加入**屬性**視窗，然後按一下**確定**)。 按 [ **下一步**]。

5.  選取您要遠端工具與之通訊的網路類型。 必須至少選取一種網路類型。 如果此電腦經由網域連線，您就必須選擇第一個項目。 如果此電腦經由工作群組或家用群組連線，您就必須選擇第二個或第三個項目。 按 [ **下一步**]。

6.  如果可以啟動服務，您就會看到 [您已順利完成 Visual Studio 遠端偵錯工具組態精靈] 。 如果無法啟動服務，您就會看到 [無法完成 Visual Studio 遠端偵錯工具組態精靈] 。 此頁面也會提供啟動服務所需遵循的一些祕訣。

7.  按一下 [ **完成**]。

 此時 [遠端偵錯工具] 會以服務方式執行。 您可以驗證，請前往**控制台 > 服務**並尋找**Visual Studio 2015 遠端偵錯工具**。

 您可以停止和啟動遠端偵錯工具服務，從**控制台 > 服務**。

## <a name="set-up-debugging-with-remote-symbols"></a>設定遠端符號偵錯

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>另請參閱

- [偵錯工具功能導覽](../debugger/debugger-feature-tour.md)
- [設定 Windows 防火牆進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)
- [遠端偵錯 IIS 的遠端電腦上的 ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)