---
title: 建立 ClickOnce 應用程式供其他人部署 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 10f7cf3b6069c80337213283eddd12bdd54e4b7d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="creating-clickonce-applications-for-others-to-deploy"></a>建立 ClickOnce 應用程式供其他人部署
並非所有的開發人員建立 ClickOnce 部署計劃部署應用程式本身。 其中許多只使用 ClickOnce 封裝其應用程式，然後遞交檔案給客戶，例如大型公司。 客戶會變成負責裝載其網路上的應用程式。 本主題討論這類部署中的.NET Framework 3.5 版之前的版本中固有的問題。 然後，它會描述在.NET Framework 3.5 使用新的 [使用信任的資訊清單] 功能提供新的方案。 最後，它會做出結論與建議的策略，以建立 ClickOnce 部署的客戶仍在使用較舊版本的.NET framework。  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>為客戶建立部署的相關問題  
 當您打算提供給客戶的部署時，就會發生幾個問題。 第一個問題是有關程式碼簽署。 才能透過網路部署，部署資訊清單和 ClickOnce 部署的應用程式資訊清單必須同時簽署的數位憑證。 這會引發的問題時是否要使用的開發人員憑證或客戶的憑證簽署資訊清單。  
  
 要使用的憑證問題並重要，因為 ClickOnce 應用程式的身分識別為基礎的部署資訊清單的數位簽章。 如果開發人員簽署部署資訊清單，它可能會導致衝突，如果客戶是大型公司，並有一個以上的公司部門部署自訂應用程式的版本。  
  
 例如，Adventure Works 的財務部門和人力資源部門。 這兩個部門的授權從 SQL 資料庫中儲存的資料產生報告的 Microsoft corporation 的 ClickOnce 應用程式。 Microsoft 會提供每個部門各以自訂其資料的應用程式的版本。 如果應用程式使用相同的 Authenticode 憑證簽署，便會嘗試使用兩個應用程式的使用者會遇到錯誤，因為 ClickOnce 會將第二個為與第一個應用程式。 在此情況下，客戶可能會導致無法預期且不必要的副作用，包括由應用程式在本機儲存的任何資料遺失。  
  
 發生其他問題相關的程式碼簽章是`deploymentProvider`會告訴 ClickOnce 何處尋找應用程式更新的部署資訊清單中的項目。 這個項目已加入至部署資訊清單簽署它之前。 如果這個項目加入之後，必須重新簽署部署資訊清單。  
  
### <a name="requiring-the-customer-to-sign-the-deployment-manifest"></a>要求客戶簽署部署資訊清單  
 非唯一的部署問題的解決方案之一是讓開發人員簽署的應用程式資訊清單和客戶簽署部署資訊清單。 當這種方法，它會導致其他問題。 因為 Authenticode 憑證必須保持受保護的資產，客戶無法只會讓程式開發人員簽署部署憑證。 雖然客戶可以簽署部署資訊清單本身使用.NET Framework SDK 中使用免費的工具，這可能需要比客戶願意或能夠提供更多技術知識。 在這種情況下，開發人員通常會建立應用程式、 網站或其他機制，透過此客戶提交自己版本的簽章的應用程式。  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>簽署 ClickOnce 應用程式安全性的客戶的影響  
 即使開發人員和客戶同意客戶應該簽署應用程式資訊清單，這會引發有關應用程式的身分識別的其他問題尤其是它會套用至受信任的應用程式部署。 (如需有關這項功能的詳細資訊，請參閱[受信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)。)說出 Adventure Works 想要設定其用戶端電腦，讓任何 Microsoft Corporation 所提供給他們的應用程式執行以完全信任。 如果 Adventure Works 簽署部署資訊清單，ClickOnce 會判斷應用程式的信任層級使用 Adventure 工作安全性簽章。  
  
