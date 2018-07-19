---
title: 發行 ClickOnce 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Options
- Microsoft.VisualStudio.Publish.ClickOnceProvider.PublishWizard.Help
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- ClickOnce applications, publishing
- applications [Visual Studio], ClickOnce deployment
- deploying applications [ClickOnce], publishing ClickOnce applications
ms.assetid: eb6dfe79-f54c-4331-8e36-073688e70973
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0c6f931af213ff7ce97ec77c2b742d6767cf733
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079242"
---
# <a name="publish-clickonce-applications"></a>發行 ClickOnce 應用程式
首次發行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，可以使用 [發行精靈] 來設定發行屬性。 這個精靈僅提供少數屬性；所有其他屬性都設為其預設值。  
  
 若要將內容發佈的後續變更會對**發佈**頁面**專案設計工具**。  
  
## <a name="publish-wizard"></a>發行精靈  
 您可以使用 [發行精靈] 來設定基本設定，以發行您的應用程式。 這包括以下的發行屬性：  
  
-   發行資料夾位置：Visual Studio 複製檔案 (本機電腦、網路檔案共用、FTP 伺服器或網站) 的位置  
  
-   安裝資料夾位置：使用者進行安裝的來源之處 (網路檔案共用、FTP 伺服器、網站、CD/DVD)  
  
-   線上或離線可用性：使用者是否可以在有網路連線或在沒有網路連線的情況下，存取應用程式  
  
