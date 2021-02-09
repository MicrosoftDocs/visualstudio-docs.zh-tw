---
title: ClickOnce 安全性和部署 |Microsoft Docs
description: 瞭解 ClickOnce 的 Visual Studio 支援，這是一種部署技術，可讓您建立自行更新的 Windows 應用程式。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8bb0bdeae09f22a2b45e3029fbc9097c00911d2a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930014"
---
# <a name="clickonce-security-and-deployment"></a>ClickOnce 安全性和部署
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 是一種部署技術，可讓您建立自行更新的 Windows 應用程式，這些應用程式可以使用極短的使用者互動來安裝和執行。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 如果您已經使用 Visual Basic 和 Visual c # 開發您的專案，則可使用 ClickOnce 技術來發行和更新部署的應用程式的完整支援。 如需部署 Visual C++ 應用程式的詳細資訊，請參閱 [Visual C++ 應用程式的 ClickOnce 部署](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)。

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署克服了部署中的三個主要問題：

- **更新應用程式的困難。** 使用 Microsoft Windows Installer 部署時，每當應用程式更新時，使用者都可以安裝更新、msp 檔案，並將其套用至已安裝的產品;使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署時，您可以自動提供更新。 只有已變更的應用程式部分會下載，然後從新的並列資料夾重新安裝完整的更新應用程式。

- **對使用者電腦的影響。** 使用 Windows Installer 部署時，應用程式通常依賴共用元件，可能會有版本控制衝突;使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署時，每個應用程式都是獨立的，而且不會干擾其他應用程式。