## <a name="creating-customer-deployments-by-using-application-manifest-for-trust"></a>使用信任的應用程式資訊清單建立客戶部署  
 在.NET Framework 3.5 的 ClickOnce 包含新的功能，可讓開發人員及客戶新方案的案例是應該用來簽署資訊清單的方式。 ClickOnce 應用程式資訊清單支援新的項目，名為`<useManifestForTrust>`，可讓開發人員，表示要在應用程式資訊清單的數位簽章項目應該用來進行信任決策。 開發人員會使用 ClickOnce 封裝工具 — 例如 Mage.exe、 MageUI.exe 和 Visual Studio，在應用程式資訊清單中包含這個項目以及其發行者名稱和應用程式的名稱嵌入資訊清單。  
  
 當使用`<useManifestForTrust>`，不需要使用憑證授權單位所核發的 Authenticode 憑證來簽署部署資訊清單。 相反地，它可以使用所謂的自我簽署憑證簽署。 自我簽署的憑證是使用標準.NET Framework SDK 工具，產生客戶或開發人員，然後使用標準的 ClickOnce 部署工具套用至部署資訊清單。 如需詳細資訊，請參閱[MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx)。  
  
 使用自我簽署的憑證的部署資訊清單有幾個優點。 不需要在取得或建立自己的 Authenticode 憑證，客戶`<useManifestForTrust>`可簡化部署的客戶，同時允許開發人員維護自己的商標設定識別身分應用程式上。 結果是帶正負號的部署更安全且唯一的應用程式身分識別的一組。 這樣就不可能從同一個應用程式部署至多個客戶，可能會發生的衝突。  
  
 如需如何建立與 ClickOnce 部署的逐步解說資訊`<useManifestForTrust>`啟用，請參閱[逐步解說： 手動部署 ClickOnce 應用程式，並不需要重新簽署，並會保留商標資訊](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>信任是在執行階段的運作方式的應用程式資訊清單  
 若要進一步了解使用信任的應用程式資訊清單的運作方式在執行階段，請考慮下列的範例。 以.NET Framework 3.5 為目標的 ClickOnce 應用程式是 Microsoft 所建立的。 應用程式資訊清單使用`<useManifestForTrust>`項目會由 Microsoft 簽署。 Adventure Works 會使用自我簽署的憑證來簽署部署資訊清單。 Adventure 的 Works 設定用戶端信任由 Microsoft 簽署的任何應用程式。  
  
 當使用者按一下部署資訊清單的連結時，ClickOnce 會在使用者電腦上安裝應用程式。 憑證和部署資訊識別唯一用戶端電腦上的 ClickOnce 應用程式。 如果使用者嘗試從不同位置，重新安裝相同的應用程式，ClickOnce 可以使用這個身分識別來判斷應用程式已經存在於用戶端。  
  
 接下來，ClickOnce 會檢查用來簽署的 ClickOnce 會授與的信任層級的應用程式資訊清單的 Authenticode 憑證。 Adventure Works 已設定它的用戶端信任由 Microsoft 簽署的任何應用程式，因為此 ClickOnce 應用程式會授與完全信任。 如需詳細資訊，請參閱 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。  
  
## <a name="creating-customer-deployments-for-earlier-versions"></a>建立舊版的客戶部署  
 如果開發人員正在部署 ClickOnce 應用程式使用的.NET framework 的較舊版本的客戶？ 下列各節摘要說明幾個建議的解決方案，以及優點和缺點，每個。  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>代表客戶的簽署部署  
 其中一種可能的部署策略是開發人員建立使用客戶自己的私密金鑰來簽署部署他們的客戶，代表一種機制。 這可防止開發人員不必管理私密金鑰或多個部署套件。 開發人員只是提供相同的部署，為每位客戶。 這是由客戶針對其環境加以自訂，使用簽章服務。  
  
 這個方法的缺點之一是實作它所需的成本與時間。 雖然可以使用.NET Framework SDK 中提供的工具來建置這類服務，它會在產品生命週期增加更多的開發時間。  
  
 如本主題稍早所述，另一個缺點是每個客戶的應用程式版本會具有相同的應用程式識別，這樣可能會導致衝突。 如果這是一項考量，開發人員可以變更 [名稱] 欄位，用於產生的部署資訊清單時提供每個應用程式的唯一名稱。 這將會建立在不同的識別每個版本的應用程式，並排除任何身分識別的潛在衝突。 此欄位對應到`-Name`引數的 Mage.exe，並**名稱**欄位**名稱**MageUI.exe 中的 索引標籤。  
  
 例如，開發人員已經建立名為 Application1 應用程式。 不使用 [名稱] 欄位設定為 Application1 中建立單一部署，開發人員可以建立數個部署與特定客戶的變化，此名稱，例如 Application1 CustomerA，Application1 CustomerB，等等。  
  
### <a name="deploy-using-a-setup-package"></a>使用安裝程式封裝部署  
 產生的 Microsoft 安裝程式專案，以執行 ClickOnce 應用程式的初始部署為第二個可能的部署策略。 這可以提供數種不同格式之一： 為 MSI 部署，安裝程式可執行檔 (。EXE)，或以批次指令碼以及封包 (.cab) 檔案。  
  
 使用這項技術，開發人員提供客戶的部署包含應用程式檔案、 應用程式資訊清單中，以及做為範本的部署資訊清單。 客戶會執行安裝程式會提示他們提供部署 URL （伺服器或檔案共用使用者將從中安裝 ClickOnce 應用程式的位置），以及數位憑證。 也可以選擇安裝應用程式提示您輸入其他 ClickOnce 組態選項，例如更新檢查的間隔。 之後會收集此資訊，安裝程式會產生實際的部署資訊清單、 登入，並發行 ClickOnce 應用程式，以指定的伺服器位置。  
  
 有三種方式，客戶可以簽署部署資訊清單在此情況下：  
  
1.  客戶可以使用憑證授權單位 (CA) 核發的有效憑證。  
  
2.  與這種方式的做法，客戶可以選擇使用自我簽署的憑證其部署資訊清單簽章。 這樣的缺點是，它會導致應用程式時，要顯示 「 未知的發行者 」 的單字會要求使用者是否要安裝它。 不過，好處是，它會防止較小的客戶需要花費大量時間和金錢所需的憑證授權單位所核發的憑證。  
  
3.  最後，開發人員可以在安裝套件包含自己的自我簽署的憑證。 這會導致與本主題稍早所述的應用程式識別潛在的問題。  
  
 設定部署專案方法的缺點是建置自訂部署應用程式所需的成本與時間。  
  
### <a name="have-customer-generate-deployment-manifest"></a>由客戶產生部署資訊清單  
 第三個可能的部署策略是要將只有應用程式檔案和應用程式資訊清單關閉給客戶。 在此案例中，客戶就是負責產生並簽署部署資訊清單使用.NET Framework SDK。  
  
 這個方法的缺點是它需要客戶安裝.NET Framework SDK 工具，並讓開發人員或系統管理員身分在使用這些技術。 有些客戶可能會要求需要少量或沒有技術投入時間集中用於其組件的解決方案。  
  
## <a name="see-also"></a>另請參閱  
 [部署 ClickOnce 應用程式進行測試和實際執行伺服器，而不重新簽章](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [逐步解說：手動部署不需要重新簽署而且會保留商標資訊的 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)