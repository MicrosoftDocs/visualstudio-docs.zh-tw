---
title: 疑難排解 ClickOnce 部署中的特定錯誤 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2d337a1ed97524dc04c8154fe2b074baf0921ca
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042377"
---
# <a name="troubleshoot-specific-errors-in-clickonce-deployments"></a>針對 ClickOnce 部署的特定錯誤進行疑難排解
本文列出當您在部署時，可能會發生下列常見的錯誤[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式，並提供解決每個問題的步驟。

## <a name="general-errors"></a>一般錯誤

#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>當您嘗試找出應用程式檔，好像沒有發生，或在 Internet Explorer 中的 XML 呈現或您收到 [執行] 或 [另存新檔] 對話方塊
 此錯誤可能被因伺服器或用戶端上未正確登錄的內容類型 （也稱為 MIME 類型）。

 首先，請確定伺服器設定為產生關聯 *.application*內容類型 」 / x ms-應用程式。 」

 如果伺服器已正確設定，請確認[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]安裝在您的電腦上。 如果[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]安裝時，您仍發現此問題，請解除安裝再重新安裝和[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]重新註冊用戶端上的內容類型。

#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>錯誤訊息指出，「 無法擷取應用程式。 在部署中遺失的檔案 」 或 「 已中斷下載應用程式、 檢查是否有網路錯誤稍後再試一 」
 此訊息表示所參考的一或多個檔案[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]無法下載資訊清單。 偵錯此錯誤的最簡單方式是嘗試將下載的 URL，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]說它無法下載。 以下是一些可能的原因：

- 如果記錄檔會說 「 (403) 禁止 」 或"(404) 找不到，「 驗證設定 Web 伺服器，這樣不會封鎖下載這個檔案。 如需詳細資訊，請參閱 [ClickOnce 部署中的伺服器和用戶端組態問題](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)。

- 如果 *.config*伺服器正在封鎖的檔案，請參閱區段 」 下載錯誤，當您嘗試安裝[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].config 檔案的應用程式 「 本文稍後的。

- 判斷是否發生此錯誤，因為`deploymentProvider`部署資訊清單中的 URL 指向不同的位置，用來啟動的 URL。

- 請確定所有檔案都都存在於伺服器上[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]記錄應該會告訴您找不到的檔案。

- 查看是否有網路連線問題;如果您的用戶端電腦在下載期間已離線，您就可以接收此訊息。

#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>當您嘗試安裝 ClickOnce 應用程式的.config 檔案下載錯誤
 根據預設，Visual Basic Windows 為基礎的應用程式會包含 App.config 檔案。 會有問題的使用者嘗試安裝從使用 Windows Server 2003，Web 伺服器，因為該作業系統會封鎖安裝時 *.config*基於安全性考量的檔案。 若要啟用 *.config*檔案安裝，請按一下 [**使用".deploy"副檔名**中**發行選項**] 對話方塊。

 您也必須設定內容類型 （也稱為 MIME 類型） 適當.application、.manifest，和.deploy 檔案。 如需詳細資訊，請參閱您的 Web 伺服器文件。

 如需詳細資訊，請參閱 「 Windows Server 2003:鎖定的內容類型 」 [ClickOnce 部署中的伺服器和用戶端組態問題](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)。

#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>錯誤訊息：「 應用程式格式不正確。 」記錄檔包含 「 XML 簽章無效 」
 請確定您已更新資訊清單檔案，並重新簽署它。 重新發佈應用程式使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]或使用 Mage 簽署應用程式一次。

#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>您已更新您的應用程式的伺服器上，但用戶端不會下載更新
 藉由完成下列工作之一，可能會解決此問題：

- 檢查`deploymentProvider`部署資訊清單中的 URL。 請確定您要更新的相同位置中的位元，`deploymentProvider`指向。

- 確認部署資訊清單中的更新間隔。 如果這個間隔設定為定期間隔，例如每隔六個小時，一次[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]會掃描更新，直到已超過此時間間隔。 您可以變更要掃描每次應用程式啟動時已更新的資訊清單。 變更的更新間隔是方便的選項，在開發期間若要確認安裝更新之後，但應用程式啟動會變慢。

- 請嘗試再次啟動應用程式，在 [開始] 功能表上。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 可能已在背景中，偵測更新，但會提示您安裝位元上的下一步 啟動。