- **安全性許可權。** Windows Installer 部署需要系統管理許可權，而且只允許受限的使用者安裝; [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署可讓非系統管理使用者安裝並只授與應用程式所需的代碼啟用安全性許可權。

  在過去，這些問題有時候會導致開發人員決定要建立 Web 應用程式，而不是以 Windows 為基礎的應用程式，因而犧牲了豐富的使用者介面，方便您安裝。 藉由使用部署的應用程式 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ，您可以使用這兩種技術的最佳做法。

## <a name="what-is-a-clickonce-application"></a>什麼是 ClickOnce 應用程式？
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式是任何 Windows Presentation Foundation (*xbap*) 、Windows Forms (*.exe*) 、主控台應用程式 (*.exe*) 或 Office 方案 (*.dll*) 使用技術發佈。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 您可以使用三種不同的方式來發佈 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式：從網頁、從網路檔案共用，或從 cd-rom 等媒體進行。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式可以安裝在終端使用者的電腦上並在本機執行，即使是在電腦離線的情況下，也可以在線上模式中執行，而不需要在終端使用者的電腦上永久安裝任何資訊。 如需詳細資訊，請參閱 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式可以自行更新;他們可以檢查是否有較新版本可供使用，並自動取代任何更新的檔案。 開發人員可以指定更新行為；網路系統管理員也可以控制更新策略，例如將更新標記為強制性。 使用者或系統管理員也可以將更新回復為先前的版本。 如需詳細資訊，請參閱 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。

 因為 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式是獨立的，所以安裝或執行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式無法中斷現有的應用程式。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式是獨立的;每個 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式都安裝在安全的每個使用者、每個應用程式的快取中，並執行。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式會在網際網路或內部網路安全性區域中執行。 如有需要，應用程式可以要求提高安全性權限。 如需詳細資訊，請參閱 [安全的 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。

## <a name="how-clickonce-security-works"></a>ClickOnce 安全性的運作方式
 核心 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 安全性是以憑證、代碼啟用安全性原則和 ClickOnce 信任提示為基礎。

### <a name="certificates"></a>憑證
 Authenticode 憑證可用來驗證應用程式發行者的真實性。 藉由使用 Authenticode 進行應用程式部署，ClickOnce 有助於防止有害的程式從拿本身成為來自可靠來源的合法程式。 您也可以選擇使用憑證來簽署應用程式和部署資訊清單，以證明檔案未遭篡改。 如需詳細資訊，請參閱 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)。 憑證也可以用來將用戶端電腦設定為具有信任的發行者清單。 如果應用程式來自信任的發行者，則可以在不需要任何使用者互動的情況下進行安裝。 如需詳細資訊，請參閱 [受信任的應用程式部署總覽](../deployment/trusted-application-deployment-overview.md)。

### <a name="code-access-security"></a>程式碼存取安全性
 代碼啟用安全性有助於限制程式碼對受保護資源的存取權。 在大多數情況下，您可以選擇 [網際網路] 或 [近端內部網路] 區域來限制許可權。 使用 **ProjectDesigner** 中的 [**安全性**] 頁面，要求應用程式所需的區域。 您也可以使用限制許可權來偵測應用程式，以模擬終端使用者體驗。 如需詳細資訊，請參閱 [ClickOnce 應用程式的代碼啟用安全性](../deployment/code-access-security-for-clickonce-applications.md)。

### <a name="clickonce-trust-prompt"></a>ClickOnce 信任提示
 如果應用程式要求的許可權超過區域允許的許可權，系統就會提示使用者進行信任決策。 終端使用者可以決定是否要執行 ClickOnce 應用程式，例如 Windows Forms 應用程式、Windows Presentation Foundation 應用程式、主控台應用程式、XAML 瀏覽器應用程式和 Office 方案。 如需詳細資訊，請參閱 [如何：設定 ClickOnce 信任提示行為](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)。

## <a name="how-clickonce-deployment-works"></a>ClickOnce 部署的運作方式
 核心 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署架構是以兩個 XML 資訊清單檔案為基礎：應用程式資訊清單和部署資訊清單。 這些檔案會用來描述 ClickOnce 應用程式的安裝位置、更新的方式，以及更新的時機。

### <a name="publish-clickonce-applications"></a>發佈 ClickOnce 應用程式
 應用程式資訊清單會描述應用程式本身。 這包括構成應用程式的元件、相依性和檔案、必要的許可權，以及可用的更新位置。 應用程式開發人員會使用 Visual Studio 中的 [發佈嚮導]，或中的資訊清單產生和編輯工具 (*Mage.exe*) ，來撰寫應用程式資訊清單 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] 。 如需詳細資訊，請參閱 [如何：使用發佈嚮導發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。

 部署資訊清單會描述應用程式的部署方式。 這包括應用程式資訊清單的位置，以及用戶端應該執行的應用程式版本。

### <a name="deploy-clickonce-applications"></a>部署 ClickOnce 應用程式
 部署資訊清單在建立之後會複製到部署位置。 這可能是 Web 伺服器、網路檔案共用或 CD 之類的媒體。 應用程式資訊清單和所有應用程式檔也會複製到部署資訊清單中指定的部署位置。 這個位置可能與部署位置相同，也可能是不同的位置。 使用 Visual Studio 中的 [ **發佈嚮導]** 時，會自動執行複製作業。

### <a name="install-clickonce-applications"></a>安裝 ClickOnce 應用程式
 在應用程式部署到部署位置之後，終端使用者可以在網頁上或資料夾中按一下代表部署資訊清單檔案的圖示，來下載和安裝應用程式。 在大部分的情況下，終端使用者會看到一個簡單的對話方塊，要求使用者確認安裝，之後安裝會繼續，且應用程式會在不需要額外介入的情況下啟動。 如果應用程式需要較高的許可權，或如果應用程式不是由受信任的憑證簽署，對話方塊也會要求使用者授與許可權，才能繼續安裝。 雖然 ClickOnce 安裝是每位使用者，但如果有需要系統管理員許可權的必要條件，則可能需要許可權提升許可權。 如需更高許可權的詳細資訊，請參閱 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。

 憑證可以在電腦或企業層級信任，因此以受信任憑證簽署的 ClickOnce 應用程式可以無訊息地安裝。 如需有關受信任憑證的詳細資訊，請參閱 [信任的應用程式部署總覽](../deployment/trusted-application-deployment-overview.md)。

 您可以將應用程式新增至使用者的 [**開始**] 功能表，以及 **主控台** 中的 [**新增或移除程式**] 群組。 與其他部署技術不同的是，不會將任何專案新增至 **Program Files** 資料夾或登錄，且不需要系統管理許可權即可安裝

> [!NOTE]
> 您也可以防止將應用程式新增至 [ **開始** ] 功能表和 [ **新增或移除程式** ] 群組，實際上它的行為就像 Web 應用程式一樣。 如需詳細資訊，請參閱 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。

### <a name="update-clickonce-applications"></a>更新 ClickOnce 應用程式
 當應用程式開發人員建立應用程式的更新版本時，會產生新的應用程式資訊清單，並將檔案複製到部署位置（通常是原始應用程式部署資料夾的同級資料夾）。 系統管理員會更新部署資訊清單，以指向應用程式新版本的位置。

> [!NOTE]
> Visual Studio 中的 [ **發佈嚮導]** 可以用來執行這些步驟。

 除了部署位置外，部署資訊清單也包含更新位置 (網頁或網路檔案共用)，應用程式會在該位置檢查更新的版本。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]**發佈** 屬性可用來指定應用程式檢查更新的時間和頻率。 您可以在部署資訊清單中指定更新行為，也可以透過 api 在應用程式的使用者介面中顯示為使用者選擇 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 此外，也可以運用 [Publish] (發佈) 屬性將更新設為強制性，或復原為較舊版本。 如需詳細資訊，請參閱 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。

