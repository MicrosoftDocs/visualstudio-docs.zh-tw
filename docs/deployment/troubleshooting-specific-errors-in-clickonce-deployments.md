---
title: "疑難排解 ClickOnce 部署中的特定錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 40c679811f137e77909395042d91d0458c874d90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="troubleshooting-specific-errors-in-clickonce-deployments"></a>疑難排解 ClickOnce 部署的特定錯誤
本主題列出當您部署時，可能會發生下列常見錯誤[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式，並提供解決每個問題的步驟。  
  
## <a name="general-errors"></a>一般錯誤  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>當您嘗試尋找.application 檔案，會發生任何狀況，或 XML 呈現在 Internet Explorer 中，或您收到執行] 或 [另存新檔對話方塊  
 內容型別 （也稱為 MIME 類型） 的伺服器或用戶端上未正確登錄，可能被造成這個錯誤。  
  
 首先，請確定伺服器已設定為將.application 副檔名做為與內容類型 」 / x ms 應用"產生關聯。  
  
 如果伺服器設定正確，請確認[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]安裝在電腦上。 如果[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]安裝時，您仍發現這個問題，請再試一次解除安裝再重新安裝和[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]重新註冊用戶端上的內容類型。  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>錯誤訊息指出，「 無法擷取應用程式。 在部署中遺失的檔案 」 或 「 下載應用程式已中斷，請檢查網路錯誤並再試一次 」  
 此訊息會指出所參考的一個或多個檔案[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]無法下載資訊清單。 若要偵錯這個錯誤最簡單的方式是嘗試下載 URL，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]指出它無法下載。 以下是一些可能的原因：  
  
-   如果記錄檔會顯示 「 (403) 禁止 」 或"(404) 找不到 」 可讓您確認網頁伺服器已設定，讓它不會封鎖下載這個檔案。 如需詳細資訊，請參閱 [ClickOnce 部署中的伺服器和用戶端組態問題](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)。  
  
-   如果伺服器正在封鎖的.config 檔案，請參閱 > 一節 「 下載錯誤，當您嘗試安裝[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]具有.config 檔案的應用程式 「 本主題稍後。  
  
-   判斷是否發生這種因為`deploymentProvider`部署資訊清單中的 URL 指向不同位置，用來啟動的 URL。  
  
-   請確認所有檔案都都出現在伺服器上;[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]記錄應該會告訴您找不到的檔案。  
  
-   查看是否有網路連線問題。如果您的用戶端電腦在下載期間已經離線，您可以收到此訊息。  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>當您嘗試安裝 ClickOnce 應用程式具有.config 檔案下載時發生錯誤  
 根據預設，Visual Basic Windows 為基礎的應用程式會包含一個 App.config 檔案。 當使用者嘗試從使用 Windows Server 2003 的網頁伺服器安裝，因為該作業系統會封鎖安裝的.config 檔案，基於安全性理由，將會是問題。 若要啟用的.config 檔案，以安裝，請按一下**使用".deploy"副檔名**中**發行選項** 對話方塊。  
  
 您也必須設定內容類型 （也稱為 MIME 類型） 適當地.application、.manifest，和.deploy 檔案。 如需詳細資訊，請參閱您的 Web 伺服器文件。  
  
 如需詳細資訊，請參閱 < Windows Server 2003:: 之一內容類型 」[伺服器和 ClickOnce 部署中的用戶端組態問題](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)。  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>錯誤訊息: 「 應用程式格式不正確。 」記錄檔包含 「 XML 簽章無效 」  
 請確定您已更新資訊清單檔案，並重新簽署它。 重新發行應用程式使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]或使用 Mage 簽署該應用程式。  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>您已更新您的應用程式在伺服器上，但用戶端不會下載更新  
 藉由完成下列工作之一，就可能會解決這個問題：  
  
-   檢查`deploymentProvider`部署資訊清單中的 URL。 請確定您要更新的相同位置中的位元的`deploymentProvider`指向。  
  
-   確認部署資訊清單中的更新間隔。 如果在此時間間隔設定為定期間隔，例如一次每隔六小時，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]不會掃描更新之前已超過此時間間隔。 您可以變更要掃描更新每次應用程式啟動時的資訊清單。 變更更新間隔是開發期間驗證正在安裝更新，但它會降低應用程式啟用的方便選項。  
  