#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>在更新期間，您會收到錯誤，有下列記錄項目：「 在部署中的參考不符合應用程式清單中所定義的身分識別 」
 因為您已經手動編輯部署和應用程式資訊清單中，而導致的組件的識別描述其變得與其他同步處理的一個資訊清單中，可能會發生此錯誤。 組件的識別是由其名稱、 版本、 文化特性和公開金鑰 token 所組成。 檢查您的資訊清單中的識別描述，並更正任何差異。

#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>第一次從本機磁碟或光碟片啟動成功，但後續從 [開始] 功能表啟動不成功
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 您可以使用部署提供者 URL，接收應用程式的更新。 請確認 URL 所指向的位置正確無誤。

#### <a name="error-cannot-start-the-application"></a>錯誤：[無法啟動應用程式]
 此錯誤訊息通常表示沒有安裝此應用程式時遇到問題[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]儲存。 應用程式有錯誤或存放區已損毀。 記錄檔可能會告訴您哪裡發生錯誤。

 您應該執行下列作業：

- 確認部署資訊清單的身分識別、 應用程式資訊清單中，身分識別和身分識別的主應用程式 EXE 都具有唯一性。

- 請確認您的檔案路徑沒有超過 100 個字元。 如果您的應用程式包含檔案路徑太長，您可能會超過您可以將儲存的最大路徑限制。 請嘗試縮短路徑並重新安裝。

#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>不會遵守 Bin 的應用程式組態檔中的設定
 若要使用 Bin （Fusion 探查路徑），應用程式必須要求完全信任權限。 請嘗試變更應用程式資訊清單，來要求完全信任，並再試一次。

#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>解除安裝期間出現，指出 「 無法解除安裝應用程式 」
 此訊息通常表示應用程式可能已經移除，或在存放區已損毀。 按一下 之後**確定**，則**新增/移除程式**將移除項目。

#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>在安裝期間，會出現訊息指出未安裝的平台相依性
 您沒有在 GAC （全域組件快取） 的應用程式執行時所需的必要條件。

## <a name="publishing-with-visual-studio"></a>使用 Visual Studio 的發行

#### <a name="publishing-in-visual-studio-fails"></a>在 Visual Studio 中的發行會失敗
 確定您已發行至伺服器的權限，您的目標。 比方說，如果您登入的終端機伺服器電腦，身為一般使用者，不是身為管理員，您可能不會發行至本機 Web 伺服器所需的權限。

 如果您要發行的 url，請確定目的地電腦已啟用 FrontPage Server Extensions。

#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>錯誤訊息：無法建立網站 '\<網站 >'。 使用 FrontPage Server Extensions 通訊的元件不會安裝。
 請確定您有 Microsoft Visual Studio 撰寫安裝 Web 元件，您從發行的機器上。 Express 使用者，預設不會安裝此元件。 如需詳細資訊，請參閱 [http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310)。

#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>錯誤訊息：Could not find file 'Microsoft.Windows.Common-Controls, Version=6.0.0.0, Culture=*, PublicKeyToken=6595b64144ccf1df, ProcessorArchitecture=\*, Type=win32'
 當您嘗試發行已啟用視覺化樣式的 WPF 應用程式時，就會出現此錯誤訊息。 若要解決此問題，請參閱[How to:發行啟用視覺化樣式的 WPF 應用程式](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)。

## <a name="using-mage"></a>使用影像

#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>您嘗試使用您的憑證存放區和收到空白的訊息方塊中的憑證簽署
 在 [**簽署**] 對話方塊中，您必須：

- 選取 **預存憑證以簽署**，及

- 從清單中選取憑證第一個憑證不是預設選項。

#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>按一下 「 不登 」 按鈕，會導致例外狀況
 這個問題是已知的 bug。 所有[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]資訊清單是必須簽署。 只選取其中一個的簽章的選項，然後按一下**確定**。

