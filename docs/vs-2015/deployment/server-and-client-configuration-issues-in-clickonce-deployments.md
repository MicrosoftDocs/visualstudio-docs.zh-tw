---
title: 伺服器和 ClickOnce 部署中的用戶端組態問題 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- Windows applications, ClickOnce deployments
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 008e7991c8f88fb1c5a8b2eb99659ebe9134df26
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942142"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>ClickOnce 部署中的伺服器和用戶端組態問題
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您在 Windows Server 上使用 Internet Information Services (IIS)，而且您的部署包含 Windows 無法辨識的檔案類型，例如 Microsoft Word 檔案，IIS 將會拒絕傳送該檔案中，與您的部署將不會成功。  
  
 此外，某些網頁伺服器和 Web 應用程式軟體，例如[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]、 包含一份檔案和檔案類型，您無法下載。 比方說，[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]會防止下載的所有 Web.config 檔案。 這些檔案可能包含機密資訊，例如使用者名稱和密碼。  
  
 雖然這項限制應該不造成任何問題，下載核心[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]檔案，例如資訊清單和組件，這項限制可能會導致您無法下載資料檔案中包含您[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式。 在  [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]，您可以藉由移除的處理常式，會禁止從 IIS configuration manager 這類檔案的下載來解決這個錯誤。 請參閱 IIS 伺服器文件，如需詳細資訊。  
  
 某些網頁伺服器可能會封鎖副檔名為.dll、.config，等.mdf 檔案。 以 Windows 為基礎的應用程式通常會包含這些延伸模組的某些檔案。 如果使用者嘗試執行[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]存取封鎖的檔案，在 Web 伺服器上的應用程式，將會產生錯誤。 而不是解除封鎖所有的檔案副檔名，[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]發佈".deploy"副檔名的每個應用程式檔案發佈的預設值。 因此，系統管理員只需要設定 Web 伺服器，以解除封鎖下列三個檔案延伸模組：  
  
- .application  
  
- .manifest  
  
- .deploy  
  
  不過，您可以停用此選項藉由清除**使用".deploy"副檔名**選項[發行選項 對話方塊中](http://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592)，在此情況下，您必須設定網頁伺服器，以解除封鎖所有的檔案副檔名在應用程式中使用。  
  
  您必須設定.manifest、.application，以及使用.deploy，比方說，如果您使用未安裝了的 IIS [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]，或如果您使用另一部 Web 伺服器 (例如 Apache)。  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce 和安全通訊端層 (SSL)  
 A[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式將會正常運作透過 SSL，但 Internet Explorer 時引發的 SSL 憑證的相關提示。 沒有發生問題的憑證，例如當站台名稱不相符或憑證已過期時，可能會引發的提示。 若要讓[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]工作透過 SSL 連線，請確定憑證是最新狀態，和憑證資料比對的站台資料。  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce 和 Proxy 驗證  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Windows 整合式的 proxy 驗證從.NET Framework 3.5 開始提供支援。 需要任何特定的 machine.config 指示詞不。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 其他的驗證通訊協定，例如基本或摘要式不提供支援。  
  
 您也可以套用 hotfix，若要啟用這項功能的.NET Framework 2.0。 如需詳細資訊，請參閱 http://go.microsoft.com/fwlink/?LinkId=158730。  
  
 如需詳細資訊，請參閱 < [ \<defaultProxy > 項目 （網路設定）](http://msdn.microsoft.com/library/9d663c4b-07b4-4f6f-9b12-efbd3630354f)。  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce 和 Web 瀏覽器相容性  
 目前，[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]安裝使用 Internet Explorer 開啟部署資訊清單的 URL 時，才啟動。 只有當 Internet Explorer 設定為預設網頁瀏覽器，將會成功啟動其 URL 從另一個應用程式，例如 Microsoft Office Outlook、 啟動部署。  
  
> [!NOTE]
>  如果部署提供者不是空白或已安裝 Microsoft.NET Framework Assistant 延伸模組，則支援 Mozilla Firefox。 此延伸模組會封裝與.NET Framework 3.5 SP1。 如需 XBAP 支援，需要時啟動 NPWPF 外掛程式。  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>啟動 ClickOnce 應用程式，透過瀏覽器的指令碼  
 如果您開發自訂的網頁，可啟動[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式使用動態指令碼中，您可能會發現某些電腦上不會啟動應用程式。 Internet Explorer 包含設定，稱為**自動提示下載檔案**，這會影響這個行為。 此設定可用於**安全性**索引標籤中其**選項**影響這個行為的功能表。 它會呼叫**自動提示下載檔案**，而且列於下方**下載**類別目錄。 屬性設定為**啟用**根據預設，內部網路網頁，以及**停用**預設會針對網際網路的網頁。 當此設定設為**停用**，任何嘗試啟動[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式以程式設計方式 (比方說，是藉由指派至其 URL`document.location`屬性) 將會遭到封鎖。 在此情況下，使用者可以啟動應用程式只能透過使用者起始的下載，比方說，依序按一下 設為 應用程式的 URL 超連結。  
  
## <a name="additional-server-configuration-issues"></a>其他伺服器組態問題  
  
##### <a name="administrator-permissions-required"></a>所需的系統管理員權限  
 如果您要使用 HTTP 發行，必須在目標伺服器上具有系統管理員權限。 IIS 會需要此權限層級。 如果您未將發佈使用 HTTP，您只需要寫入權限的目標路徑。  
  
##### <a name="server-authentication-issues"></a>伺服器驗證問題  
 當您發行至已關閉 [匿名存取] 的遠端伺服器時，您會收到下列警告：  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  您可以進行 NTLM （NT 挑戰-回應） 驗證，如果站台會提示輸入您的預設認證以外的認證，並在 [安全性] 對話方塊中，按一下**確定**提示您時如果您想要儲存所提供未來的工作階段的認證。 不過，這個因應措施不適用於基本驗證。  
  
## <a name="using-third-party-web-servers"></a>使用第三方 Web 伺服器  
 如果您要部署[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]從 Web 伺服器，而不是 IIS 的應用程式，您可能會遇到的問題，如果伺服器傳回的內容金鑰類型不正確[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]檔案，例如部署資訊清單和應用程式資訊清單。 若要解決此問題，請參閱有關如何將新的內容類型加入至伺服器，並確定所有的檔案名稱副檔名對應，列出下表中的文件已備妥的網頁伺服器的說明。  
  
|副檔名|內容類型|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce 和對應的磁碟機  
 如果您使用 Visual Studio 來發行 ClickOnce 應用程式時，您無法指定對應的磁碟機做為安裝位置。 不過，您可以修改 ClickOnce 應用程式，若要使用的資訊清單產生器和編輯器 （Mage.exe 和 MageUI.exe） 安裝的磁碟機。 如需詳細資訊，請參閱 < [Mage.exe （資訊清單產生和編輯工具）](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)並[MageUI.exe (圖形用戶端、資訊清單產生和編輯工具)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)。  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>FTP 通訊協定不支援如安裝應用程式  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 從任何 HTTP 1.1 Web 伺服器或檔案伺服器安裝應用程式的支援。 FTP 檔案傳輸通訊協定不支援如安裝應用程式。 您可以使用 FTP 發行應用程式。 下表摘要說明這些差異：  
  
|URL 類型|描述|  
|--------------|-----------------|  
|ftp://|您可以發佈[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式使用此通訊協定。|  
|http://|您可以安裝[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式使用此通訊協定。|  
|https://|您可以安裝[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式使用此通訊協定。|  
|file://|您可以安裝[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式使用此通訊協定。|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2：Windows 防火牆  
 根據預設，Windows XP SP2 會啟用 Windows 防火牆。 如果您正在開發您的應用程式已安裝的 Windows XP 的電腦上，您就仍然能夠發行和執行[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]從本機伺服器執行 IIS 的應用程式。 不過，您無法存取該伺服器是從另一部電腦執行 IIS，除非您開啟 Windows 防火牆。 如需管理 Windows 防火牆的指示，請參閱 Windows 說明。  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server：啟用 FrontPage server extensions  
 應用程式發佈到使用 HTTP 的 Windows Web 伺服器需要 Microsoft 的 FrontPage Server Extensions。  
  
 根據預設，Windows Server 並沒有安裝的 FrontPage Server Extensions。 如果您想要使用[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]来發行至 Windows Server 網頁伺服器會使用 FrontPage Server Extensions 中的 HTTP，您必須先安裝 FrontPage Server Extensions。 您可以使用 Windows Server 中的 管理您的伺服器管理工具來執行安裝。  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server：鎖定的內容類型  
 上的 IIS[!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)]鎖定特定已知的內容類型 （例如.htm、.html、.txt 等等） 以外的所有檔案類型。 若要啟用部署[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]使用此伺服器應用程式，您需要變更 IIS 設定，以允許下載類型.application.manifest 及您的應用程式所使用的任何其他自訂的檔案類型的檔案。  
  
 如果您使用 IIS 伺服器部署，執行 inetmgr.exe，並新增新的檔案類型的預設網頁：  
  
- .application 和.manifest 的擴充功能，MIME 類型應該是 「 應用程式/x-ms-應用程式。 」 其他檔案類型，MIME 類型應該是 「 應用程式/八位元資料流。 」  
  
- 如果您建立副檔名的 MIME 類型 「 * 」 和 「 應用程式/八位元資料流 」 MIME 類型，它會允許遭封鎖的檔案類型，若要下載的檔案。 （不過，封鎖無法下載類型，例如.aspx 和.asmx 檔案）。  
  
  如需在 Windows Server 中設定 MIME 類型的特定指示，請參閱 Microsoft 知識庫文件 KB326965，「 IIS 6.0 不會不提供未知 MIME 類型 」， [ http://support.microsoft.com/default.aspx?scid=kb; en-us-我們; 326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965)。  
  
## <a name="content-type-mappings"></a>內容類型對應  
 .Application 檔案的內容類型 （也稱為 MIME 類型） 發行時透過 HTTP，應該是 「 應用程式/x-ms-應用程式。 」 如果您有[!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]安裝在伺服器上，這會為您自動設定。 如果未安裝，則您需要建立新的 MIME 類型關聯，如[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式 vroot （或整部伺服器）。  
  
 如果您使用 IIS 伺服器部署，執行 inetmgr.exe，並加入新的 「 應用程式/x-ms-應用程式 」.application 副檔名做為內容類型。  
  
## <a name="http-compression-issues"></a>HTTP 壓縮的問題  
 使用[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]，您可以執行使用 HTTP 壓縮的下載、 使用 GZIP 演算法來壓縮資料流，再將資料流傳送至用戶端的 Web 伺服器技術。 用戶端 — 在此情況下， [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]— 解壓縮資料流之前讀取檔案。  
  
 如果您使用 IIS，您可以輕鬆地啟用 HTTP 壓縮。 不過，當您啟用 HTTP 壓縮，它才會啟用為特定檔案類型，也就是，HTML 和文字的檔案。 若要啟用組件 (.dll) 的壓縮，XML (.xml)、 部署資訊清單 (.application)，以及應用程式資訊清單 (.manifest)，您必須加入這些檔案類型的 IIS 壓縮的類型清單。 直到您將檔案類型新增至您的部署時，只有 「 文字 」 和 「 HTML 檔案將會壓縮。  
  
 如需 iis 的詳細指示，請參閱[如何指定其他的文件類型的 HTTP 壓縮](http://go.microsoft.com/fwlink/?LinkId=178459)。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解 ClickOnce 部署](../deployment/troubleshooting-clickonce-deployments.md)   
 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)
