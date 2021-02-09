---
title: '針對 ClickOnce 部署 (的錯誤進行疑難排解) '
description: 本文描述當您部署 ClickOnce 應用程式時可能發生的常見錯誤，並提供解決每個問題的步驟。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4697aa4869535d63c522ae25c978dd89bfe51697
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876169"
---
# <a name="troubleshoot-specific-errors-in-clickonce-deployments"></a>針對 ClickOnce 部署的特定錯誤進行疑難排解
本文列出當您部署應用程式時可能會發生的下列常見錯誤 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ，並提供解決每個問題的步驟。

## <a name="general-errors"></a>一般錯誤

#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>當您嘗試找出應用程式檔時，不會發生任何事，或 XML 會在 Internet Explorer 中轉譯，或是您會收到 [執行] 或 [另存新檔] 對話方塊
 此錯誤可能是因為內容類型 (也稱為 MIME 類型，) 未在伺服器或用戶端上正確註冊。

 首先，請確定已將伺服器設定為將 *. 應用程式* 延伸模組與內容類型 "application/x-ms-application" 產生關聯。

 如果伺服器設定正確，請檢查電腦上是否已安裝 .NET Framework 2.0。 如果 .NET Framework 2.0 已安裝，但您仍遇到此問題，請嘗試卸載並重新安裝 .NET Framework 2.0，以在用戶端上重新註冊內容類型。

#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>錯誤訊息指出「無法取出應用程式。 部署中缺少檔案」或「應用程式下載已中斷，請檢查網路錯誤並稍後再試一次」
 此訊息表示 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 無法下載資訊清單所參考的一或多個檔案。 若要偵測此錯誤，最簡單的方法是嘗試下載 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 指出無法下載的 URL。 以下是一些可能的原因：

- 如果記錄檔顯示「 (403) 禁止」或「 (404) 找不到」，請確認網頁伺服器已設定，使其不會封鎖此檔案的下載。 如需詳細資訊，請參閱 [ClickOnce 部署中的伺服器和用戶端組態問題](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)。

- 如果伺服器正在封鎖 *.config* 檔案，請參閱本文稍後的「當您嘗試安裝具有 .config 檔案的應用程式時下載錯誤」一節 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。

- 判斷是否發生此錯誤，因為 `deploymentProvider` 部署資訊清單中的 url 指向的位置，與用於啟用的 url 不同。

