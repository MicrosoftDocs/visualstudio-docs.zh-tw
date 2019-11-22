---
title: ClickOnce 部署中的伺服器和用戶端設定問題 |Microsoft Docs
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
ms.openlocfilehash: 5a78fab1986c7fae50bbb4c8149e8f2c89ec4873
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295205"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>ClickOnce 部署中的伺服器和用戶端組態問題
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您使用 Windows Server 上的 Internet Information Services （IIS），而且您的部署包含 Windows 無法辨識的檔案類型（例如 Microsoft Word 檔案），則 IIS 會拒絕傳送該檔案，而且您的部署將會失敗。  
  
 此外，某些 Web 服務器和 Web 應用程式軟體（例如 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]）包含無法下載的檔案和檔案類型清單。 例如，[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 會防止下載所有的 web.config 檔案。 這些檔案可能包含機密資訊，例如使用者名稱和密碼。  
  
 雖然這項限制應該不會造成下載核心 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 檔案（例如資訊清單和元件）的問題，但這項限制可能會讓您無法下載 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式中所包含的資料檔案。 在 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]中，您可以藉由移除禁止從 IIS 設定管理員下載這類檔案的處理常式來解決這個錯誤。 如需其他詳細資料，請參閱 IIS 伺服器檔。  
  
 有些 Web 服務器可能會封鎖副檔名為 .dll、.config 和 .mdf 的檔案。 以 Windows 為基礎的應用程式通常會包含具有其中一些延伸模組的檔案。 如果使用者嘗試執行存取 Web 服務器上封鎖之檔案的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式，將會產生錯誤。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 預設會發佈具有 ". deploy" 副檔名的每個應用程式檔，而不是解除封鎖所有副檔名。 因此，系統管理員只需要將 Web 服務器設定為解除封鎖下列三個副檔名：  
  
- .application  
  
- .manifest  
  
