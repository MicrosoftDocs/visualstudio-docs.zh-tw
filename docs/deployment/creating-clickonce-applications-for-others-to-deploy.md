---
title: 建立 ClickOnce 應用程式供其他人部署 |Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3307fc124f50e8c9f73749293c36f53be36c5e3c
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252453"
---
# <a name="create-clickonce-applications-for-others-to-deploy"></a>建立 ClickOnce 應用程式供其他人部署
並非所有建立 ClickOnce 部署的開發人員都打算部署應用程式本身。 其中有許多隻是使用 ClickOnce 封裝其應用程式，然後將檔案交給客戶，例如大型公司。 客戶會成為負責在其網路上裝載應用程式的使用者。 本主題討論在3.5 版之前的 .NET Framework 版本中，這類部署固有的一些問題。 然後，它會描述使用 .NET Framework 3.5 中新的「使用資訊清單來信任」功能所提供的新解決方案。 最後，它會針對仍使用舊版 .NET Framework 的客戶，以建議的策略來建立 ClickOnce 部署。

## <a name="issues-involved-in-creating-deployments-for-customers"></a>建立客戶部署的相關問題
 當您打算提供部署給客戶時，會發生數個問題。 第一個問題會考慮程式碼簽署。 為了在網路上部署，ClickOnce 部署的部署資訊清單和應用程式資訊清單都必須以數位憑證簽署。 這會引發在簽署資訊清單時，是否要使用開發人員憑證或客戶憑證的問題。

 要使用哪一個憑證的問題是很重要的，因為 ClickOnce 應用程式的身分識別是以部署資訊清單的數位簽章為基礎。 如果開發人員簽署部署資訊清單，當客戶是大型公司，且公司的多個部門部署了自訂版本的應用程式時，可能會導致衝突。

 例如，假設「艾德公司」有財務部門和「人力資源部門」。 這兩個部門都是由 Microsoft Corporation 授權的 ClickOnce 應用程式，它會從 SQL database 中儲存的資料產生報告。 Microsoft 會針對其資料自訂的應用程式版本提供每個部門。 如果應用程式是使用相同的 Authenticode 憑證來簽署，則嘗試使用這兩個應用程式的使用者會發生錯誤，因為 ClickOnce 會將第二個應用程式視為與第一個相同。 在此情況下，客戶可能會遇到無法預期和不想要的副作用，其中包括應用程式儲存在本機的任何資料遺失。

 與程式碼簽署相關的其他問題是`deploymentProvider`部署資訊清單中的專案，它會告訴 ClickOnce 在何處尋找應用程式更新。 此元素必須先加入至部署資訊清單，才能簽署它。 如果之後加入這個元素，則必須重新簽署部署資訊清單。

### <a name="require-the-customer-to-sign-the-deployment-manifest"></a>要求客戶簽署部署資訊清單
 這種非唯一部署問題的解決方法之一，就是讓開發人員簽署應用程式資訊清單，而客戶會簽署部署資訊清單。 雖然這種方法可行，但還是會引進其他問題。 因為 Authenticode 憑證必須保留受保護的資產，所以客戶不能只將憑證提供給開發人員來簽署部署。 雖然客戶可以使用 .NET Framework SDK 免費提供的工具來簽署部署資訊清單，但這可能需要比客戶願意或無法提供更多的技術知識。 在這種情況下，開發人員通常會建立應用程式、網站或其他機制，讓客戶可以提交其應用程式版本進行簽署。

### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>客戶對 ClickOnce 應用程式安全性的影響
 即使開發人員和客戶同意客戶應該簽署應用程式資訊清單，這也會引發其他會導致應用程式身分識別的問題，特別是當它適用于信任的應用程式部署時。 （如需這項功能的詳細資訊，請參閱[信任的應用程式部署總覽](../deployment/trusted-application-deployment-overview.md)）。假設「艾德公司」想要設定其用戶端電腦，讓 Microsoft Corporation 提供給他們的任何應用程式都能以完全信任的方式執行。 如果「艾德公司」登入部署資訊清單，則 ClickOnce 會使用「艾德工作」的安全性簽章來判斷應用程式的信任層級。

