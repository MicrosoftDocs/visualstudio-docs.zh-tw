---
title: 針對 ClickOnce 部署中的特定錯誤進行疑難排解 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: troubleshooting
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c66a25830e34571648727bd6ec71791e5e637ca8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294727"
---
# <a name="troubleshooting-specific-errors-in-clickonce-deployments"></a>疑難排解 ClickOnce 部署的特定錯誤
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題列出當您部署 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式時可能會發生的下列常見錯誤，並提供解決每個問題的步驟。  
  
## <a name="general-errors"></a>一般錯誤  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>當您嘗試找出應用程式檔時，不會發生任何事，或 Internet Explorer 中的 XML 轉譯，或是您收到 [執行] 或 [另存新檔] 對話方塊  
 此錯誤很可能是因為內容類型（也稱為 MIME 類型）未在伺服器或用戶端上正確註冊。  
  
 首先，請確定伺服器已設定為將應用程式延伸模組與內容類型 "application/x-ms-應用程式" 建立關聯。  
  
 如果伺服器設定正確，請確定您的電腦上已安裝 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]。 如果已安裝 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]，而且您仍然看到此問題，請嘗試卸載並重新安裝 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]，以在用戶端上重新註冊內容類型。  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>錯誤訊息顯示：「無法取得應用程式。 部署中缺少檔案」或「應用程式下載已中斷，請檢查網路錯誤，並于稍後再試一次」  
 此訊息表示無法下載 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 資訊清單所參考的一或多個檔案。 若要偵測此錯誤，最簡單的方式是嘗試下載 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 指出無法下載的 URL。 以下是一些可能的原因：  
  
- 如果記錄檔顯示「（403）禁止」或「（404）找不到」，請確認已設定 Web 服務器，使其不會封鎖此檔案的下載。 如需詳細資訊，請參閱 [ClickOnce 部署中的伺服器和用戶端組態問題](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)。  
  
- 如果伺服器正在封鎖 .config 檔案，請參閱本主題稍後的「當您嘗試安裝具有 .config 檔案的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式時，下載錯誤」一節。  
  
- 判斷是否發生這種情況，是因為部署資訊清單中的 `deploymentProvider` URL 指向的位置與用於啟用的 URL 不同。  
  