- .deploy  
  
  不過，您可以藉由清除 [[發行選項] 對話方塊](https://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592)上的 [**使用] [部署] 副檔名**選項來停用此選項，在此情況下，您必須設定網頁伺服器解除封鎖應用程式中使用的所有副檔名。  
  
  例如，如果您使用未安裝 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]的 IIS，或者您使用的是其他網頁伺服器（例如 Apache），您就必須設定資訊清單、. 應用程式和部署。  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce 和安全通訊端層（SSL）  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 的應用程式在 SSL 上可以正常運作，但 Internet Explorer 引發 SSL 憑證的提示時除外。 當憑證發生問題，例如當網站名稱不相符或憑證已過期時，就會引發提示。 若要讓 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 透過 SSL 連線進行工作，請確定憑證是最新的，而且憑證資料符合網站資料。  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce 和 Proxy 驗證  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 提供從 .NET Framework 3.5 開始的 Windows 整合式 proxy 驗證支援。 不需要特定的 machine.config 指示詞。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 不提供其他驗證通訊協定（例如基本或摘要）的支援。  
  
 您也可以將修補程式套用至 .NET Framework 2.0，以啟用這項功能。 如需詳細資訊，請參閱 https://go.microsoft.com/fwlink/?LinkId=158730。  
  
 如需詳細資訊，請參閱[\<defaultProxy > 元素（網路設定）](https://msdn.microsoft.com/library/9d663c4b-07b4-4f6f-9b12-efbd3630354f)。  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce 和 Web 瀏覽器相容性  
 目前，只有在使用 Internet Explorer 開啟部署資訊清單的 URL 時，才會啟動 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 安裝。 只有當 Internet Explorer 設定為預設網頁瀏覽器時，才會從另一個應用程式（例如 Microsoft Office Outlook）啟動其 URL 的部署。  
  
> [!NOTE]
> 如果部署提供者不是空白或已安裝 Microsoft .NET Framework Assistant 延伸模組，則會支援 Mozilla Firefox。 此延伸模組會與 .NET Framework 3.5 SP1 封裝在一起。 針對 XBAP 支援，NPWPF 外掛程式會在需要時啟用。  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>透過瀏覽器腳本啟用 ClickOnce 應用程式  
 如果您開發了使用動態指令碼啟動 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式的自訂網頁，您可能會發現應用程式不會在某些電腦上啟動。 Internet Explorer 包含名為 [**自動提示檔案下載**] 的設定，這會影響此行為。 此設定可在其 [**選項**] 功能表中影響此行為的 [**安全性**] 索引標籤上取得。 系統會**針對檔案下載呼叫自動提示**，而且它會列在 [**下載**] 類別之下。 針對內部網路網頁，預設會將屬性設定為 [**啟用**]，並預設為針對網際網路網頁**停**用。 當此設定設為 [**停**用] 時，任何以程式設計方式啟動 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式的嘗試（例如，藉由將其 URL 指派給 `document.location` 屬性）都會遭到封鎖。 在此情況下，使用者只能透過使用者起始的下載來啟動應用程式，例如，按一下設定為應用程式 URL 的超連結。  
  
## <a name="additional-server-configuration-issues"></a>其他伺服器設定問題  
  
##### <a name="administrator-permissions-required"></a>需要系統管理員許可權  
 如果您使用 HTTP 發佈，則必須擁有目標伺服器的系統管理員許可權。 IIS 需要此許可權層級。 如果您不是使用 HTTP 發行，則只需要目標路徑的寫入權限。  
  
##### <a name="server-authentication-issues"></a>伺服器驗證問題  
 當您發行至已關閉「匿名存取」的遠端伺服器時，您會收到下列警告：  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
> 如果網站提示您輸入預設認證以外的認證，您可以進行 NTLM （NT 挑戰-回應）驗證，而在 [安全性] 對話方塊中，當系統提示您是否要儲存提供的認證供未來的會話使用時，請按一下 **[確定]** 。 不過，這種因應措施不適用於基本驗證。  
  
## <a name="using-third-party-web-servers"></a>使用協力廠商 Web 服務器  
 如果您要從 IIS 以外的 Web 服務器部署 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式，則可能會在伺服器傳回不正確的金鑰 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 檔案內容類型（例如部署資訊清單和應用程式資訊清單）時遇到問題。 若要解決此問題，請參閱您的網頁伺服器說明文件，以瞭解如何將新的內容類型新增至伺服器，並確定下表所列的所有副檔名對應皆已就緒。  
  
|副檔名|內容類型|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce 和對應的磁片磁碟機  
 如果您使用 Visual Studio 發行 ClickOnce 應用程式，則無法指定映射磁碟機做為安裝位置。 不過，您可以使用資訊清單產生器和編輯器（Mage.exe 和 Mageui.exe）修改 ClickOnce 應用程式，以便從對應的磁片磁碟機安裝。 如需詳細資訊，請參閱 < [Mage.exe （資訊清單產生和編輯工具）](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)並[MageUI.exe (圖形用戶端、資訊清單產生和編輯工具)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)。  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>不支援安裝應用程式的 FTP 通訊協定  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 支援從任何 HTTP 1.1 Web 服務器或檔案伺服器安裝應用程式。 安裝應用程式時，不支援 FTP、檔案傳輸通訊協定。 您只能使用 FTP 來發佈應用程式。 下表摘要說明這些差異：  
  
|URL 類型|描述|  
|--------------|-----------------|  
|ftp://|您可以使用此通訊協定來發行 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式。|  
|http://|您可以使用此通訊協定來安裝 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式。|  
|https://|您可以使用此通訊協定來安裝 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式。|  
|file://|您可以使用此通訊協定來安裝 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式。|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2： Windows 防火牆  
 根據預設，Windows XP SP2 會啟用 Windows 防火牆。 如果您是在已安裝 Windows XP 的電腦上開發應用程式，您仍然可以從執行 IIS 的本機伺服器發佈和執行 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式。 不過，除非您開啟 Windows 防火牆，否則無法從另一部電腦存取正在執行 IIS 的伺服器。 如需管理 Windows 防火牆的指示，請參閱 Windows 說明。  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server：啟用 FrontPage Server extensions  
 將應用程式發行至使用 HTTP 的 Windows Web 服務器時，需要 Microsoft 的 FrontPage Server Extensions。  
  
 根據預設，Windows Server 不會安裝 FrontPage Server Extensions。 如果您想要使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 發行至使用 HTTP 搭配 FrontPage Server Extensions 的 Windows Server Web 服務器，您必須先安裝 FrontPage Server Extensions。 您可以使用 Windows Server 中的 [管理您的伺服器管理] 工具來執行安裝。  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server：已鎖定內容類型  
 [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] 上的 IIS 會鎖定所有檔案類型，但某些已知的內容類型除外（例如 .htm、.html、.txt 等等）。 若要使用這部伺服器啟用 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式的部署，您需要變更 IIS 設定，以允許下載檔案類型. application、.manifest 和應用程式所使用的任何其他自訂檔案類型。  
  
 如果您使用 IIS 伺服器進行部署，請執行 inetmgr .exe 並加入預設網頁的新檔案類型：  
  
- 針對. 應用程式和資訊清單延伸模組，MIME 類型應為 "application/x-ms-應用程式"。 若為其他檔案類型，MIME 類型應為「應用程式/八位串流」。  
  
- 如果您建立副檔名為 "*" 且 MIME 類型為 "application/八進位-stream" 的 MIME 類型，則會允許下載已解除封鎖的檔案類型檔案。 （不過，無法下載已封鎖的檔案類型，例如 .aspx 和 .asmx）。  
  
  如需有關在 Windows Server 上設定 MIME 類型的特定指示，請參閱 Microsoft 知識庫文章 KB326965 「IIS 6.0 不提供未知的 MIME 類型」（位於[https://support.microsoft.com/default.aspx?scid=kb; en-us; 326965](https://support.microsoft.com/default.aspx?scid=kb;en-us;326965)）。  
  
## <a name="content-type-mappings"></a>內容類型對應  
 透過 HTTP 發佈時，應用程式檔的內容類型（也稱為 MIME 類型）應為 "application/x-ms-應用程式"。 如果您已在伺服器上安裝 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]，就會自動為您設定。 如果未安裝，則您需要為 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式 vroot （或整部伺服器）建立 MIME 類型關聯。  
  
 如果您使用 IIS 伺服器進行部署，請執行 inetmgr，並為應用程式延伸模組新增 "application/x-ms-應用程式" 內容類型。  
  
## <a name="http-compression-issues"></a>HTTP 壓縮問題  
 使用 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]，您可以執行使用 HTTP 壓縮的下載，這是一種 Web 服務器技術，使用 GZIP 演算法來壓縮資料流程，然後再將資料流程傳送至用戶端。 用戶端（在此案例中為 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]）會在讀取檔案之前先解壓縮串流。  
  
 如果您使用 IIS，您可以輕鬆地啟用 HTTP 壓縮。 不過，當您啟用 HTTP 壓縮時，它只會針對特定檔案類型（也就是 HTML 和文字檔）啟用。 若要啟用元件（.dll）、XML （.xml）、部署資訊清單（. 應用程式）和應用程式資訊清單（.manifest）的壓縮，您必須將這些檔案類型新增至要壓縮的類型清單。 在您將檔案類型新增至部署之前，只會壓縮文字和 HTML 檔案。  
  
 如需 IIS 的詳細指示，請參閱[如何指定 HTTP 壓縮的其他檔案類型](https://go.microsoft.com/fwlink/?LinkId=178459)。  
  
## <a name="see-also"></a>另請參閱  
 針對[ClickOnce 部署進行疑難排解](../deployment/troubleshooting-clickonce-deployments.md)   
 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)