### <a name="third-party-installers"></a>協力廠商安裝程式
 您可以自訂 ClickOnce 安裝程式，以安裝協力廠商元件和您的應用程式。 您必須將可轉散發套件 ( .exe 或 .msi 檔案) ，並使用語言中性的產品資訊清單和特定語言的套件資訊清單來描述套件。 如需詳細資訊，請參閱建立啟動載入器 [套件](../deployment/creating-bootstrapper-packages.md)。

## <a name="clickonce-tools"></a>ClickOnce 工具
 下表顯示您可以用來產生、編輯、簽署和重新簽署應用程式和部署資訊清單的工具。

|工具|描述|
|----------|-----------------|
|[專案設計工具、安全性頁](../ide/reference/security-page-project-designer.md)|簽署應用程式和部署資訊清單。|
|[專案設計工具、發行頁](../ide/reference/publish-page-project-designer.md)|產生和編輯 Visual Basic 和 Visual c # 應用程式的應用程式和部署資訊清單。|
|[*Mage.exe* (資訊清單產生和編輯工具)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|針對 Visual Basic、Visual c # 和 Visual C++ 應用程式產生應用程式和部署資訊清單。<br /><br /> 簽署並重新簽署應用程式和部署資訊清單。<br /><br /> 可以從批次腳本和命令提示字元執行。|
|[*MageUI.exe* (資訊清單產生和編輯工具、圖形用戶端)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|產生和編輯應用程式和部署資訊清單。<br /><br /> 簽署並重新簽署應用程式和部署資訊清單。|
|[GenerateApplicationManifest 工作](../msbuild/generateapplicationmanifest-task.md)|產生應用程式資訊清單。<br /><br /> 可以從 MSBuild 執行。 如需詳細資訊，請參閱 [MSBuild 參考](../msbuild/msbuild-reference.md)。|
|[GenerateDeploymentManifest 工作](../msbuild/generatedeploymentmanifest-task.md)|產生部署資訊清單。<br /><br /> 可以從 MSBuild 執行。 如需詳細資訊，請參閱 [MSBuild 參考](../msbuild/msbuild-reference.md)。|
|[SignFile 工作](../msbuild/signfile-task.md)|簽署應用程式和部署資訊清單。<br /><br /> 可以從 MSBuild 執行。 如需詳細資訊，請參閱 [MSBuild 參考](../msbuild/msbuild-reference.md)。|
|[Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/microsoft.build.tasks.deployment.manifestutilities)|開發您自己的應用程式，以產生應用程式和部署資訊清單。|

 下表顯示在這些瀏覽器中支援 ClickOnce 應用程式所需的 .NET Framework 版本。

|瀏覽器|.NET Framework 版本|
|-------------|----------------------------|
|Internet Explorer|2.0、3.0、3.5、3.5 SP1、4|
|Firefox|2.0 SP1、3.5 SP1、4|
|Chrome|3.5|
|Microsoft Edge|3.5|

## <a name="see-also"></a>另請參閱
- [Windows Vista 的 ClickOnce 部署](../deployment/clickonce-deployment-on-windows-vista.md)
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)
- [使用 ClickOnce 部署 COM 元件](../deployment/deploying-com-components-with-clickonce.md)
- [從命令列建置 ClickOnce 應用程式](../deployment/building-clickonce-applications-from-the-command-line.md)
- [使用 System. Deployment 的 Debug ClickOnce 應用程式](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
