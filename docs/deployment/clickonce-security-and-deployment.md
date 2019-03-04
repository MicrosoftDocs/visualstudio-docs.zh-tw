---
title: ClickOnce 安全性和部署 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29659af4fa05c6556656a0a11f13377119f9df9e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56612903"
---
# <a name="clickonce-security-and-deployment"></a>ClickOnce 安全性和部署
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 是一種部署技術，可讓您建立自行更新以 Windows 為基礎的應用程式可以安裝並執行最少使用者介入。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 提供完整的支援發佈及更新應用程式部署與 ClickOnce 技術，如果您在開發您的專案與 Visual Basic 和 Visual C#。 部署 Visual c + + 應用程式的相關資訊，請參閱[Visual c + + 應用程式的 ClickOnce 部署](/cpp/ide/clickonce-deployment-for-visual-cpp-applications)。

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署可克服在部署中的三個主要問題：

- **更新應用程式的困難。** 使用 Microsoft Windows Installer 部署時，只要更新應用程式，使用者可以安裝更新，msp 檔案，並將它套用到已安裝的產品;使用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署，您可以自動提供更新。 下載的只有這些組件的應用程式已變更，並完整、 已更新的應用程式然後重新安裝新的並排顯示資料夾中。

- **若要在使用者電腦的影響。** 使用 Windows Installer 部署時，應用程式經常依賴共用元件，可能發生版本衝突;使用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署中，每個應用程式是獨立的並不會干擾其他應用程式。

- **安全性權限。** Windows Installer 部署需要系統管理權限，且允許只有有限的使用者安裝;[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署啟用非系統管理員的使用者安裝，並授與應用程式所需的程式碼存取安全性使用權。

  在過去，這些問題有時會導致開發人員決定建立 Web 應用程式，而不是以 Windows 為基礎的應用程式，犧牲豐富的使用者介面，以簡化安裝。 使用應用程式部署使用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]，您可以有最佳的這兩種技術。