## <a name="create-customer-deployments-by-using-application-manifest-for-trust"></a>使用應用程式資訊清單進行信任來建立客戶部署
 .NET Framework 3.5 中的 ClickOnce 包含一項新功能，可為開發人員和客戶提供如何簽署資訊清單之案例的新解決方案。 ClickOnce 應用程式資訊清單支援名為`<useManifestForTrust>`的新專案，可讓開發人員表示應用程式資訊清單的數位簽章應該用來進行信任決策。 開發人員使用 ClickOnce 封裝工具（例如*mage.exe*、 *mageui.exe*和 Visual Studio）將此元素包含在應用程式資訊清單中，以及將其發行者名稱和應用程式名稱內嵌在資訊清單中。

 使用`<useManifestForTrust>`時，不需要使用憑證授權單位單位所發行的 Authenticode 憑證來簽署部署資訊清單。 相反地，它可以使用所謂的自我簽署憑證來簽署。 自我簽署憑證是由客戶或開發人員使用標準的 .NET Framework SDK 工具所產生，然後使用標準的 ClickOnce 部署工具套用至部署資訊清單。 如需詳細資訊，請參閱[MakeCert](/windows/desktop/SecCrypto/makecert)。

 針對部署資訊清單使用自我簽署憑證有數個優點。 藉由排除客戶取得或建立自己的 Authenticode 憑證的需求， `<useManifestForTrust>`可簡化客戶的部署，同時允許開發人員在應用程式上維護自己的商標身分識別。 結果是一組較安全且具有唯一應用程式身分識別的已簽署部署。 這可避免將相同的應用程式部署至多個客戶時可能發生的衝突。

 如需如何使用`<useManifestForTrust>`啟用建立 ClickOnce 部署的逐步解說資訊，請參閱[逐步解說：手動部署不需要重新簽署而且會保留商標資訊](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)的 ClickOnce 應用程式。

### <a name="how-application-manifest-for-trust-works-at-run-time"></a>應用程式資訊清單在執行時間的運作方式
 若要進一步瞭解如何在執行時間使用應用程式資訊清單來取得信任，請考慮下列範例。 以 .NET Framework 3.5 為目標的 ClickOnce 應用程式是由 Microsoft 所建立。 應用程式資訊清單會`<useManifestForTrust>`使用元素，並由 Microsoft 簽署。 「艾德作品」會使用自我簽署憑證來簽署部署資訊清單。 「艾德公司」用戶端會設定成信任由 Microsoft 簽署的任何應用程式。

 當使用者按一下部署資訊清單的連結時，ClickOnce 會將應用程式安裝在使用者的電腦上。 憑證和部署資訊會針對用戶端電腦上的 ClickOnce 唯一識別應用程式。 如果使用者嘗試從不同的位置重新安裝相同的應用程式，則 ClickOnce 可以使用此身分識別來判斷應用程式是否已存在於用戶端上。

 接下來，ClickOnce 會檢查用來簽署應用程式資訊清單的 Authenticode 憑證，這會決定 ClickOnce 將授與的信任層級。 由於「艾德公司」已將其用戶端設定為信任由 Microsoft 簽署的任何應用程式，因此此 ClickOnce 應用程式會被授與完全信任。 如需詳細資訊，請參閱[受信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)。

## <a name="create-customer-deployments-for-earlier-versions"></a>為較早的版本建立客戶部署
 如果開發人員將 ClickOnce 應用程式部署到使用舊版 .NET Framework 的客戶，該怎麼辦？ 下列各節摘要說明數個建議的解決方案，以及各自的優點和缺點。

