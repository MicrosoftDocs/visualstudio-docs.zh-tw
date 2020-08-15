---
title: ClickOnce 部署中的伺服器/用戶端設定問題
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ec07e71e57c0b3875d690773b7ff2618269b8f4
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250003"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>ClickOnce 部署中的伺服器和用戶端組態問題
如果您使用 Internet Information Services (Windows Server 上的 IIS) ，而您的部署包含 Windows 無法辨識的檔案類型（例如 Microsoft Word 檔案），則 IIS 會拒絕傳送該檔案，且您的部署將會失敗。

 此外，某些 Web 服務器和 Web 應用程式軟體（例如 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ）包含您無法下載的檔案和檔案類型清單。 例如， [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 會防止下載所有的 *Web.config* 檔案。 這些檔案可能包含機密資訊，例如使用者名稱和密碼。

 雖然這項限制應該不會造成下載核心檔案 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] （例如資訊清單和元件）的問題，但這項限制可能會讓您無法下載包含在應用程式中的資料檔案 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 在中 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ，您可以藉由移除禁止從 IIS 設定管理員下載這類檔案的處理常式來解決這個錯誤。 如需其他詳細資料，請參閱 IIS 伺服器檔。

 有些 Web 服務器可能會封鎖副檔名為 *.dll*、 *.config*和 *.mdf*的檔案。 以 Windows 為基礎的應用程式通常會包含具有其中一些延伸模組的檔案。 如果使用者嘗試執行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 存取 Web 服務器上封鎖之檔案的應用程式，將會產生錯誤。 根據預設，不會解除封鎖所有副檔名，而是會 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 發佈每個應用程式檔，並使用 *.deploy 副檔名。* 因此，系統管理員只需要將 Web 服務器設定為解除封鎖下列三個副檔名：

- *。應用程式*

- *.manifest*

- *。部署*

  不過，您可以藉由清除 [[發行選項] 對話方塊](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100))上的 [**使用] [部署] 副檔名**選項來停用此選項，在此情況下，您必須設定網頁伺服器解除封鎖應用程式中使用的所有副檔名。

  例如，如果您使用未安裝 .NET Framework 的 IIS，或使用另一部 Web 服務器 (例如 Apache) ，則必須設定*資訊清單*、 *. 應用程式*和 *。*

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce 和安全通訊端層 (SSL) 
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式將可透過 ssl 正常運作，但 Internet Explorer 引發 ssl 憑證提示時除外。 當憑證發生問題，例如當網站名稱不相符或憑證已過期時，就會引發提示。 若要透過 SSL 連線進行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 工作，請確定憑證是最新的，而且憑證資料符合網站資料。