## <a name="what-is-a-clickonce-application"></a>什麼是 ClickOnce 應用程式？
 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式是任何 Windows Presentation Foundation (*.xbap*)，Windows Form (*.exe*)、 主控台應用程式 (*.exe*)，或 Office 方案 (*.dll*) 使用發行[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]技術。 您可以發佈[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式的方式有三種： 從網頁、 網路檔案共用，或媒體例如 CD-ROM。 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式可以安裝在終端使用者的電腦上和在本機執行，即使電腦處於離線狀態，或可以在僅限線上模式中執行而不需要永久終端使用者的電腦上安裝任何項目。 如需詳細資訊，請參閱 <<c0> [ 選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式可以自行更新;它們可以檢查較新版本，因為它們變成可用，而且會自動取代任何更新的檔案。 開發人員可以指定更新行為；網路系統管理員也可以控制更新策略，例如將更新標記為強制性。 更新可以也會回復為舊版由使用者或系統管理員。 如需詳細資訊，請參閱 <<c0> [ 選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。

 因為[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式是隔離的安裝或執行[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式不會中斷現有應用程式。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式是獨立的;每個[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式已安裝且執行從安全的個別使用者，每個應用程式快取。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 在網際網路或內部網路安全性區域中，執行應用程式。 如有需要，應用程式可以要求提高安全性權限。 如需詳細資訊，請參閱 <<c0> [ 保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。

## <a name="how-clickonce-security-works"></a>ClickOnce 安全性的運作方式
 核心[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]安全性根據憑證、 程式碼存取安全性原則和 ClickOnce 信任提示。

### <a name="certificates"></a>憑證
 Authenticode 憑證用來驗證的應用程式發行者真偽。 藉由使用 Authenticode 部署應用程式，ClickOnce 會有助於防止有害的程式本身公家來自於已建立、 可信任來源的合法程式。 或者，也可以使用憑證簽署應用程式和部署資訊清單，以證明檔案未已遭竄改。 如需詳細資訊，請參閱 < [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)。 憑證也可用來設定用戶端電腦有一份受信任的發行者。 如果應用程式來自受信任的發行者，則它可以安裝沒有任何使用者互動。 如需詳細資訊，請參閱[受信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)。

### <a name="code-access-security"></a>程式碼存取安全性
 程式碼存取安全性有助於限制程式碼對受保護資源的存取權。 在大部分情況下，您可以選擇的網際網路或近端內部網路區域，以限制權限。 使用**安全性**頁面**ProjectDesigner**要求適用於應用程式的區域。 您也可以偵錯應用程式，以限制權限來模擬的使用者體驗。 如需詳細資訊，請參閱 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)。

### <a name="clickonce-trust-prompt"></a>ClickOnce 信任提示
 如果應用程式要求更多的權限超過允許的區域，您就可以提示使用者進行信任決策。 使用者可以決定是否受信任而得以執行 ClickOnce 應用程式，例如 Windows Forms 應用程式、 Windows Presentation Foundation 應用程式、 主控台應用程式、 XAML 瀏覽器應用程式，以及 Office 方案。 如需詳細資訊，請參閱 <<c0> [ 如何： 設定 ClickOnce 信任提示行為](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)。

## <a name="how-clickonce-deployment-works"></a>ClickOnce 部署的運作方式
 核心[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署架構根據兩個 XML 資訊清單檔案： 應用程式資訊清單和部署資訊清單。 檔案用來描述從 ClickOnce 應用程式的安裝位置，更新方式和更新的時機。

### <a name="publish-clickonce-applications"></a>發佈 ClickOnce 應用程式
 應用程式資訊清單描述應用程式本身。 這包括組件、 相依性和構成應用程式、 必要的權限，以及位置會提供更新的檔案。 應用程式開發人員使用發行精靈，在 Visual Studio 或資訊清單產生和編輯工具來撰寫應用程式資訊清單 (*Mage.exe*) 中[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]。 如需詳細資訊，請參閱 <<c0> [ 如何： 發行 ClickOnce 應用程式使用發行精靈](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。

 部署資訊清單會描述應用程式的部署方式。 這包括應用程式資訊清單的位置以及用戶端應該執行的應用程式的版本。

### <a name="deploy-clickonce-applications"></a>部署 ClickOnce 應用程式
 部署資訊清單在建立之後會複製到部署位置。 這可能是 Web 伺服器、網路檔案共用或 CD 之類的媒體。 應用程式資訊清單和應用程式的所有檔案也會複製到部署資訊清單中指定的部署位置中。 這個位置可能與部署位置相同，也可能是不同的位置。 使用時**發行精靈**在 Visual Studio 中，複製作業會自動執行。

### <a name="install-clickonce-applications"></a>安裝 ClickOnce 應用程式
 在應用程式部署到部署位置之後，終端使用者可以在網頁上或資料夾中按一下代表部署資訊清單檔案的圖示，來下載和安裝應用程式。 在大部分情況下，使用者會使用簡單的對話方塊，詢問使用者要確認安裝之後安裝會繼續，而不需要其他介入的情況下啟動應用程式。 在應用程式需要提高權限的權限，或如果應用程式並非由受信任的憑證簽署的位置的情況下，對話方塊也會要求使用者授與權限，才能繼續安裝。 雖然 ClickOnce 安裝，而且每個使用者，權限提高權限可能需要有需要系統管理員權限的必要條件。 如需提高權限的詳細資訊，請參閱[保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。

 憑證可以是受信任電腦或企業層級，以便以受信任的憑證簽署的 ClickOnce 應用程式可以進行無訊息安裝。 如需有關受信任憑證的詳細資訊，請參閱[信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)。

 應用程式可以新增至使用者的**開始** 功能表並**新增或移除程式**群組中**控制台**。 不同於其他部署技術，不會加入至**Program Files**資料夾或登錄和無系統管理權限所需的安裝

> [!NOTE]
>  它也可防止應用程式新增至**開始**功能表並**新增或移除程式** 群組，實際上讓它像 Web 應用程式的行為。 如需詳細資訊，請參閱 <<c0> [ 選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。

### <a name="update-clickonce-applications"></a>更新 ClickOnce 應用程式
 當應用程式開發人員建立應用程式的更新的版本時，它們產生新的應用程式資訊清單，並將檔案複製到部署位置 — 通常是原始的應用程式部署資料夾的同層級資料夾。 系統管理員會更新部署資訊清單，以指向應用程式新版本的位置。

> [!NOTE]
>  **發行精靈**Visual Studio 中可以用來執行這些步驟。

 除了部署位置外，部署資訊清單也包含更新位置 (網頁或網路檔案共用)，應用程式會在該位置檢查更新的版本。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] **發行**屬性用來指定時間和頻率的應用程式應該檢查更新。 部署資訊清單中，可以指定更新行為，或它可以呈現為藉由應用程式的使用者介面中的使用者選項[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Api。 此外，也可以運用 [Publish] (發佈) 屬性將更新設為強制性，或復原為較舊版本。 如需詳細資訊，請參閱[選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。

### <a name="third-party-installers"></a>協力廠商安裝程式
 您可以自訂您要安裝第三方元件，以及您的應用程式的 ClickOnce 安裝程式。 您必須擁有可轉散發套件 （.exe 或.msi 檔案），並且描述使用非語言相關產品資訊清單和特定語言的封裝資訊清單套件。 如需詳細資訊，請參閱 <<c0> [ 建立啟動載入器套件](../deployment/creating-bootstrapper-packages.md)。

## <a name="clickonce-tools"></a>ClickOnce tools
 下表顯示的工具，可用來產生、 編輯、 登入，並重新簽署應用程式和部署資訊清單。

|工具|說明|
|----------|-----------------|
|[專案設計工具、安全性頁面](../ide/reference/security-page-project-designer.md)|簽署的應用程式和部署資訊清單。|
|[專案設計工具、發行頁面](../ide/reference/publish-page-project-designer.md)|產生和編輯 Visual Basic 和 Visual 的應用程式和部署資訊清單C#應用程式。|
|[*Mage.exe* (資訊清單產生和編輯工具)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|產生 Visual basic 中，視覺效果的應用程式和部署資訊清單C#，和 Visual c + + 應用程式。<br /><br /> 簽署並重新簽署應用程式和部署資訊清單。<br /><br /> 可以從批次指令碼和命令提示字元中執行。|
|[*MageUI.exe* (資訊清單產生和編輯工具，圖形化用戶端)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|產生和編輯應用程式和部署資訊清單。<br /><br /> 簽署並重新簽署應用程式和部署資訊清單。|
|[GenerateApplicationManifest 工作](../msbuild/generateapplicationmanifest-task.md)|產生應用程式資訊清單。<br /><br /> 從執行 MSBuild。 如需詳細資訊，請參閱 [MSBuild 參考](../msbuild/msbuild-reference.md)。|
|[GenerateDeploymentManifest 工作](../msbuild/generatedeploymentmanifest-task.md)|產生部署資訊清單。<br /><br /> 從執行 MSBuild。 如需詳細資訊，請參閱 [MSBuild 參考](../msbuild/msbuild-reference.md)。|
|[SignFile 工作](../msbuild/signfile-task.md)|簽署的應用程式和部署資訊清單。<br /><br /> 從執行 MSBuild。 如需詳細資訊，請參閱 [MSBuild 參考](../msbuild/msbuild-reference.md)。|
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|開發您自己的應用程式，以產生應用程式和部署資訊清單。|

 下表顯示支援這些瀏覽器中的 ClickOnce 應用程式所需的.NET Framework 版本。

|瀏覽器|.NET Framework 版本|
|-------------|----------------------------|
|Internet Explorer|2.0、3.0、3.5、3.5 SP1、4|
|Firefox|2.0 SP1、3.5 SP1、4|

## <a name="see-also"></a>另請參閱
- [ClickOnce deployment on Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md) (Windows Vista 的 ClickOnce 部署)
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)
- [Deploy COM components with ClickOnce](../deployment/deploying-com-components-with-clickonce.md) (使用 ClickOnce 部署 COM 元件)
- [Build ClickOnce applications from the command line](../deployment/building-clickonce-applications-from-the-command-line.md) (從命令列建置 ClickOnce 應用程式)
- [對使用 System.Deployment.Application 的 ClickOnce 應用程式進行偵錯](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