-   請嘗試再次啟動應用程式，在 [開始] 功能表上。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]可能已在背景中偵測更新，但將會提示您先安裝 bits，在下一步 啟動。  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>更新期間，您收到錯誤，有下列記錄項目: 「 部署中的參考與應用程式資訊清單中所定義的識別不相符 」  
 因為您已經手動編輯部署和應用程式資訊清單中，有一個變得與其他同步處理的資訊清單中會導致身分識別的組件的描述，可能會發生這個錯誤。 組件的識別是由其名稱、 版本、 文化特性和公開金鑰語彙基元所組成。 檢查身分識別中的說明資訊清單，並更正任何差異。  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>第一次從本機磁碟或 CD-ROM 啟動成功，但後續從 [開始] 功能表啟動不成功  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]您可以使用部署提供者 URL 來接收應用程式的更新。 請確認 URL 所指向的位置正確。  
  
#### <a name="error-cannot-start-the-application"></a>錯誤: 「 無法啟動應用程式 」  
 此錯誤訊息通常表示已安裝到此應用程式的問題[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]儲存。 請在應用程式有錯誤或存放區已損毀。 記錄檔可能會告訴您哪裡發生錯誤。  
  
 您應該執行下列作業：  
  
-   確認部署資訊清單識別、 應用程式資訊清單，識別和身分識別的主要應用程式執行檔都具有唯一性。  
  
-   請確認您的檔案路徑沒有超過 100 個字元。 如果您的應用程式包含檔案路徑太長，可能會超過您可以儲存最大路徑限制。 請嘗試縮短路徑，然後重新安裝。  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>Bin 應用程式組態檔的設定不會生效  
 若要使用 Bin （Fusion 探查路徑），應用程式必須要求完全信任權限。 請嘗試變更應用程式資訊清單，以要求完全信任，並再試一次。  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>解除安裝期間出現，指出 「 無法解除安裝應用程式 」  
 此訊息通常表示已移除該應用程式，或在存放區已損毀。 按一下 之後**確定**、**新增或移除程式**將移除項目。  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>在安裝期間，會顯示訊息表示沒有安裝的平台相依性  
 遺漏的必要條件，才能執行的應用程式必須在 GAC （全域組件快取） 中。  
  
## <a name="publishing-with-visual-studio"></a>使用 Visual Studio 發行  
  
#### <a name="publishing-in-visual-studio-fails"></a>在 Visual Studio 中的發佈失敗  
 確定您已發行至伺服器的權限所設定的目標。 例如，如果您登入終端機伺服器的電腦，以一般使用者，不是身為管理員，您可能不會發行至本機 Web 伺服器所需的權限。  
  
 如果您要發行的 url，請確定目標電腦已啟用 FrontPage Server Extensions。  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>錯誤訊息： 無法建立網站 '\<站台 >'。 不會安裝的 FrontPage Server extensions 通訊的元件。  
 確定您有 Microsoft Visual Studio 撰寫安裝 Web 元件，您從發行的機器上。 Express 使用者預設不會安裝此元件。 如需詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310)。  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>錯誤訊息： 找不到檔案 ' Microsoft.Windows.Common-控制項，Version = 6.0.0.0，文化特性 = *，PublicKeyToken = 6595b64144ccf1df，ProcessorArchitecture =\*，類型 = win32'  
 當您嘗試發佈已啟用視覺化樣式的 WPF 應用程式時，就會出現此錯誤訊息。 若要解決此問題，請參閱[如何： 發行與已啟用視覺化樣式的 WPF 應用程式](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)。  
  
## <a name="using-mage"></a>使用 Mage  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>您嘗試使用您的憑證存放區和收到空白訊息方塊中的憑證，簽署  
 在**簽署**對話方塊中，您必須：  
  
-   選取**預存憑證以簽署**，和  
  
-   從清單中選取的憑證第一份憑證不是預設選項。  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>按一下 [不要簽署] 按鈕會發生例外狀況  
 這個問題是已知的錯誤。 所有[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]資訊清單都必須經過簽署。 只要選取其中一個簽章的選項，然後**確定**。  
  