- 請確定所有檔案都存在於伺服器上;[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 記錄檔應該會告訴您找不到哪個檔案。  
  
- 查看是否有網路連線問題;如果您的用戶端電腦在下載期間離線，您可以收到此訊息。  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>當您嘗試安裝具有 .config 檔案的 ClickOnce 應用程式時，發生下載錯誤  
 根據預設，Visual Basic 的 Windows 應用程式會包含 App.config 檔案。 當使用者嘗試從使用 Windows Server 2003 的 Web 服務器進行安裝時，將會發生問題，因為該作業系統會因為安全性的緣故而封鎖 .config 檔案的安裝。 若要啟用要安裝的 .config 檔案，請按一下 [**發行選項**] 對話方塊中的 [**使用] [部署] 副檔名**。  
  
 您也必須針對. application、.manifest 和 deploy 檔案，適當地設定內容類型（也稱為 MIME 類型）。 如需詳細資訊，請參閱您的網頁伺服器檔。  
  
 如需詳細資訊，請參閱在[ClickOnce 部署中的伺服器和用戶端設定問題](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)中的「Windows Server 2003：鎖定的內容類型」。  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>錯誤訊息：「應用程式的格式不正確;」記錄檔包含「XML 簽章無效」  
 請確定您已更新資訊清單檔案，然後再次簽署它。 使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 重新發佈您的應用程式，或使用 Mage 再次簽署應用程式。  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>您已在伺服器上更新您的應用程式，但用戶端不會下載更新  
 您可以藉由完成下列其中一項工作來解決此問題：  
  
- 檢查部署資訊清單中的 `deploymentProvider` URL。 請確定您要更新 `deploymentProvider` 指向的相同位置中的位。  
  
- 確認部署資訊清單中的更新間隔。 如果此間隔設定為定期間隔（例如每隔六小時一次），[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 將不會掃描是否有更新，直到經過此間隔為止。 您可以變更資訊清單，以在每次應用程式啟動時掃描更新。 在開發期間，變更更新間隔是一個方便的選項，以驗證正在安裝的更新，但它會減緩應用程式啟用的速度。  
  
- 嘗試在 [開始] 功能表上再次啟動應用程式。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 可能已在背景中偵測到更新，但會提示您在下一次啟用時安裝位。  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>在更新期間，您會收到含有下列記錄專案的錯誤：「部署中的參考不符合應用程式資訊清單中定義的身分識別」  
 發生此錯誤的原因可能是您已手動編輯部署和應用程式資訊清單，並導致一個資訊清單中元件的識別身分描述與另一個資訊清單不同步。 元件的身分識別是由其名稱、版本、文化特性和公開金鑰 token 所組成。 請檢查資訊清單中的身分識別描述，並更正任何差異。  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>第一次從本機磁片或 CD-ROM 啟用時，將會成功，但從 [開始] 功能表後續啟用不會成功  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 會使用部署提供者 URL 來接收應用程式的更新。 確認 URL 指向的位置是正確的。  
  
#### <a name="error-cannot-start-the-application"></a>錯誤：「無法啟動應用程式」  
 此錯誤訊息通常表示將此應用程式安裝到 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 存放區時發生問題。 可能是應用程式發生錯誤或存放區已損毀。 記錄檔可能會告訴您發生錯誤的位置。  
  
 您應該執行下列動作：  
  
- 確認部署資訊清單的身分識別、應用程式資訊清單的身分識別，以及主要應用程式 EXE 的識別都是唯一的。  
  
- 請確認您的檔案路徑長度不超過100個字元。 如果您的應用程式包含太長的檔案路徑，您可能會超過可以儲存的最大路徑限制。 請嘗試縮短路徑，然後重新安裝。  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>不接受應用程式佈建檔中的 PrivatePath 設定  
 若要使用 PrivatePath （融合探查路徑），應用程式必須要求完全信任許可權。 請嘗試將應用程式資訊清單變更為 [要求完全信任]，然後再試一次。  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>卸載期間會出現訊息，指出「無法卸載應用程式」  
 此訊息通常表示應用程式已經移除，或存放區已損毀。 按一下 **[確定]** 之後，將會移除 [**新增/移除程式**] 專案。  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>在安裝期間，會出現一則訊息，指出未安裝平臺相依性。  
 您在 GAC （全域組件快取）中遺漏了應用程式執行所需的必要條件。  
  
## <a name="publishing-with-visual-studio"></a>使用 Visual Studio 發行  
  
#### <a name="publishing-in-visual-studio-fails"></a>在 Visual Studio 中發佈失敗  
 請確定您有權發行至您的目標伺服器。 例如，如果您以一般使用者（而不是系統管理員）身分登入終端機伺服器電腦，則可能不會有發佈到本機 Web 服務器所需的許可權。  
  
 如果您使用 URL 發行，請確定目的地電腦已啟用 FrontPage Server Extensions。  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>錯誤訊息：無法建立網站 '\<網站 > '。 未安裝與 FrontPage Server Extensions 通訊的元件。  
 請確定您已在要發佈的電腦上安裝 Microsoft Visual Studio Web Authoring Component。 若為 Express 使用者，預設不會安裝此元件。 如需詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=102310](https://go.microsoft.com/fwlink/?LinkId=102310)。  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>錯誤訊息：找不到檔案 ' Microsoft. Windows. 通用控制項，版本 = 6.0.0.0，Culture = *，PublicKeyToken = 6595b64144ccf1df，ProcessorArchitecture =\*，類型 = win32 '  
 當您嘗試發行已啟用視覺樣式的 WPF 應用程式時，會出現此錯誤訊息。 若要解決此問題，請參閱[如何：發行已啟用視覺化樣式的 WPF 應用程式](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)。  
  
## <a name="using-mage"></a>使用 Mage  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>您嘗試使用憑證存放區中的憑證，以及收到的空白訊息方塊來簽署  
 在 [**簽署**] 對話方塊中，您必須：  
  
- 選取 [**使用預存憑證簽署**]，然後  
  
- 從清單中選取憑證;第一個憑證不是預設的選取專案。  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>按一下 [不要簽署] 按鈕會造成例外狀況  
 此問題是已知的錯誤。 所有 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 資訊清單都必須經過簽署。 只要選取其中一個簽署選項，然後按一下 **[確定]** 。  
  
## <a name="additional-errors"></a>其他錯誤  
 下表顯示當使用者安裝 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式時，用戶端電腦的使用者可能會收到的一些常見錯誤訊息。 每個錯誤訊息都會列在錯誤最可能原因的描述旁邊。  
  
|錯誤訊息|描述|  
|-------------------|-----------------|  
|無法啟動應用程式。 請聯絡應用程式發行者。<br /><br /> 無法啟動應用程式。 請洽詢應用程式廠商以尋求協助。|這些是在無法啟動應用程式時所發生的一般錯誤訊息，而且找不到其他特定原因。 通常這表示應用程式有某種程度的損毀，或 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 存放區已損毀。|  
|無法繼續。 應用程式的格式不正確。 請洽詢應用程式發行者以取得協助。<br /><br /> 應用程式驗證失敗。 無法繼續。<br /><br /> 無法取出應用程式檔。 部署中的檔案已損毀。|部署中的其中一個資訊清單檔案語法不正確，或包含無法與對應檔案協調的雜湊。 此錯誤也可能表示內嵌在元件中的資訊清單已損毀。 重新建立您的部署並重新編譯應用程式，或在資訊清單中手動尋找並修正錯誤。|  
|無法取得應用程式。 驗證錯誤。<br /><br /> 應用程式安裝失敗。 找不到伺服器上的應用程式檔。 請洽詢應用程式發行者或您的系統管理員以取得協助。|無法下載部署中的一個或多個檔案，因為您沒有存取這些檔案的許可權。 這可能是因為 Web 服務器傳回403禁止的錯誤所造成，如果您部署中的其中一個檔案結尾的延伸模組，使 Web 服務器將其視為受保護的檔案，可能會發生這種情況。 此外，包含一或多個應用程式檔案的目錄，可能需要使用者名稱和密碼才能存取。|  
|無法下載應用程式。 應用程式缺少必要的檔案。 請洽詢應用程式廠商或您的系統管理員以取得協助。|在伺服器上找不到應用程式資訊清單中列出的一或多個檔案。 請確認您已上傳所有部署的相依檔案，然後再試一次。|  
|應用程式下載未成功。 檢查您的網路連線，或洽詢您的系統管理員或網路服務提供者。|[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 無法建立與伺服器的網路連接。 檢查伺服器的可用性和網路的狀態。|  
|URLDownloadToCacheFile 失敗，HRESULT 為 '\<數位 > '。 嘗試下載 '\<file > ' 時發生錯誤。|如果使用者已將部署目的電腦上的 [Internet Explorer Advanced Security] 選項設為 [在安全和不安全模式之間變更]，而且要安裝之 ClickOnce 應用程式的安裝 URL 從不安全重新導向至安全的網站（或相反地，安裝將會失敗，因為 Internet Explorer 警告會中斷其連接。<br /><br /> 若要解決這個問題，您可以執行下列其中一項動作：<br /><br /> -清除 [安全性] 選項。<br />-請確定安裝程式 URL 不會以變更安全性模式的方式重新導向。<br />-完全移除重新導向，並指向實際的安裝 URL。|  
|寫入硬碟時發生錯誤。 磁片上可能沒有足夠的可用空間。 請洽詢應用程式廠商或您的系統管理員以取得協助。|這可能表示儲存應用程式的磁碟空間不足，但是當您嘗試將應用程式檔儲存到磁片磁碟機時，也可能表示發生較一般的 i/o 錯誤。|  
|無法啟動應用程式。 磁片上的可用空間不足。|硬碟已滿。 請清除空間，然後再次嘗試執行應用程式。|  
|太多部署的啟用同時嘗試載入。|[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 限制可以同時啟動的不同應用程式數目。 這主要是為了協助防止惡意嘗試對本機 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 服務 instigate 阻絕服務攻擊;嘗試重複啟動相同應用程式的使用者，很快就會得到應用程式的單一實例。|  
|無法透過網路啟用快捷方式。|只能在本機硬碟上啟動 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式的快捷方式。 您無法開啟指向遠端伺服器上快捷方式檔案的 URL 來啟動它們。|  
|應用程式太大，無法在部分信任的線上執行。 請洽詢應用程式廠商或您的系統管理員以取得協助。|在部分信任中執行的應用程式不能大於線上應用程式配額大小的一半，預設為 250 MB。|  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [疑難排解 ClickOnce 部署](../deployment/troubleshooting-clickonce-deployments.md)
