---
title: 建立 ClickOnce 應用程式供其他人部署 |Microsoft Docs
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
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: b8f4736066501324d5428fd2634dfacd8c6537a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497098"
---
# <a name="creating-clickonce-applications-for-others-to-deploy"></a>建立 ClickOnce 應用程式供其他人部署
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[建立 ClickOnce 應用程式供其他人部署](https://docs.microsoft.com/visualstudio/deployment/creating-clickonce-applications-for-others-to-deploy)。  
  
並非所有的開發人員會建立 ClickOnce 部署計劃部署應用程式本身。 多個封裝使用 ClickOnce 應用程式，然後遞交檔案給客戶，例如大型公司。 客戶會變成負責裝載其網路上的應用程式。 本主題討論某些這類部署中的.NET Framework 3.5 版之前版本的問題。 然後，它會描述.NET Framework 3.5 中使用新的 [使用信任的資訊清單] 功能來提供新的方案。 最後，最後建立的客戶仍在使用舊版.NET Framework 的 ClickOnce 部署的建議策略。  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>建立針對客戶部署的相關問題  
 當您打算提供給客戶的部署時，就會發生幾個問題。 第一個問題是有關程式碼簽署。 若要透過網路部署，部署資訊清單和 ClickOnce 部署的應用程式資訊清單必須同時簽署使用數位憑證。 這會引發時是否要使用的開發人員憑證或客戶的憑證簽署資訊清單的問題。  
  
 若要使用哪一個憑證的問題而言很重要，因為 ClickOnce 應用程式的身分識別為基礎的部署資訊清單的數位簽章。 如果開發人員簽署部署資訊清單，它可能會導致衝突如果客戶是大型公司，以及多個部門的公司部署應用程式的自訂的版本。  
  
 例如，Adventure Works 有財務部門和人力資源部門。 這兩個部門的授權從 SQL database 中儲存的資料產生報告的 Microsoft corporation 的 ClickOnce 應用程式。 Microsoft 會提供每個部門，以自訂其資料的應用程式的版本。 如果應用程式會使用相同的 Authenticode 憑證簽署，便會嘗試使用兩個應用程式的使用者會遇到錯誤，因為 ClickOnce 會將第二個為與第一個應用程式。 在此情況下，客戶可能會導致無法預期和不必要的副作用包含儲存在本機應用程式的任何資料遺失。  
  
 發生其他問題相關的程式碼簽署是`deploymentProvider`告知 ClickOnce 在何處尋找應用程式更新的部署資訊清單中的項目。 這個項目具有要加入至部署資訊清單簽署它之前。 如果之後新增此項目，則必須重新簽署部署資訊清單。  
  
### <a name="requiring-the-customer-to-sign-the-deployment-manifest"></a>需要客戶簽署部署資訊清單  
 這個問題的非唯一部署的解決方案之一是讓開發人員簽署的應用程式資訊清單和客戶簽署部署資訊清單。 雖然這種方法的運作方式，它會造成其他問題。 Authenticode 憑證必須保持受保護的資產，因為客戶不能只會為開發人員簽署部署的憑證。 雖然客戶可以簽署部署資訊清單本身使用.NET Framework SDK 中免費提供的工具，這可能需要比客戶不願意或能夠提供更多技術的知識。 在這種情況下，開發人員通常會建立應用程式、 網站或其他機制，讓客戶可以提交其簽署的應用程式的版本。  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>簽署 ClickOnce 應用程式安全性的客戶的影響  
 即使開發人員和客戶同意客戶應登入應用程式資訊清單，這引發應用程式的身分識別，其他問題，特別是，因為它適用於受信任的應用程式部署。 (如需這項功能的詳細資訊，請參閱[Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。)假設 Adventure Works 想要設定其用戶端電腦，因此任何由 Microsoft Corporation 提供給他們的應用程式執行以完全信任。 如果 Adventure Works 簽署部署資訊清單，ClickOnce 會判斷應用程式的信任層級使用 Adventure Work 安全性簽章。  
  
## <a name="creating-customer-deployments-by-using-application-manifest-for-trust"></a>使用信任的應用程式資訊清單建立客戶部署  
 .NET Framework 3.5 中的 ClickOnce 包含新的功能，可讓開發人員和客戶的新解決方案的案例是簽署資訊清單的方式。 ClickOnce 應用程式資訊清單支援新的項目，名為`<useManifestForTrust>`，可讓開發人員若要表示應用程式資訊清單的數位簽章是什麼應該用來進行信任決策。 開發人員使用 ClickOnce 封裝工具-Mage.exe、 MageUI.exe 等 Visual Studio，在應用程式資訊清單中，包含這個項目以及內嵌資訊清單中的發行者名稱與應用程式的名稱。  
  
 當使用`<useManifestForTrust>`，不需要使用憑證授權單位所核發的 Authenticode 憑證來簽署部署資訊清單。 相反地，它可以使用所謂的自我簽署憑證簽署。 自我簽署的憑證是由客戶或開發人員產生使用標準的.NET Framework SDK 工具，，，然後使用標準的 ClickOnce 部署工具，以套用至部署資訊清單。 如需詳細資訊，請參閱 < [Makecert.exe （憑證建立工具）](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)。  
  
 使用自我簽署的憑證的部署資訊清單有幾個優點。 取得或建立自己的 Authenticode 憑證，客戶無須`<useManifestForTrust>`可簡化部署的客戶，同時讓開發人員維護自己的應用程式的商標身分識別。 結果是一組的帶正負號的部署更安全且具有唯一的應用程式身分識別。 這樣就不可能從同一個應用程式部署至多個客戶可能會發生的衝突。  
  
 如需如何建立與 ClickOnce 部署的逐步資訊`<useManifestForTrust>`啟用，請參閱[逐步解說： 手動部署 ClickOnce 應用程式，並不需要重新簽署和該會保留商標資訊](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>信任適用於在執行階段如何應用程式資訊清單  
 若要進一步了解使用信任的應用程式資訊清單的運作方式在執行階段，請考慮下列的範例。 .NET Framework 3.5 為目標的 ClickOnce 應用程式是由 Microsoft 建立的。 應用程式資訊清單使用`<useManifestForTrust>`項目和經過 Microsoft 簽署。 Adventure Works 使用自我簽署的憑證簽署部署資訊清單。 Adventure Works 用戶端會設定為信任由 Microsoft 所簽署的任何應用程式。  
  
 當使用者按一下部署資訊清單的連結時，ClickOnce 會在使用者的電腦上安裝應用程式。 憑證和部署資訊會識別唯一用戶端電腦上的 ClickOnce 應用程式。 如果使用者嘗試從不同的位置重新安裝相同的應用程式，ClickOnce 可以使用這個身分識別，以判斷應用程式已存在於用戶端。  
  
 接下來，ClickOnce 會檢查用來簽署判斷的 ClickOnce 會授與的信任層級的應用程式資訊清單的 Authenticode 憑證。 Adventure Works 已設定它的用戶端信任由 Microsoft 所簽署的任何應用程式，因為這個 ClickOnce 應用程式會授與完全信任。 如需詳細資訊，請參閱 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。  
  
## <a name="creating-customer-deployments-for-earlier-versions"></a>建立適用於舊版的客戶部署  
 如果開發人員部署 ClickOnce 應用程式會使用舊版.NET Framework 的客戶嗎？ 下列各節摘要說明數個建議的解決方案，以及每個的優缺點。  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>代表客戶的簽署部署  
 開發人員建立使用客戶自己的私用金鑰來簽署部署他們的客戶，代表一種機制，是其中一種可能的部署策略。 這可防止開發人員無須分心於管理私用金鑰或多個部署套件。 開發人員只是會為每位客戶提供相同的部署。 這是由客戶針對其環境加以自訂，使用簽章的服務。  
  
 這個方法的缺點之一是實作它所需的成本與時間。 雖然這類服務可以使用.NET Framework SDK 中提供的工具進行建置，它會在產品生命週期中新增更多的開發時間。  
  
 如本主題稍早所述，另一個缺點是應用程式的每個客戶的版本會有相同的應用程式識別，這可能導致衝突。 如果這方面的問題，開發人員可以變更 [名稱] 欄位，來產生部署資訊清單時提供每個應用程式的唯一名稱。 這會建立個別的身分識別，每個版本的應用程式，並排除任何可能發生的身分識別衝突。 此欄位對應`-Name`引數的 Mage.exe，進而**名稱**欄位**名稱**MageUI.exe 中的索引標籤。  
  
 例如，假設開發人員會建立名為 Application1 應用程式。 而不是使用 [名稱] 欄位設定為應用程式 1 建立單一部署，開發人員可以使用客戶特定的變化，此名稱，例如 Application1-Application1-CustomerB CustomerA 建立數個部署等等。  
  
### <a name="deploy-using-a-setup-package"></a>使用安裝程式套件部署  
 產生 Microsoft 安裝程式專案，以執行 ClickOnce 應用程式的初始部署為第二個可能的部署策略。 可提供數個不同格式之一： 為 MSI 部署，安裝程式可執行檔 (。EXE)，或為封包 (.cab) 檔案，以及批次指令碼。  
  
 使用這項技術，開發人員會提供客戶部署，包括應用程式檔案、 應用程式資訊清單中，以及做為範本的部署資訊清單。 客戶會執行安裝程式會提示他們提供的部署 URL （伺服器或檔案共用使用者將從中安裝 ClickOnce 應用程式的位置），以及數位憑證。 也可以選擇安裝應用程式提示您輸入其他的 ClickOnce 組態選項，例如更新檢查間隔。 之後會收集此資訊，安裝程式會產生實際的部署資訊清單、 登入，並發行 ClickOnce 應用程式，到指定的伺服器位置。  
  
 有三種方式，客戶可以簽署部署資訊清單，在此情況下：  
  
1.  客戶可以使用的憑證授權單位 (CA) 核發的有效憑證。  
  
2.  這種方法的一種變化，客戶可以選擇使用自我簽署的憑證其部署資訊清單簽章。 缺點是，它會導致應用程式顯示文字 「 未知的發行者 」 時系統會詢問是否要安裝它。 不過，好處是，它會防止較小的客戶需花費的時間和金錢所需的憑證授權單位所核發的憑證。  
  
3.  最後，開發人員可以在安裝套件包含他們自己的自我簽署的憑證。 這會引入本主題稍早所述的應用程式身分識別的潛在問題。  
  
 設定部署專案方法的缺點是時間和建置自訂部署的應用程式所需的費用。  
  
### <a name="have-customer-generate-deployment-manifest"></a>讓客戶產生部署資訊清單  
 第三個可能的部署策略是交給只有應用程式檔案和應用程式資訊清單關閉給客戶。 在此案例中，客戶須負責產生並簽署部署資訊清單中使用.NET Framework SDK。  
  
 這個方法的缺點是它需要安裝.NET Framework SDK 工具，並讓開發人員或系統管理員是在使用這些技術熟練的客戶。 有些客戶可能要求的解決方案需要其組件上的少量或沒有技術投入時間。  
  
## <a name="see-also"></a>另請參閱  
 [部署 ClickOnce 應用程式進行測試和實際執行伺服器，但不重新簽署](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [逐步解說：手動部署不需要重新簽署而且會保留商標資訊的 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)