- 確定所有檔案都存在於伺服器上; [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 記錄檔應該會告訴您找不到哪個檔案。

- 查看是否有網路連線問題;如果用戶端電腦在下載期間離線，您就可以收到此訊息。

#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>當您嘗試安裝具有 .config 檔案的 ClickOnce 應用程式時，下載錯誤
 根據預設，Visual Basic Windows 型應用程式包含 App.config 檔案。 當使用者嘗試從使用 Windows Server 2003 的 Web 服務器安裝時，將會發生問題，因為作業系統會基於安全性理由封鎖 *.config* 檔案的安裝。 若要啟用要安裝的 *.config* 檔案，請按一下 [**發行選項**] 對話方塊中的 **[使用 "deploy" 副檔名**]。

 您也必須將內容類型 (也稱為 MIME 類型) 適當地針對. 應用程式、資訊清單和. 部署檔案。 如需詳細資訊，請參閱您的網頁伺服器檔。

 如需詳細資訊，請參閱 [ClickOnce 部署中的伺服器和用戶端設定問題](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)中的「Windows Server 2003：鎖定的內容類型」。

#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>錯誤訊息：「應用程式格式不正確;」記錄檔包含 "XML signature 無效"
 請確定您已更新資訊清單檔案，然後再次簽署。 使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 或使用 Mage 重新簽署應用程式，重新發佈您的應用程式。

#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>您已在伺服器上更新您的應用程式，但用戶端不會下載更新。
 您可以完成下列其中一項工作來解決此問題：

- 檢查 `deploymentProvider` 部署資訊清單中的 URL。 確定您要更新的位位在指向的相同位置 `deploymentProvider` 。

- 確認部署資訊清單中的更新間隔。 如果此間隔設定為定期間隔，例如每六個小時一次，則在達到 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 此間隔之前，將不會掃描更新。 您可以變更資訊清單，以在每次應用程式啟動時掃描更新。 在開發期間變更更新間隔是很方便的選項，以確認是否已安裝更新，但它會減緩應用程式啟用。

- 請嘗試在 [開始] 功能表上再次啟動應用程式。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 可能已在背景中偵測到更新，但會提示您在下一次啟用時安裝 bits。

#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>在更新期間，您會收到具有下列記錄專案的錯誤：「部署中的參考與應用程式資訊清單中定義的身分識別不相符」
 發生此錯誤的原因可能是您已手動編輯部署和應用程式資訊清單，並導致某個資訊清單中元件的身分識別描述與另一個資訊清單不同步。 元件的身分識別是由其名稱、版本、文化特性和公開金鑰 token 所組成。 檢查資訊清單中的身分識別描述，並修正任何差異。

#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>第一次從本機磁片或 CD-ROM 啟用時，會成功，但後續從 [開始] 功能表啟用則不會成功
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用部署提供者 URL 來接收應用程式的更新。 確認 URL 指向的位置正確無誤。

#### <a name="error-cannot-start-the-application"></a>錯誤：「無法啟動應用程式」
 此錯誤訊息通常表示在存放區中安裝此應用程式時發生問題 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 可能是應用程式發生錯誤或存放區已損毀。 記錄檔可能會告訴您發生錯誤的位置。

 您應該執行下列作業：

- 確認部署資訊清單的身分識別、應用程式資訊清單的身分識別，以及主要應用程式 EXE 的身分識別都是唯一的。

- 確認您的檔案路徑不超過100個字元。 如果您的應用程式包含的檔案路徑太長，您可能會超過可以儲存的最大路徑限制。 請嘗試縮短路徑並重新安裝。

#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>不接受應用程式佈建檔中的 PrivatePath 設定
 若要使用 PrivatePath (融合探查路徑) ，應用程式必須要求完全信任許可權。 請嘗試變更應用程式資訊清單以要求完全信任，然後再試一次。

#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>在卸載期間，訊息會顯示「無法卸載應用程式」
 此訊息通常表示應用程式已被移除，或存放區已損毀。 按一下 **[確定]** 之後，將會移除 [ **新增/移除程式** ] 專案。

#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>在安裝期間，會出現一則訊息，指出未安裝平臺相依性。
 您在 GAC 中缺少必要元件 (全域組件快取) 應用程式需要該應用程式才能執行。

## <a name="publishing-with-visual-studio"></a>使用 Visual Studio 發行

#### <a name="publishing-in-visual-studio-fails"></a>Visual Studio 中的發佈失敗
 確定您有權發行至您的目標伺服器。 比方說，如果您是以一般使用者的身分登入終端機伺服器電腦，而不是以系統管理員身分登入，您可能就不需要發佈到本機 Web 服務器的許可權。

 如果您要使用 URL 發佈，請確定目的地電腦已啟用 FrontPage Server Extensions。

#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>錯誤訊息：無法建立網站 ' ' \<site> 。 未安裝與 FrontPage Server Extensions 進行通訊的元件。
 確定您已在要發行的電腦上安裝 Microsoft Visual Studio Web Authoring Component。 若為 Express 使用者，預設不會安裝此元件。 如需詳細資訊，請參閱 [http://go.microsoft.com/fwlink/?LinkId=102310](https://support.microsoft.com/help/945358)。

#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>錯誤訊息：找不到檔案 ' Microsoft. Common Controls，Version = 6.0.0.0，Culture = *，PublicKeyToken = 6595b64144ccf1df，ProcessorArchitecture = \* ，Type = win32 '
 當您嘗試發行已啟用視覺化樣式的 WPF 應用程式時，會出現此錯誤訊息。 若要解決此問題，請參閱 [如何：發行已啟用視覺化樣式的 WPF 應用程式](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)。

## <a name="using-mage"></a>使用 Mage

#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>您嘗試使用憑證存放區中的憑證和收到的空白訊息方塊來簽署
 在 [ **簽署** ] 對話方塊中，您必須：

- 選取 [ **使用預存憑證簽署**]，然後

- 從清單中選取憑證;第一個憑證不是預設選項。

#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>按一下 [不要簽署] 按鈕會造成例外狀況
 此問題是已知的 bug。 所有 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 資訊清單都需要簽署。 只需選取其中一個簽署選項，然後按一下 **[確定]**。

## <a name="additional-errors"></a>其他錯誤
 下表顯示當使用者安裝應用程式時，用戶端電腦使用者可能會收到的一些常見錯誤訊息 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 錯誤的最可能原因描述旁邊會列出每個錯誤訊息。

| 錯誤訊息 | Description |
| - | - |
| 無法啟動應用程式。 聯繫應用程式發行者。<br /><br /> 無法啟動應用程式。 洽詢應用程式廠商以取得協助。 | 這些是當應用程式無法啟動時所發生的一般錯誤訊息，而且找不到其他特定的原因。 這通常表示應用程式已損毀，或 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 存放區已損毀。 |
| 無法繼續。 應用程式的格式不正確。 請洽詢應用程式發行者以取得協助。<br /><br /> 應用程式驗證失敗。 無法繼續。<br /><br /> 無法取出應用程式檔。 部署中的檔案已損毀。 | 部署中的其中一個資訊清單檔案的語法無效，或包含無法與對應檔案協調的雜湊。 這項錯誤也可能表示內嵌在元件中的資訊清單已損毀。 重新建立您的部署並重新編譯您的應用程式，或在資訊清單中手動尋找並修正錯誤。 |
| 無法取出應用程式。 驗證錯誤。<br /><br /> 應用程式安裝失敗。 找不到伺服器上的應用程式檔。 洽詢應用程式發行者或您的系統管理員以取得協助。 | 無法下載部署中的一或多個檔案，因為您沒有存取這些檔案的許可權。 這可能是 Web 服務器傳回403禁止的錯誤所致，如果您部署中的其中一個檔案的結尾是讓 Web 服務器將它視為受保護的檔案，則可能會發生這種錯誤。 此外，包含一或多個應用程式檔的目錄可能需要使用者名稱和密碼才能存取。 |
| 無法下載應用程式。 應用程式遺失必要的檔案。 洽詢應用程式廠商或您的系統管理員以取得協助。 | 在伺服器上找不到應用程式資訊清單中所列的一或多個檔案。 請確認您已上傳所有部署的相依檔案，然後再試一次。 |
| 應用程式下載失敗。 檢查您的網路連線，或洽詢您的系統管理員或網路服務提供者。 | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 無法建立與伺服器的網路連接。 檢查伺服器的可用性和您網路的狀態。 |
| URLDownloadToCacheFile 失敗，HRESULT 為 ' \<number> '。 嘗試下載 ' ' 時發生錯誤 \<file> 。 | 如果使用者已在部署目的電腦上設定 [如果在安全和不安全模式之間變更時警告] Internet Explorer Advanced 安全性選項，且正在安裝之 ClickOnce 應用程式的安裝 URL 會從不安全的重新導向至安全的網站 (或反之亦然) ，則安裝將會失敗，因為 Internet Explorer 警告會將它中斷。<br /><br /> 若要解決這個錯誤，您可以執行下列其中一項工作：<br /><br /> -清除安全性選項。<br />-請確定安裝程式 URL 不會以變更安全性模式的方式重新導向。<br />-完全移除重新導向，並指向實際的安裝程式 URL。 |
| 寫入硬碟時發生錯誤。 磁片上的可用空間可能不足。 洽詢應用程式廠商或您的系統管理員以取得協助。 | 這可能表示用來儲存應用程式的磁碟空間不足，但是當您嘗試將應用程式檔儲存到磁片磁碟機時，也可能會指出更一般的 i/o 錯誤。 |
| 無法啟動應用程式。 磁片上的可用空間不足。 | 硬碟已滿。 清除空格鍵，然後再次嘗試執行應用程式。 |
| 太多部署的啟用嘗試一次載入。 | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 限制可以同時啟動的不同應用程式數目。 這主要是為了協助防止惡意嘗試對本機服務 instigate 阻斷服務攻擊 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ; 嘗試重複啟動相同應用程式的使用者，很快就會得到單一的應用程式實例。 |
| 無法透過網路啟用快速鍵。 | 應用程式的快捷方式 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 只能在本機硬碟上啟動。 您無法藉由開啟指向遠端伺服器上快捷方式檔案的 URL 來啟動它們。 |
| 應用程式太大，無法在線上以部分信任方式執行。 洽詢應用程式廠商或您的系統管理員以取得協助。 | 在部分信任中執行的應用程式不能大於線上應用程式配額的一半，預設為 250 MB。 |

## <a name="see-also"></a>另請參閱
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
- [針對 ClickOnce 部署進行疑難排解](../deployment/troubleshooting-clickonce-deployments.md)
- [Visual Studio 疑難排解](/troubleshoot/visualstudio/welcome-visual-studio/)