### <a name="sign-deployments-on-behalf-of-customer"></a>代表客戶簽署部署
 其中一個可能的部署策略，是讓開發人員使用客戶自己的私密金鑰，建立代表客戶簽署部署的機制。 這可防止開發人員管理私密金鑰或多個部署封裝。 開發人員只需為每個客戶提供相同的部署。 客戶可以使用簽署服務，針對其環境進行自訂。

 這種方法有一個缺點，就是執行它所需的時間和費用。 雖然這類服務可以使用 .NET Framework SDK 中提供的工具來建立，但它會在產品生命週期中增加更多開發時間。

 如本主題稍早所述，另一個缺點是每個客戶的應用程式版本都會有相同的應用程式識別，而這可能會導致衝突。 如果這是問題，開發人員可以變更產生部署資訊清單時所使用的名稱欄位，為每個應用程式提供唯一的名稱。 這會為每個版本的應用程式建立個別的身分識別，並排除任何可能的身分識別衝突。 這個欄位對應于 mage.exe `-Name`的引數，以及 mageui.exe 中 [**名稱**] 索引標籤上的 [**名稱**] 欄位。

 例如，假設開發人員已建立名為 Application1 的應用程式。 開發人員不會建立將 Name 欄位設定為 Application1 的單一部署，而是使用此名稱的客戶特定變化來建立數個部署，例如 Application1-CustomerA、Application1-CustomerB 等等。

### <a name="deploy-using-a-setup-package"></a>使用安裝套件進行部署
 第二種可能的部署策略是產生 Microsoft 安裝專案，以執行 ClickOnce 應用程式的初始部署。 這可以使用下列數種不同的格式之一提供：作為 MSI 部署，做為安裝程式可執行檔（。EXE），或做為封包（.cab）檔案連同批次腳本。

 開發人員可以使用這項技術，為客戶提供一個部署，其中包含應用程式檔、應用程式資訊清單，以及做為範本的部署資訊清單。 客戶會執行安裝程式，它會提示他們輸入部署 URL （使用者將安裝 ClickOnce 應用程式的伺服器或檔案共用位置），以及數位憑證。 安裝應用程式也可以選擇提示其他 ClickOnce 設定選項，例如更新檢查間隔。 收集這項資訊之後，安裝程式會產生實際的部署資訊清單、簽署它，然後將 ClickOnce 應用程式發佈到指定的伺服器位置。

 有三種方式可讓客戶在此情況下簽署部署資訊清單：

1. 客戶可以使用憑證授權單位單位（CA）所發行的有效憑證。

2. 這種方法的變化，客戶可以選擇使用自我簽署憑證來簽署其部署資訊清單。 其缺點是，當詢問使用者是否安裝時，應用程式會顯示「未知的發行者」字樣。 不過，它的好處是，它可以避免較小的客戶必須花費憑證授權單位單位所發行的憑證所需的時間和金錢。

3. 最後，開發人員可以在安裝套件中包含自己的自我簽署憑證。 這會引進本主題稍早所討論之應用程式識別的潛在問題。

   安裝部署專案方法的缺點是建立自訂部署應用程式所需的時間和費用。

### <a name="have-customer-generate-deployment-manifest"></a>讓客戶產生部署資訊清單
 第三種可能的部署策略是只將應用程式檔和應用程式資訊清單交給客戶。 在此案例中，客戶會負責使用 .NET Framework SDK 來產生及簽署部署資訊清單。

 此方法的缺點是需要客戶安裝 .NET Framework SDK 工具，並讓開發人員或系統管理員熟練使用它們。 有些客戶可能會要求解決方案，而不需要對其進行任何技術工作。

## <a name="see-also"></a>另請參閱
- [部署 ClickOnce 應用程式以進行測試和實際執行伺服器，而不需要簽署](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)
- [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [逐步解說：手動部署不需要重新簽署而且會保留商標資訊的 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)