## <a name="additional-errors"></a>其他錯誤  
 下表顯示一些常見的錯誤訊息，使用者安裝時，用戶端電腦使用者可能會收到[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。 每個錯誤訊息列旁邊的最可能的錯誤的原因描述。  
  
|錯誤訊息|描述|  
|-------------------|-----------------|  
|無法啟動應用程式。 請連絡應用程式發行者。<br /><br /> 無法啟動應用程式。 請連絡應用程式廠商尋求協助。|這些是無法啟動應用程式，並可以找到其他特定原因時發生一般錯誤訊息。 通常這表示，應用程式由於某種原因而損毀，或[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]存放區已損毀。|  
|無法繼續。 應用程式的格式不正確。 請連絡應用程式發行者以尋求協助。<br /><br /> 應用程式驗證失敗。 無法繼續。<br /><br /> 無法擷取應用程式檔案。 在部署中的檔案損毀。|其中一個部署中的資訊清單檔案的語法無效，或包含不能和對應檔案一致的雜湊。 此錯誤也可能表示內嵌於組件資訊清單已損毀。 重新建立您的部署和重新編譯您的應用程式，或尋找並修正錯誤手動資訊清單中。|  
|無法擷取應用程式。 驗證錯誤。<br /><br /> 應用程式安裝失敗。 找不到應用程式伺服器上的檔案。 如需協助，請連絡應用程式發行者或您的系統管理員。|無法下載部署中的一個或多個檔案，因為您沒有存取權限。 這可能被因所傳回的網頁伺服器，如果您的部署中的檔案的其中一個 Web 伺服器視為受保護的檔案副檔名，可能會發生 403 禁止錯誤。 此外，包含一或多個應用程式的檔案的目錄，可能會需要使用者名稱和密碼才能存取。|  
|無法下載應用程式。 應用程式缺少必要的檔案。 如需協助，請連絡應用程式廠商或您的系統管理員。|在伺服器上找不到一或多個應用程式資訊清單中列出的檔案。 請確認您已上傳的所有部署的相依檔案，並再試一次。|  
|應用程式下載失敗。 檢查網路連線，或連絡您的系統管理員或網路服務提供者。|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]無法建立網路連線到伺服器。 請檢查伺服器的可用性，以及您網路的狀態。|  
|URLDownloadToCacheFile 失敗，HRESULT '\<編號 >'。 嘗試下載時，發生錯誤 '\<檔案 >'。|如果使用者已設定 Internet Explorer 進階安全性選項 「 安全之間切換時，即發出警告和不安全模式 」 的部署目標電腦上，而且安裝程式的 URL 所安裝的 ClickOnce 應用程式從非安全重新導向至安全網站 （或反之亦然），安裝會失敗，因為 Internet Explorer 警告中斷它。<br /><br /> 若要解決此問題，您可以執行下列其中一項：<br /><br /> -清除安全性選項。<br />-請確定安裝程式 URL 不會重新導向的方式，以變更安全性模式。<br />-完全移除的重新導向，並指向實際的安裝程式的 URL。|  
|寫入硬碟時發生錯誤。 可能沒有足夠的空間可用磁碟上。 如需協助，請連絡應用程式廠商或您的系統管理員。|這可能足夠的磁碟空間來儲存應用程式，但它也可能表示更一般的 I/O 錯誤，當您嘗試將應用程式檔案儲存到磁碟機。|  
|無法啟動應用程式。 在磁碟上沒有足夠的可用空間。|硬碟已滿。 請釋放空間，然後嘗試再次執行應用程式。|  
|太多已部署的啟用嘗試載入一次。|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]限制可以同時啟動的不同應用程式數目。 這主要是為了有效抵禦惡意嘗試發動阻絕服務攻擊本機[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]服務; 嘗試快速而連續重複啟動相同的應用程式，將只的單一執行個體的使用者應用程式。|  
|無法透過網路啟動捷徑。|捷徑[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]只在本機硬碟上啟動應用程式。 無法啟動這類開啟指向遠端伺服器上的捷徑檔案的 URL。|  
|應用程式太大而無法在線上，在部分信任中執行。 如需協助，請連絡應用程式廠商或您的系統管理員。|在部分信任中執行的應用程式不能大於線上應用程式的配額，其預設值為 250 MB 大小的一半。|  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [疑難排解 ClickOnce 部署](../deployment/troubleshooting-clickonce-deployments.md)