---
title: 發行 ClickOnce 應用程式 |Microsoft Docs
description: 瞭解如何使用發佈嚮導第一次發行 ClickOnce 應用程式。 在 [專案設計工具] 的 [發行] 頁面上進行後續變更。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fa9e94bf124888d05b6393a4821b5db61181871c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927570"
---
# <a name="publish-clickonce-applications"></a>發佈 ClickOnce 應用程式
首次發行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，可以使用 [發行精靈] 來設定發行屬性。 這個精靈僅提供少數屬性；所有其他屬性都設為其預設值。

 對發佈屬性所進行的任何後續變更，可在 [專案設計工具] 的 [發佈] 頁面中進行。

## <a name="publish-wizard"></a>發行精靈
 您可以使用 [發行精靈] 來設定基本設定，以發行您的應用程式。 這包括以下的發行屬性：

- 發行資料夾位置：Visual Studio 複製檔案 (本機電腦、網路檔案共用、FTP 伺服器或網站) 的位置

- 安裝資料夾位置：終端使用者進行安裝的來源之處 (網路檔案共用、FTP 伺服器、網站、CD/DVD)

- 線上或離線可用性：終端使用者是否可以在有網路連線或在沒有網路連線的情況下，存取應用程式

- 更新頻率：應用程式查看是否新的更新之頻率。

  如需詳細資訊，請參閱 [如何：使用發佈嚮導發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。

## <a name="publish-page"></a>發行頁面
 [專案設計工具]  的 [發行]  頁面，可用以設定 ClickOnce 部署的屬性。 下表列出相關主題。

|標題|描述|
|-----------|-----------------|
|[How to: Specify where Visual Studio copies the files](../deployment/how-to-specify-where-visual-studio-copies-the-files.md) (如何：指定 Visual Studio 複製檔案的位置)|描述如何設定 Visual Studio 放置應用程式檔案和資訊清單的位置。|
|[How to: Specify the location where end users will install from (如何：指定終端使用者會從該處安裝的位置)](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|描述如何設定使用者下載及安裝應用程式的位置。|
|[How to: Specify the ClickOnce offline or online install mode](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md) (如何：指定 ClickOnce 離線或線上安裝模式)|描述如何設定是否可離線或在線上使用應用程式。|
|[How to: Set the ClickOnce publish version (如何：設定 ClickOnce 發行版本)](../deployment/how-to-set-the-clickonce-publish-version.md)|描述如何設定 ClickOnce **發佈版本** 屬性，其會決定是否將您發佈的應用程式視為更新。|
|[How to: Automatically increment the ClickOnce publish version](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md) (如何：自動累加 ClickOnce 的發行版本)|描述如何在每次發佈應用程式時，自動遞增 **PublishVersion** 的修訂編號。|

 如需詳細資訊，請參閱 [專案設計工具、發行頁](../ide/reference/publish-page-project-designer.md)

### <a name="application-files-dialog-box"></a>[應用程式檔案] 對話方塊
 您可利用這個對話方塊，指定專案中的檔案會如何分類以進行發行、動態下載與更新。 它包含的方格會列出預設未排除或有下載群組的專案檔案。

 若要排除檔案、將檔案標示為資料檔案或必要條件，並在 Visual Studio UI 中建立條件式安裝的檔案群組，請參閱 [如何：指定 ClickOnce 發行的](../deployment/how-to-specify-which-files-are-published-by-clickonce.md)檔案。 您也可以使用 Mage.exe 來標記資料檔。 如需詳細資訊，請參閱 [How to: Include a data file in a ClickOnce application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md) (如何：如何在 ClickOnce 應用程式中包含資料檔案)。

### <a name="prerequisites-dialog-box"></a>必要條件對話方塊
 這個對話方塊會指定安裝哪些必備元件，以及安裝這些元件的方法。 如需詳細資訊，請參閱 [如何：使用 ClickOnce 應用程式安裝必要條件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) 和 [必要條件對話方塊](../ide/reference/prerequisites-dialog-box.md)。

### <a name="application-updates-dialog-box"></a>應用程式更新對話方塊
 這個對話方塊會指定應用程式安裝應該如何查看是否有更新。 如需詳細資訊，請參閱 [如何：管理 ClickOnce 應用程式的更新](../deployment/how-to-manage-updates-for-a-clickonce-application.md)。

### <a name="publish-options-dialog-box"></a>發佈選項對話方塊
 [發行選項] 對話方塊會指定應用程式的部署選項。

|標題|描述|
|-|-|
|[How to: Change the publish language for a ClickOnce application](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md) (如何：變更 ClickOnce 應用程式的發行語言)|描述如何指定語言和文化特性，以符合當地語系化的版本。|
|[How to: Specify a Start menu name for a ClickOnce application](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md) (如何：指定 ClickOnce 應用程式的 [開始] 功能表名稱)|描述如何變更 ClickOnce 應用程式的顯示名稱。|
|[How to: Specify a link for Technical Support](../deployment/how-to-specify-a-link-for-technical-support.md) (如何：指定技術支援的連結)|描述如何設定 **支援 URL** 屬性，其可識別使用者可以前往以取得應用程式相關資訊之網頁或檔案共用。|
|[How to: Specify a Support URL for individual prerequisites in a ClickOnce deployment](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md) (如何：在 ClickOnce 部署中指定個別必要條件的支援 URL)|示範如何手動變更應用程式資訊清單，以包含每個必備項目的個別支援 URL。|
|[如何：指定 ClickOnce 應用程式的發行頁面](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|描述如何產生及發行預設網頁 (publish.htm) 以及應用程式|
|[How to: Customize the ClickOnce default Web page](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md) (如何：自訂 ClickOnce 預設網頁)|描述如何自訂自動產生及發行的網頁以及應用程式。|
|[How to: Enable AutoStart for CD installations (如何：啟用 CD 安裝的 AutoStart)](../deployment/how-to-enable-autostart-for-cd-installations.md)|描述如何啟用 AutoStart，以便在插入媒體時，自動啟動 ClickOnce 應用程式。|

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[How to: Create file associations For a ClickOnce application](../deployment/how-to-create-file-associations-for-a-clickonce-application.md) (如何：建立 ClickOnce 應用程式的檔案關聯)|描述如何將副檔名支援加入 ClickOnce 應用程式。|
|[How to: Retrieve query string information in an online ClickOnce application](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md) (如何：在線上 ClickOnce 應用程式中擷取查詢字串資訊)|示範如何擷取在 URL 中傳遞以執行 ClickOnce 應用程式的參數。|
|[How to: Disable URL activation of ClickOnce applications by using the designer](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md) (如何：使用設計工具停用 ClickOnce 應用程式的 URL 啟動過程)|描述如何強制使用者使用設計工具，從 [開始] 功能表啟動應用程式。|
|[How to: Disable URL activation of ClickOnce applications](../deployment/how-to-disable-url-activation-of-clickonce-applications.md) (如何：停用 ClickOnce 應用程式的 URL 啟動過程)|描述如何強制使用者從 [開始] 功能表啟動應用程式。|
|[Walkthrough: Downloading assemblies on demand with the ClickOnce deployment API using the Designer](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md) (逐步解說：依需求使用設計工具以 ClickOnce 部署 API 下載組件)|描述如何只有在使用設計工具的應用程式第一次使用應用程式組件時，才下載這些組件。|
|[逐步解說：使用 ClickOnce 部署 API 依需求下載元件](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|說明如何只有在應用程式第一次使用應用程式組件時，才下載這些組件。|
|[逐步解說：使用 ClickOnce 部署 API 依需求下載附屬元件](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|描述如何將您的附屬組件標記為選用項目，並僅下載用戶端電腦因其目前文化特性設定而需要的組件。|
|[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|說明如何使用.NET Framework 公用程式，部署 ClickOnce 應用程式。|
|[逐步解說：手動部署不需要重新簽署而且會保留商標資訊的 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)|說明如何使用 .NET Framework 公用程式，部署 ClickOnce 應用程式，但不重新簽署資訊清單。|
|[如何：將專案設定成以各種平台為目標](../ide/how-to-configure-projects-to-target-platforms.md)|說明如何透過變更專案中的 [目標 CPU] 或 [平台目標] 屬性，針對 64 位元處理器發佈。|
|[逐步解說：讓 ClickOnce 應用程式可在多個 .NET Framework 版本上執行](/previous-versions/dd996998(v=vs.100))|說明如何啟用 ClickOnce 應用程式，在 NET Framework 的多個版本上安裝及執行。|
|[逐步解說：為 ClickOnce 應用程式建立自訂安裝程式](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|說明如何建立自訂安裝程式，來安裝 ClickOnce 應用程式。|
|[How to: Publish a WPF application with visual styles enabled](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md) (如何：發行已啟用視覺化樣式的 WPF 應用程式)|提供逐步指示，解決在您嘗試發行啟用視覺化樣式的 WPF 應用程式時出現的錯誤。|

## <a name="see-also"></a>另請參閱
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce 參考](../deployment/clickonce-reference.md)