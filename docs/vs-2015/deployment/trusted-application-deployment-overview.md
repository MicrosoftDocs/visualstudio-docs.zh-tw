---
title: 受信任的應用程式部署概觀 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- ClickOnce deployment, security
- trusted application deployment
ms.assetid: b24a1702-8fbe-45b1-87a0-9618a0708f1d
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: afcfc0d2a494b27359de041b13a8e9595ede1bc7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487705"
---
# <a name="trusted-application-deployment-overview"></a>受信任的應用程式部署概觀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[Trusted Application Deployment Overview](https://docs.microsoft.com/visualstudio/deployment/trusted-application-deployment-overview)。  
  
本主題提供如何部署 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式的概觀，使用受信任的應用程式部署技術可提高此應用程式的權限。  
  
 信任的應用程式部署 ([!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署技術的一部分)，可讓各種規模的組織以更安全的方式授與 Managed 應用程式的其他權限，而不需要進行使用者提示。 使用信任的應用程式部署，組織可以只設定用戶端電腦的信任發行者清單，這些發行者是使用 Authenticode 憑證來識別。 此後，由其中一個信任發行者簽署的任何 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式，會收到較高的信任層級。  
  
> [!NOTE]
>  信任的應用程式部署需要對使用者電腦進行一次性的組態。 在 Managed 桌面環境中，可以使用全域原則來執行此組態。 如果您的應用程式不想要使用這種方式，請改用權限提高。 如需詳細資訊，請參閱[保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。  
  
## <a name="trusted-application-deployment-basics"></a>信任的應用程式部署基本概念  
 下表顯示信任的應用程式部署所涉及的物件和角色。  
  
|物件或角色|描述|  
|--------------------|-----------------|  
|系統管理員|負責更新和維護用戶端電腦的組織實體|  
|測試管理員|在 Common Language Runtime (CLR) 內負責強制執行用戶端應用程式安全性的子系統。|  
|發行者|撰寫和維護應用程式的實體。|  
|部署者|封裝並散發應用程式給使用者的實體。|  
|憑證|密碼編譯簽章，包含公開和私密金鑰；通常由可以確認其真確性的憑證授權單位 (CA) 發出。|  
|Authenticode 憑證|具有內嵌中繼資料的憑證，最重要的是描述可以採用該憑證的用途。|  
|憑證授權單位|驗證發行者身分識別並發出內嵌發行者中繼資料之憑證給他們的組織。|  
|根授權單位|授權其他憑證授權單位發出憑證的憑證授權單位。|  
|金鑰容器|儲存憑證的 Microsoft Windows 邏輯儲存空間。|  
|信任的發行者|Authenticode 憑證已加入用戶端電腦憑證信任清單 (CTL) 的發行者。|  
  
 在大型組織中，發行者和部署者通常是兩個不同的實體：  
  
-   發行者是建立 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式的群組。  
  
-   部署者是散發 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式到公司企業桌上型電腦的群組，通常是資訊技術 (IT) 部門。  
  
 您必須遵循下列步驟來利用信任的應用程式部署：  
  
1.  取得發行者的憑證。  
  
2.  將發行者加入所有用戶端上的信任的發行者存放區。  
  
3.  建立您的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式。  
  
4.  使用發行者的憑證簽署部署資訊清單。  
  
5.  將應用程式部署發行到用戶端電腦。  
  
### <a name="obtain-a-certificate-for-the-publisher"></a>取得發行者的憑證  
 數位憑證是 Microsoft Authenticode 驗證和安全性系統的核心元件。 Authenticode 是 Windows 作業系統的標準部分。 所有 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式必須以數位憑證簽署，不論它們是否參與信任的應用程式部署。 如需 Authenticode 如何與搭配運作的完整說明[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]，請參閱 < [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)。  
  
### <a name="add-the-publisher-to-the-trusted-publishers-store"></a>將發行者加入信任的發行者存放區  
 您的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式要收到較高層級的信任，您必須將憑證以信任的發行者加入應用程式執行所在的每台用戶端電腦。 執行這項工作是一次性的組態。 完成之後，您可以部署任意數量的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式並以您的發行者憑證簽署，它們全都會以高信任來執行。  
  
 如果您要在 Managed 桌面環境中部署應用程式，例如執行 Windows 作業系統的公司內部網路，您可以使用群組原則建立新的憑證信任清單 (CTL)，將信任的發行者加入用戶端的存放區。 如需詳細資訊，請參閱 [建立群組原則物件的憑證信任清單](http://go.microsoft.com/fwlink/?LinkId=102576)。  
  
 如果您不在 Managed 桌面環境中部署您的應用程式，在將憑證加入信任的發行者存放區時有下列選項：  
  
-   <xref:System.Security.Cryptography?displayProperty=fullName> 命名空間。  
  
-   CertMgr.exe，這是 Internet Explorer 的元件，因此存在於 Windows 98 和所有更新版本上。 如需詳細資訊，請參閱 < [Certmgr.exe （憑證管理員工具）](http://msdn.microsoft.com/library/7e953b43-1374-4bbc-814f-53ca1b6b52bb)。  
  
### <a name="create-a-clickonce-application"></a>建立 ClickOnce 應用程式  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式是 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 用戶端應用程式，並結合描述應用程式及提供安裝參數的資訊清單檔案。 您可以開啟將程式變成[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]使用應用程式**發佈**命令，在[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 或者，您可以使用 [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] 隨附的工具，產生 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署所需的所有檔案。 如需詳細步驟[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]部署，請參閱 <<c2> [ 逐步解說： 手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
 信任的應用程式部署是 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 所特有，並且僅能與 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式搭配使用。  
  
### <a name="sign-the-deployment"></a>簽署部署  
 取得您的憑證之後，必須用它來簽署您的部署。 如果您使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 發行精靈來部署應用程式，精靈會自動產生測試憑證 (如果您未自行指定憑證的話)。 您也可以使用[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]專案設計工具 視窗中，不過，若要提供由 CA 所提供的憑證。  另請參閱 [如何：使用發行精靈發行 ClickOnce 應用程式](http://msdn.microsoft.com/library/31kztyey\(v=vs.110\)) 或 [如何：使用發行精靈發行 ClickOnce 應用程式](http://msdn.microsoft.com/library/31kztyey\(v=vs.110\))。  
  
> [!CAUTION]
>  我們不建議使用測試憑證來部署應用程式。  
  
 您也可以使用 Mage.exe 或 MageUI.exe SDK 工具簽署應用程式。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 如需與部署簽署相關的命令列選項的完整清單，請參閱 < [Mage.exe （資訊清單產生和編輯工具）](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)。  
  
### <a name="publish-the-application"></a>發行應用程式  
 一旦您簽署了 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 資訊清單，應用程式便已準備好要發行到您的安裝位置。 安裝位置可以是 Web 伺服器、檔案共用或本機磁碟。 當用戶端存取第一次部署資訊清單時，信任管理員必須選擇是否已授與 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式權限，以便以已安裝之信任發行者的較高信任層級執行。 信任管理員會藉由比較用來簽署部署的憑證與儲存在用戶端信任的發行者存放區的憑證，來進行這項選擇。 如果信任管理員找到相符項目，應用程式會以高信任執行。  
  
## <a name="trusted-application-deployment-and-permission-elevation"></a>信任的應用程式部署和權限提高  
 如果目前的發行者不是信任的發行者，信任管理員會使用權限提高來查詢使用者是否想要授與您的應用程式提高的權限。 不過，如果系統管理員已停用權限提高，應用程式便無法取得執行用的權限。 應用程式不會執行，且不會對使用者顯示任何通知。 如需權限提高的詳細資訊，請參閱[保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。  
  
## <a name="limitations-of-trusted-application-deployment"></a>信任的應用程式部署的限制  
 您可以使用信任的應用程式部署，授與提高的信任給透過 Web 或企業共用部署的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式。 您不必針對在 CD 上散發的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式使用信任的應用程式部署，因為依預設，這些應用程式便已被授與完全信任。  
  
## <a name="see-also"></a>另請參閱  
 [Mage.exe (資訊清單產生和編輯工具)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)