## <a name="additional-errors"></a>其他錯誤
 下表顯示一些常見的錯誤訊息，當使用者安裝，用戶端電腦使用者可能會收到[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。 每個錯誤訊息會列出最可能的錯誤的原因的描述旁邊。

| 錯誤訊息 | 描述 |
| - | - |
| 無法啟動應用程式。 請連絡應用程式發行者。<br /><br /> 無法啟動應用程式。 請連絡應用程式廠商尋求協助。 | 這些是無法啟動應用程式，而且可以找到其他特定原因時，會發生的一般錯誤訊息。 通常這表示，應用程式以某種方式損毀，或[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]存放區已損毀。 |
| 無法繼續。 應用程式的格式不正確。 請連絡應用程式發行者尋求協助。<br /><br /> 應用程式驗證失敗。 無法繼續。<br /><br /> 無法擷取應用程式檔案。 在部署中的檔案損毀。 | 其中一個部署中的資訊清單檔案的語法無效，或包含無法對應的檔案和一致的雜湊。 這項錯誤也可能表示資訊清單內嵌在組件已損毀。 重新建立您的部署和重新編譯您的應用程式，或尋找及修正錯誤以手動方式在您的資訊清單中。 |
| 無法擷取應用程式。 驗證錯誤。<br /><br /> 應用程式安裝失敗。 找不到檔案伺服器上的應用程式。 請連絡應用程式發行者或您的系統管理員尋求協助。 | 無法下載部署中的一個或多個檔案，因為您沒有存取權限。 這可能被因 403 禁止錯誤所傳回的 Web 伺服器，如果其中一個部署中的檔案結尾的擴充功能會讓 Web 伺服器視為受保護的檔案，可能會發生。 此外，此目錄包含一或多個應用程式的檔案可能需要使用者名稱和密碼才能存取。 |
| 無法下載應用程式。 應用程式缺少必要的檔案。 請連絡應用程式廠商或您的系統管理員尋求協助。 | 在伺服器上找不到一或多個應用程式資訊清單中列出的檔案。 請檢查您已上傳了部署的所有相依檔案，並再試一次。 |
| 下載應用程式失敗。 檢查您的網路連線，或連絡系統管理員或網路服務提供者。 | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 無法建立網路連線到伺服器。 檢查伺服器的可用性和網路的狀態。 |
| URLDownloadToCacheFile 失敗，HRESULT '\<編號 >'。 嘗試下載時，發生錯誤 '\<檔案 >'。 | 如果使用者已設定 Internet Explorer 進階安全性選項 「 安全之間切換時，即發出警告和不安全模式 」 的部署目標電腦上，而且安裝 ClickOnce 應用程式的安裝程式 URL 從非安全重新導向至安全的站台 （或反之亦然），安裝會失敗，因為 Internet Explorer 警告中斷它。<br /><br /> 若要解決這個錯誤，您可以執行下列工作之一：<br /><br /> -清除安全性選項。<br />-請確定安裝程式的 URL 不會重新導向的方式，以變更安全性模式。<br />-完全移除的重新導向，並指向實際的安裝程式的 URL。 |
| 寫入硬碟時，已發生錯誤。 可能會有足夠的空間可用磁碟上。 請連絡應用程式廠商或您的系統管理員尋求協助。 | 這可能表示沒有足夠的磁碟空間來儲存應用程式，但它也可能表示更一般的 I/O 錯誤，當您嘗試將應用程式檔案儲存到磁碟機。 |
| 無法啟動應用程式。 在磁碟上沒有足夠的可用空間。 | 硬碟已滿。 清除空間，然後再次嘗試再次執行應用程式。 |
| 太多的部署的啟用嘗試載入一次。 | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 限制可以同時啟動的不同應用程式數目。 這主要是要協助防範惡意嘗試發動阻絕服務攻擊本機[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]服務; 嘗試快速且連續地重複，啟動相同的應用程式，將只得到的單一執行個體的使用者應用程式。 |
| 無法透過網路啟動的捷徑。 | 捷徑[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]只在本機硬碟上啟動應用程式。 他們無法啟動開啟的 URL，指向遠端伺服器上的捷徑檔案。 |
| 應用程式太大而無法在線上在部分信任中執行。 請連絡應用程式廠商或您的系統管理員尋求協助。 | 在部分信任中執行的應用程式不能大於一半的線上應用程式的配額，其預設值為 250 MB 的大小。 |

## <a name="see-also"></a>另請參閱
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
- [針對 ClickOnce 部署進行疑難排解](../deployment/troubleshooting-clickonce-deployments.md)