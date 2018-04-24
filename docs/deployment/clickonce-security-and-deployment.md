---
title: ClickOnce 安全性和部署 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ec2e74623c39640517ae73786d7865143bf1505
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="clickonce-security-and-deployment"></a>ClickOnce 安全性和部署
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 是一種部署技術，可讓您建立自我更新 Windows 為基礎的應用程式可以安裝並執行最少的使用者互動。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 用於發佈及更新部署與 ClickOnce 技術，如果您已經開發您的專案與 Visual Basic 和 Visual C# 應用程式提供完整支援。 部署 Visual c + + 應用程式的相關資訊，請參閱[Visual c + + 應用程式的 ClickOnce 部署](/cpp/ide/clickonce-deployment-for-visual-cpp-applications)。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署克服部署中的三個主要問題：  
  
-   **更新應用程式的問題。** 使用 Microsoft Windows Installer 部署時，每當更新應用程式時，使用者可以安裝更新，msp 檔案，並將它套用到已安裝的產品。與[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署中，您可以自動提供更新。 只有應用程式部分已變更被下載，和完整、 更新應用程式然後重新安裝新的並行的資料夾。  
  
-   **若要在使用者電腦的影響。** 使用 Windows Installer 部署時，應用程式通常會仰賴共用元件，而且可能會針對版本控制衝突。與[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署中，每個應用程式為獨立，而且不會干擾其他應用程式。  
  
-   **安全性權限。** Windows Installer 部署需要系統管理權限，並允許只受限制的使用者安裝。[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署可讓非系統管理使用者安裝，並且授與必要應用程式的程式碼存取安全性使用權。  
  
 在過去，這些問題有時會造成開發人員決定要建立 Web 應用程式，而不是 Windows 架構應用程式，犧牲簡易安裝的豐富使用者介面。 使用應用程式部署使用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]，您可以讓最棒的是這兩種技術。  
  
## <a name="what-is-a-clickonce-application"></a>什麼是 ClickOnce 應用程式？  
 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式是任何 Windows Presentation Foundation (.xbap)、 Windows Form (.exe)、 主控台應用程式 (.exe) 或使用發行 Office 方案 (.dll)[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]技術。 您可以發佈[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式的三種不同的方式： 從網頁上、 網路檔案共用，或媒體例如 CD-ROM。 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式可以安裝在終端使用者電腦上，並在本機執行，即使電腦已離線，或可以在僅限線上模式中執行而不需要永久終端使用者電腦上安裝任何項目。 如需詳細資訊，請參閱[選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式可以自行更新。它們可以檢查可用並自動取代任何更新的檔案的較新版本。 開發人員可以指定更新的行為;網路系統管理員也可以控制更新策略，例如，標示為必要的更新。 更新可以也會回復至舊版的終端使用者或系統管理員。 如需詳細資訊，請參閱[選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
 因為[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式都已隔離，安裝或執行[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式不能破壞現有的應用程式。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式各自獨立。每個[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式會安裝並執行從安全每位使用者，每個應用程式快取。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 在網際網路或內部網路安全性區域中，執行應用程式。 必要時，應用程式可以要求提高權限的安全性權限。 如需詳細資訊，請參閱[保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。  
  
## <a name="how-clickonce-security-works"></a>ClickOnce 安全性的運作方式  
 核心[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]安全性根據憑證、 程式碼存取安全性原則和 ClickOnce 信任提示。  
  
### <a name="certificates"></a>憑證  
 Authenticode 憑證可用來驗證應用程式的發行者。 藉由使用 Authenticode 以部署應用程式，ClickOnce 會有助於防止有害的程式合法程式來自已建立、 值得信任的來源方法本身。 或者，也可以使用憑證簽署應用程式和部署資訊清單，以證明檔案未已遭竄改。 如需詳細資訊，請參閱[ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)。 憑證也可用來設定用戶端電腦具有受信任的發行者清單。 如果應用程式來自受信任的發行者，則它可以安裝沒有任何使用者互動。 如需詳細資訊，請參閱 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。  
  
### <a name="code-access-security"></a>程式碼存取安全性  
 程式碼存取安全性有助於限制程式碼對受保護資源的存取。 在大部分情況下，您可以選擇網際網路或近端內部網路區域以限制權限。 使用**安全性**頁面**ProjectDesigner**來要求適當的應用程式的區域。 您也可以偵錯應用程式，以限制使用權限來模擬的使用者體驗。 如需詳細資訊，請參閱 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)。  
  
### <a name="clickonce-trust-prompt"></a>ClickOnce 信任提示  
 如果應用程式要求超過區域可讓更多的權限，可以提示使用者進行信任決策。 使用者可以決定是否受信任而得以執行 ClickOnce 應用程式，例如 Windows Forms 應用程式、 Windows Presentation Foundation 應用程式、 主控台應用程式、 XAML 瀏覽器應用程式和 Office 方案。 如需詳細資訊，請參閱[How to： 設定 ClickOnce 信任提示行為](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)。  
  
## <a name="how-clickonce-deployment-works"></a>ClickOnce 部署的運作方式  
 核心[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署架構根據兩個 XML 資訊清單檔案： 應用程式資訊清單和部署資訊清單。 檔案會用來描述 ClickOnce 應用程式的安裝位置，更新方式與更新時。  
  
### <a name="publishing-clickonce-applications"></a>發行 ClickOnce 應用程式  
 應用程式資訊清單會描述應用程式本身。 這包括組件的相依性和構成應用程式、 必要的權限，以及位置會提供更新的檔案。 應用程式開發人員撰寫使用 Visual Studio 或資訊清單產生和編輯工具 (Mage.exe) 中的 [發行精靈] 中的應用程式資訊清單[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]。 如需詳細資訊，請參閱[如何： 發行 ClickOnce 應用程式使用發行精靈](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
 部署資訊清單會描述如何部署應用程式。 這包括應用程式資訊清單的位置以及用戶端應該要執行的應用程式的版本。  
  
### <a name="deploying-clickonce-applications"></a>部署 ClickOnce 應用程式  
 它建立之後，部署資訊清單會複製到部署位置。 這可以是 Web 伺服器、 網路檔案共用或媒體例如 CD。 應用程式資訊清單和應用程式的所有檔案也會複製到部署資訊清單中指定的部署位置。 這可以是部署位置，與相同或不同的位置。 當使用**發行精靈**在 Visual Studio 中，複製作業會自動執行。  
  
### <a name="installing-clickonce-applications"></a>安裝 ClickOnce 應用程式  
 部署至部署位置之後，使用者就可以下載並安裝應用程式，按一下圖示代表在網頁上或資料夾中的部署資訊清單檔案。 在大部分情況下，使用者會與簡單的對話方塊，詢問使用者確定安裝，安裝會繼續而不需要其他介入啟動應用程式。 在應用程式需要提高權限，或如果應用程式並非由受信任的憑證簽署的情況下，對話方塊也會要求使用者授與權限，才能繼續安裝。 雖然 ClickOnce 安裝，而且每個使用者，提高權限可能需要是否有需要系統管理員權限的必要條件。 如需更高權限的詳細資訊，請參閱[保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。  
  
 憑證可以是受信任電腦或企業層級，以便以受信任的憑證簽署的 ClickOnce 應用程式可以進行無訊息安裝。 如需受信任憑證的詳細資訊，請參閱[受信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)。  
  
 應用程式可以加入至使用者的**啟動**功能表和**新增或移除程式**群組**控制台**。 不同於其他部署技術，不會加入**Program Files**資料夾或登錄中，然後無系統管理權限所需的安裝  
  
> [!NOTE]
>  它也可防止應用程式新增至**啟動**功能表和**新增或移除程式**群組，實際上將它的行為就像 Web 應用程式。 如需詳細資訊，請參閱[選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。  
  
### <a name="updating-clickonce-applications"></a>更新 ClickOnce 應用程式  
 當應用程式開發人員建立應用程式的更新的版本時，它們產生新的應用程式資訊清單，並將檔案複製到部署位置 — 通常是原始的應用程式部署資料夾的同層級資料夾。 系統管理員更新部署資訊清單，以指向新版本的應用程式的位置。  
  
> [!NOTE]
>  **發行精靈**Visual Studio 中可以用來執行這些步驟。  
  
 部署位置中，除了部署資訊清單也包含其中應用程式會檢查有更新版本的更新位置 （Web 網頁或網路檔案共用）。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] **發行**屬性用來指定時間和頻率應用程式應該檢查更新。 部署資訊清單中，可以指定更新行為，或藉由應用程式的使用者介面中的使用者選項做[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式開發介面。 此外，**發行**可以採用屬性，讓更新成為強制或回復為舊版。 如需詳細資訊，請參閱[選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
### <a name="third-party-installers"></a>第三方廠商安裝程式  
 您可以自訂您要安裝協力廠商元件，以及您的應用程式的 ClickOnce 安裝程式。 您必須有可轉散發套件 （.exe 或.msi 檔案），並描述具有非語言相關產品資訊清單和的特定語言套件資訊清單的封裝。 如需詳細資訊，請參閱[建立啟動載入器套件](../deployment/creating-bootstrapper-packages.md)。  
  
## <a name="clickonce-tools"></a>ClickOnce 工具  
 下表顯示的工具，您可以使用產生、 編輯、 簽署，並重新簽署應用程式和部署資訊清單。  
  
|工具|描述|  
|----------|-----------------|  
|[專案設計工具、安全性頁面](../ide/reference/security-page-project-designer.md)|簽署的應用程式和部署資訊清單。|  
|[專案設計工具、發行頁面](../ide/reference/publish-page-project-designer.md)|產生和編輯 Visual Basic 和 Visual C# 應用程式的應用程式和部署資訊清單。|  
|[Mage.exe (資訊清單產生和編輯工具)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|產生 Visual Basic、 Visual C# 和 Visual c + + 應用程式的應用程式和部署資訊清單。<br /><br /> 簽署並重新簽署應用程式和部署資訊清單。<br /><br /> 可以從批次指令碼及命令提示字元中執行。|  
|[MageUI.exe (圖形用戶端、資訊清單產生和編輯工具)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|產生和編輯應用程式和部署資訊清單。<br /><br /> 簽署並重新簽署應用程式和部署資訊清單。|  
|[GenerateApplicationManifest 工作](../msbuild/generateapplicationmanifest-task.md)|產生應用程式資訊清單。<br /><br /> 可以執行從 MSBuild。 如需詳細資訊，請參閱[MSBuild 參考](../msbuild/msbuild-reference.md)。|  
|[GenerateDeploymentManifest 工作](../msbuild/generatedeploymentmanifest-task.md)|產生的部署資訊清單。<br /><br /> 可以執行從 MSBuild。 如需詳細資訊，請參閱[MSBuild 參考](../msbuild/msbuild-reference.md)。|  
|[SignFile 工作](../msbuild/signfile-task.md)|簽署的應用程式和部署資訊清單。<br /><br /> 可以執行從 MSBuild。 如需詳細資訊，請參閱[MSBuild 參考](../msbuild/msbuild-reference.md)。|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|開發您自己的應用程式，以產生應用程式和部署資訊清單。|  
  
 下表顯示支援這些瀏覽器中的 ClickOnce 應用程式所需的.NET Framework 版本。  
  
|瀏覽器|.NET Framework 版本|  
|-------------|----------------------------|  
|Internet Explorer|2.0、 3.0、 3.5、 3.5 SP1、 4|  
|Firefox|2.0 SP1、 3.5 SP1、 4|  
  
## <a name="see-also"></a>另請參閱  
 [Windows Vista 的 ClickOnce 部署](../deployment/clickonce-deployment-on-windows-vista.md)   
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [使用 ClickOnce 部署 COM 元件](../deployment/deploying-com-components-with-clickonce.md)   
 [從命令列建置 ClickOnce 應用程式](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [偵錯使用 System.Deployment.Application 的 ClickOnce 應用程式](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)