-   更新頻率：應用程式查看是否新的更新之頻率。  
  
 如需詳細資訊，請參閱 <<c0> [ 如何： 發行 ClickOnce 應用程式使用發行精靈](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
## <a name="publish-page"></a>發行頁面  
 [專案設計工具]  的 [發行]  頁面，可用以設定 ClickOnce 部署的屬性。 下表列出的主題。  
  
|標題|描述|  
|-----------|-----------------|  
|[如何： 指定 Visual Studio 複製檔案的位置](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|描述如何設定 Visual Studio 放置應用程式檔案和資訊清單的位置。|  
|[如何： 指定使用者將從安裝的位置](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|描述如何設定使用者下載及安裝應用程式的位置。|  
|[如何： 指定 ClickOnce 離線或線上安裝模式](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|描述如何設定是否可離線或在線上使用應用程式。|  
|[如何： 設定 ClickOnce 發行版本](../deployment/how-to-set-the-clickonce-publish-version.md)|描述如何設定 ClickOnce**發行版本**屬性，決定是否要發行的應用程式將會被視為更新。|  
|[如何： 自動累加 ClickOnce 的發行版本](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|描述如何自動遞增的修訂編號**PublishVersion**每次發行應用程式。|  
  
 如需詳細資訊，請參閱[專案設計工具、 發行頁](../ide/reference/publish-page-project-designer.md)  
  
### <a name="application-files-dialog-box"></a>應用程式檔案 對話方塊  
 您可利用這個對話方塊，指定專案中的檔案會如何分類以進行發行、動態下載與更新。 它包含的方格會列出預設未排除或有下載群組的專案檔案。  
  
 若要排除的檔案，將檔案標示為資料檔或必備，和在 Visual Studio UI 中建立的條件式安裝的檔案群組，請參閱[如何： 指定哪些檔案由 ClickOnce 發行](../deployment/how-to-specify-which-files-are-published-by-clickonce.md)。 您也可以使用 Mage.exe 來標記資料檔。 如需詳細資訊，請參閱 <<c0> [ 如何： 在 ClickOnce 應用程式中納入資料檔案](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)。  
  
### <a name="prerequisites-dialog-box"></a>必要條件對話方塊  
 這個對話方塊會指定安裝哪些必備元件，以及安裝這些元件的方法。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用 ClickOnce 應用程式安裝必要條件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)並[必要條件對話方塊](../ide/reference/prerequisites-dialog-box.md)。  
  
### <a name="application-updates-dialog-box"></a>應用程式 [更新] 對話方塊  
 這個對話方塊會指定應用程式安裝應該如何查看是否有更新。 如需詳細資訊，請參閱 <<c0> [ 如何： 管理 ClickOnce 應用程式的更新](../deployment/how-to-manage-updates-for-a-clickonce-application.md)。  
  
### <a name="publish-options-dialog-box"></a>發行選項 對話方塊  
 [發行選項] 對話方塊會指定應用程式的部署選項。  
  
|||  
|-|-|  
|[如何： 變更 ClickOnce 應用程式的發行語言](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|描述如何指定語言和文化特性，以符合當地語系化的版本。|  
|[如何： 指定 ClickOnce 應用程式的開始功能表名稱](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|描述如何變更 ClickOnce 應用程式的顯示名稱。|  
|[如何： 指定技術支援的連結](../deployment/how-to-specify-a-link-for-technical-support.md)|描述如何設定**支援 URL**屬性，可識別網頁或使用者可以前往取得應用程式的相關資訊的檔案共用。|  
|[如何： 在 ClickOnce 部署中指定個別必要條件的支援 URL](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|示範如何手動變更應用程式資訊清單，以包含每個必備項目的個別支援 URL。|  
|[如何： 指定 ClickOnce 應用程式的發行頁面](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|描述如何產生及發行預設網頁 (publish.htm) 以及應用程式|  
|[如何： 自訂 ClickOnce 預設 Web 網頁](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|描述如何自訂自動產生及發行的網頁以及應用程式。|  
|[如何： 啟用 CD 安裝的 AutoStart](../deployment/how-to-enable-autostart-for-cd-installations.md)|描述如何啟用 AutoStart，以便在插入媒體時，自動啟動 ClickOnce 應用程式。|  
  
## <a name="related-tpics"></a>相關的 tpics  
  
|標題|描述|  
|-----------|-----------------|  
|[如何： 建立檔案關聯的 ClickOnce 應用程式](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|描述如何將副檔名支援加入 ClickOnce 應用程式。|  
|[如何： 擷取在線上 ClickOnce 應用程式中的查詢字串資訊](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|示範如何擷取在 URL 中傳遞以執行 ClickOnce 應用程式的參數。|  
|[如何： 使用設計工具停用 ClickOnce 應用程式的 URL 啟動](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|描述如何強制使用者啟動應用程式**啟動**使用設計工具 功能表。|  
|[如何： 停用 ClickOnce 應用程式的 URL 啟動](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|描述如何強制使用者啟動應用程式**啟動**功能表。|  
|[逐步解說： 下載組件隨選與 ClickOnce 部署 API 使用設計工具](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|描述如何只有在使用設計工具的應用程式第一次使用應用程式組件時，才下載這些組件。|  
|[逐步解說： 下載組件隨選與 ClickOnce 部署 API](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|說明如何只有在應用程式第一次使用應用程式組件時，才下載這些組件。|  
|[逐步解說： 下載附屬組件，依需求以 ClickOnce 部署 API](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|描述如何將您的附屬組件標記為選用項目，並僅下載用戶端電腦因其目前文化特性設定而需要的組件。|  
|[逐步解說： 手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|說明如何使用.NET Framework 公用程式，部署 ClickOnce 應用程式。|  
|[逐步解說： 手動部署 ClickOnce 應用程式，而無須重新簽署而且會保留商標資訊](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)|說明如何使用 .NET Framework 公用程式，部署 ClickOnce 應用程式，但不重新簽署資訊清單。|  
|[如何： 將專案設定到目標平台](../ide/how-to-configure-projects-to-target-platforms.md)|說明如何藉由變更發佈適用於 64 位元處理器**目標 CPU**或是**平台目標**專案中的屬性。|  
|[逐步解說： 啟用 ClickOnce 應用程式，在多個.NET Framework 版本上執行](http://msdn.microsoft.com/en-us/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|說明如何啟用 ClickOnce 應用程式，在 NET Framework 的多個版本上安裝及執行。|  
|[逐步解說： 建立 ClickOnce 應用程式的自訂安裝程式](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|說明如何建立自訂安裝程式，來安裝 ClickOnce 應用程式。|  
|[如何： 發行已啟用視覺化樣式的 WPF 應用程式](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|提供逐步指示，解決在您嘗試發行啟用視覺化樣式的 WPF 應用程式時出現的錯誤。|  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce 參考](../deployment/clickonce-reference.md)