## <a name="clickonce-and-proxy-authentication"></a>ClickOnce 和 proxy 驗證
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 提供從 .NET Framework 3.5 開始的 Windows 整合式 proxy 驗證支援。 不需要特定的 machine.config 指示詞。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 不提供其他驗證通訊協定（例如基本或摘要）的支援。

 您也可以將修補程式套用至 .NET Framework 2.0，以啟用這項功能。 如需詳細資訊，請參閱 [FIX：當您嘗試將在 .NET Framework 2.0 中建立的 ClickOnce 應用程式安裝到設定為使用 proxy 伺服器的用戶端電腦時，請參閱修正 .. 錯誤訊息：「需要 proxy 驗證](https://support.microsoft.com/help/917952/fix-error-message-when-you-try-to-install-a-clickonce-application-that)」。

 如需詳細資訊，請參閱[ \<defaultProxy> (網路設定) 的元素](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings)。

## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce 和 Web 瀏覽器相容性
 目前， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 只有在使用 Internet Explorer 開啟部署資訊清單的 URL 時，才會啟動安裝。 只有當 Internet Explorer 設定為預設網頁瀏覽器時，才會從另一個應用程式（例如 Microsoft Office Outlook）啟動其 URL 的部署。

> [!NOTE]
> 如果部署提供者不是空白或已安裝 Microsoft .NET Framework Assistant 延伸模組，則會支援 Mozilla Firefox。 此延伸模組會與 .NET Framework 3.5 SP1 封裝在一起。 針對 XBAP 支援，NPWPF 外掛程式會在需要時啟用。

## <a name="activate-clickonce-applications-through-browser-scripting"></a>透過瀏覽器腳本啟動 ClickOnce 應用程式
 如果您開發了 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用動態指令碼啟動應用程式的自訂網頁，您可能會發現應用程式不會在某些電腦上啟動。 Internet Explorer 包含名為 [ **自動提示檔案下載**] 的設定，這會影響此行為。 此設定可在其 [**選項**] 功能表中影響此行為的 [**安全性**] 索引標籤上取得。 系統會 **針對檔案下載呼叫自動提示**，而且它會列在 [ **下載** ] 類別之下。 針對內部網路網頁，預設會將屬性設定為 [ **啟用** ]，並預設為針對網際網路網頁 **停** 用。 當此設定設為 [ **停**用] 時，任何嘗試以 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 程式設計方式啟動應用程式 (例如，藉由將其 URL 指派給 `document.location` 屬性) 將會遭到封鎖。 在此情況下，使用者只能透過使用者起始的下載來啟動應用程式，例如，按一下設定為應用程式 URL 的超連結。

## <a name="additional-server-configuration-issues"></a>其他伺服器設定問題

##### <a name="administrator-permissions-required"></a>需要系統管理員許可權
 如果您使用 HTTP 發佈，則必須擁有目標伺服器的系統管理員許可權。 IIS 需要此許可權層級。 如果您不是使用 HTTP 發行，則只需要目標路徑的寫入權限。

##### <a name="server-authentication-issues"></a>伺服器驗證問題
 當您發行至已關閉「匿名存取」的遠端伺服器時，您會收到下列警告：

```
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."
```

> [!NOTE]
> 如果網站提示您輸入預設認證以外的認證，您可以讓 NTLM (NT 挑戰回應) 驗證工作，然後在 [安全性] 對話方塊中，當系統提示您是否要儲存提供的認證供未來會話使用時，請按一下 **[確定]** 。 不過，這種因應措施不適用於基本驗證。

## <a name="use-third-party-web-servers"></a>使用協力廠商 Web 服務器
 如果您要 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 從 IIS 以外的 Web 服務器部署應用程式，則可能會在伺服器傳回不正確的金鑰檔內容類型（ [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 例如部署資訊清單和應用程式資訊清單）時遇到問題。 若要解決此問題，請參閱您的網頁伺服器說明文件，以瞭解如何將新的內容類型新增至伺服器，並確定下表所列的所有副檔名對應皆已就緒。

|副檔名|內容類型|
|-------------------------|------------------|
|`.application`|`application/x-ms-application`|
|`.manifest`|`application/x-ms-manifest`|
|`.deploy`|`application/octet-stream`|
|`.msu`|`application/octet-stream`|
|`.msp`|`application/octet-stream`|

## <a name="clickonce-and-mapped-drives"></a>ClickOnce 和對應的磁片磁碟機
 如果您使用 Visual Studio 發行 ClickOnce 應用程式，則無法指定映射磁碟機做為安裝位置。 不過，您可以使用資訊清單產生器和編輯器 ( # A0 和 MageUI.exe) ，修改 ClickOnce 應用程式以從對應的磁片磁碟機安裝。 如需詳細資訊，請參閱 < [Mage.exe （資訊清單產生和編輯工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)並[MageUI.exe (圖形用戶端、資訊清單產生和編輯工具)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)。

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>不支援安裝應用程式的 FTP 通訊協定
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 支援從任何 HTTP 1.1 Web 服務器或檔案伺服器安裝應用程式。 安裝應用程式時，不支援 FTP、檔案傳輸通訊協定。 您只能使用 FTP 來發佈應用程式。 下表摘要說明這些差異：

| URL 類型 | 描述 |
|----------| - |
| ftp:// | 您可以 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用此通訊協定來發行應用程式。 |
| http:// | 您可以 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用此通訊協定來安裝應用程式。 |
| https:// | 您可以 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用此通訊協定來安裝應用程式。 |
| file:// | 您可以 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用此通訊協定來安裝應用程式。 |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2： Windows 防火牆
 根據預設，Windows XP SP2 會啟用 Windows 防火牆。 如果您是在已安裝 Windows XP 的電腦上開發應用程式，您仍然可以 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 從執行 IIS 的本機伺服器發佈和執行應用程式。 不過，除非您開啟 Windows 防火牆，否則無法從另一部電腦存取正在執行 IIS 的伺服器。 如需管理 Windows 防火牆的指示，請參閱 Windows 說明。

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server：啟用 FrontPage Server extensions
 將應用程式發行至使用 HTTP 的 Windows Web 服務器時，需要 Microsoft 的 FrontPage Server Extensions。

 根據預設，Windows Server 不會安裝 FrontPage Server Extensions。 如果您想要使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 來發行至使用 HTTP 搭配 FrontPage Server Extensions 的 Windows Server Web 服務器，您必須先安裝 FrontPage Server Extensions。 您可以使用 Windows Server 中的 [管理您的伺服器管理] 工具來執行安裝。

## <a name="windows-server-locked-down-content-types"></a>Windows Server：已鎖定內容類型
 IIS on 會 [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] 鎖定所有檔案類型，但某些已知的內容類型除外 (例如， *.htm*、 *.html*、 *.txt*等等) 。 若要使用這部 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 伺服器啟用應用程式的部署，您需要變更 IIS 設定，以允許下載類型為 *. application*、 *.manifest*以及應用程式所使用的任何其他自訂檔案類型的檔。

 如果您使用 IIS 伺服器進行部署，請執行 *inetmgr.exe* 並新增預設網頁的新檔案類型：

- 針對 *. 應用程式* 和 *資訊清單* 延伸模組，MIME 類型應為 "application/x-ms-應用程式"。 若為其他檔案類型，MIME 類型應為「應用程式/八位串流」。

- 如果您建立副檔名為 " \<em> " 且 mime 類型為 "application/八進位-stream" 的 mime 類型，則會允許下載已解除封鎖的檔案類型檔案。  (不過，無法下載已封鎖的檔案類型，例如* \* .aspx*和* \* .asmx* 。 ) 

  如需在 Windows Server 上設定 MIME 類型的特定指示，請參閱 [如何將 mime 類型新增至網站或應用程式](/iis/configuration/system.webserver/staticcontent/mimemap#how-to-add-a-mime-type-to-a-web-site-or-application)。

## <a name="content-type-mappings"></a>內容類型對應
 透過 HTTP 發佈時， *應用* 程式檔的內容類型 (也稱為 MIME 類型) ，應該是 "application/x-ms-應用程式"。 如果您已在伺服器上安裝 .NET Framework 2.0，則會自動為您設定。 如果未安裝，則您需要為 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式 vroot (或整個伺服器) 建立 MIME 類型關聯。

 如果您使用 IIS 伺服器進行部署，請執行 <em>inetmgr。</em>exe，並為 *應用* 程式副檔名新增 "application/x-ms-應用程式" 內容類型。

## <a name="http-compression-issues"></a>HTTP 壓縮問題
 使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ，您可以執行使用 HTTP 壓縮的下載，這是一種 Web 服務器技術，使用 GZIP 演算法來壓縮資料流程，然後再將資料流程傳送至用戶端。 用戶端（在此案例中為）會在 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 讀取檔案之前解壓縮串流。

 如果您使用 IIS，您可以輕鬆地啟用 HTTP 壓縮。 不過，當您啟用 HTTP 壓縮時，它只會針對特定檔案類型（也就是 HTML 和文字檔）啟用。 若要啟用元件的壓縮 (*.dll*) 、xml (*.xml*) 、部署資訊清單 (*. 應用程式*) 以及應用程式指令 *清單 (中* ，您必須將這些檔案類型新增至要壓縮的類型清單中。 在您將檔案類型新增至部署之前，只會壓縮文字和 HTML 檔案。

 如需 IIS 的詳細指示，請參閱 [如何指定 HTTP 壓縮的其他檔案類型](https://support.microsoft.com/help/234497)。

## <a name="see-also"></a>另請參閱
- [針對 ClickOnce 部署進行疑難排解](../deployment/troubleshooting-clickonce-deployments.md)
- [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)
