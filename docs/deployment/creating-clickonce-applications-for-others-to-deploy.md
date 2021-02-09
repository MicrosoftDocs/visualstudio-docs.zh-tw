---
title: 建立 ClickOnce 應用程式供其他人部署 |Microsoft Docs
description: 瞭解在 .NET Framework 3.5 與舊版 .NET Framework 中開發的客戶託管 ClickOnce 應用程式。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9554cad786669ae4aa3b9aa84ecd6b996ee196f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888468"
---
# <a name="create-clickonce-applications-for-others-to-deploy"></a>建立 ClickOnce 應用程式供其他人部署
並非所有建立 ClickOnce 部署的開發人員都計畫自行部署應用程式。 其中有許多是使用 ClickOnce 來封裝應用程式，然後將檔案交給客戶，例如大型公司。 客戶會成為負責在其網路上裝載應用程式的人。 本主題將討論在3.5 版之前的 .NET Framework 版本中，這類部署中固有的一些問題。 接著，它會描述在 .NET Framework 3.5 中使用新的「使用資訊清單進行信任」功能所提供的新解決方案。 最後，它會針對仍在使用舊版 .NET Framework 的客戶建立 ClickOnce 部署的建議策略。

## <a name="issues-involved-in-creating-deployments-for-customers"></a>為客戶建立部署的相關問題
 當您打算提供部署給客戶時，會發生數個問題。 第一個問題是程式碼簽署問題。 為了要在網路上部署，ClickOnce 部署的部署資訊清單和應用程式資訊清單都必須使用數位憑證來簽署。 這會引發問題，指出是否要在簽署資訊清單時使用開發人員的憑證或客戶的憑證。

 要使用哪一個憑證的問題很重要，因為 ClickOnce 應用程式的身分識別是以部署資訊清單的數位簽章為基礎。 如果開發人員簽署部署資訊清單，如果客戶是大型公司，而且公司有多個部門部署自訂的應用程式版本，則可能會導致衝突。

 例如，假設艾德公司有財務部門和人力資源部門。 這兩個部門都會從 Microsoft Corporation 中授權 ClickOnce 應用程式，以從 SQL 資料庫中儲存的資料產生報表。 Microsoft 會為每個部門提供針對其資料自訂的應用程式版本。 如果應用程式是使用相同的 Authenticode 憑證簽署，則嘗試使用這兩個應用程式的使用者將會發生錯誤，因為 ClickOnce 會將第二個應用程式視為與第一個應用程式相同。 在此情況下，客戶可能會遇到無法預期和不必要的副作用，包括應用程式儲存在本機的任何資料遺失。

 與程式碼簽署相關的其他問題是 `deploymentProvider` 部署資訊清單中的元素，它會告知 ClickOnce 要在哪裡尋找應用程式更新。 在簽署之前，必須先將這個專案加入至部署資訊清單。 如果之後加入此元素，則必須重新簽署部署資訊清單。

### <a name="require-the-customer-to-sign-the-deployment-manifest"></a>要求客戶簽署部署資訊清單
 這種非唯一部署問題的解決方法之一，是讓開發人員簽署應用程式資訊清單，並讓客戶簽署部署資訊清單。 雖然這個方法可行，但會造成其他問題。 由於 Authenticode 憑證必須維持受保護的資產，因此客戶無法只將憑證提供給開發人員來簽署部署。 雖然客戶可以使用 .NET Framework SDK 免費提供的工具來簽署部署資訊清單，但這可能需要比客戶願意或提供更多的技術知識。 在這種情況下，開發人員通常會建立應用程式、網站或其他機制，讓客戶可以提交應用程式的版本進行簽署。

### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>客戶簽署 ClickOnce 應用程式安全性的影響
 即使開發人員和客戶同意客戶應該簽署應用程式資訊清單，這也會引發其他問題，這些問題會在應用程式的身分識別範圍外，特別是當它適用于受信任的應用程式部署時。  (如需這項功能的詳細資訊，請參閱 [信任的應用程式部署總覽](../deployment/trusted-application-deployment-overview.md)。 ) 說，「艾德作品」想要設定其用戶端電腦，讓 Microsoft Corporation 以完全信任的方式執行提供的任何應用程式。 如果「艾德作品」會簽署部署資訊清單，則 ClickOnce 會使用「艾德公司」的安全性簽章來判斷應用程式的信任層級。

## <a name="create-customer-deployments-by-using-application-manifest-for-trust"></a>使用應用程式資訊清單進行信任以建立客戶部署
 .NET Framework 3.5 中的 ClickOnce 包含新的功能，可為開發人員和客戶提供新的解決方案，以瞭解如何簽署資訊清單的案例。 ClickOnce 應用程式資訊清單支援名為的新專案 `<useManifestForTrust>` ，可讓開發人員表示應用程式資訊清單的數位簽章是應該用來進行信任決策的專案。 開發人員使用 ClickOnce 封裝工具（例如 *Mage.exe*、 *MageUI.exe* 和 Visual Studio）將此專案包含在應用程式資訊清單中，以及在資訊清單中內嵌其發行者名稱和應用程式名稱。

 使用時 `<useManifestForTrust>` ，不需要使用憑證授權單位單位所發行的 Authenticode 憑證來簽署部署資訊清單。 相反地，您可以使用所謂的自我簽署憑證來簽署。 自我簽署的憑證是由客戶或開發人員使用標準 .NET Framework SDK 工具產生，然後使用標準 ClickOnce 部署工具套用至部署資訊清單。 如需詳細資訊，請參閱 [MakeCert](/windows/desktop/SecCrypto/makecert)。

 使用適用于部署資訊清單的自我簽署憑證，會帶來幾項優點。 藉由免除客戶取得或建立自己的 Authenticode 憑證的需求，可 `<useManifestForTrust>` 簡化客戶的部署，同時讓開發人員在應用程式上維護自己的商標身分識別。 結果是一組更安全且具有唯一應用程式身分識別的已簽署部署。 這可避免將相同的應用程式部署到多個客戶時可能發生的衝突。

 如需有關如何建立已啟用之 ClickOnce 部署的逐步資訊 `<useManifestForTrust>` ，請參閱逐步解說 [：手動部署不需要重新簽署的 clickonce 應用程式，並保留商標資訊](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)。

### <a name="how-application-manifest-for-trust-works-at-run-time"></a>應用程式資訊清單 for trust 在執行時間的運作方式
 若要深入瞭解使用應用程式資訊清單 for trust 在執行時間的運作方式，請考慮下列範例。 以 .NET Framework 3.5 為目標的 ClickOnce 應用程式是由 Microsoft 所建立。 應用程式資訊清單 `<useManifestForTrust>` 會使用元素，並由 Microsoft 簽署。 「艾德作品」會使用自我簽署憑證來簽署部署資訊清單。 [艾德公司] 用戶端設定為信任任何由 Microsoft 簽署的應用程式。

 當使用者按一下部署資訊清單的連結時，ClickOnce 會將應用程式安裝在使用者的電腦上。 憑證和部署資訊會在用戶端電腦上將應用程式唯一識別為 ClickOnce。 如果使用者嘗試從不同的位置再次安裝相同的應用程式，則 ClickOnce 可以使用此身分識別來判斷應用程式是否已存在於用戶端上。

 接下來，ClickOnce 會檢查用來簽署應用程式資訊清單的 Authenticode 憑證，以決定 ClickOnce 將授與的信任層級。 由於艾德公司已將其用戶端設定為信任任何由 Microsoft 簽署的應用程式，因此此 ClickOnce 應用程式會被授與完全信任。 如需詳細資訊，請參閱 [受信任的應用程式部署總覽](../deployment/trusted-application-deployment-overview.md)。

## <a name="create-customer-deployments-for-earlier-versions"></a>針對較舊的版本建立客戶部署
 如果開發人員將 ClickOnce 應用程式部署到使用舊版 .NET Framework 的客戶，該怎麼辦？ 下列各節摘要說明數個建議的解決方案，以及各自的優點和缺點。

### <a name="sign-deployments-on-behalf-of-customer"></a>代表客戶簽署部署
 其中一個可能的部署策略是讓開發人員使用客戶自己的私密金鑰來建立可代表其客戶簽署部署的機制。 這可防止開發人員管理私用金鑰或多個部署套件。 開發人員只會為每個客戶提供相同的部署。 客戶可透過使用簽署服務，自行針對其環境進行自訂。

 這種方法有一個缺點，就是執行此方法所需的時間和費用。 雖然這類服務可以使用 .NET Framework SDK 中提供的工具來建立，但它會在產品生命週期中增加更多開發時間。

 如本主題稍早所述，另一個缺點是每個客戶的應用程式版本都有相同的應用程式身分識別，這可能會導致衝突。 如果這是一項考慮，開發人員可以變更產生部署資訊清單時所使用的名稱欄位，為每個應用程式提供唯一的名稱。 這會為每個版本的應用程式建立個別的身分識別，並消除任何可能的身分識別衝突。 這個欄位會對應至 `-Name` Mage.exe 的引數，以及 MageUI.exe 之 [**名稱**] 索引標籤上的 [**名稱**] 欄位。

 例如，假設開發人員已建立名為 Application1 的應用程式。 開發人員可以使用此名稱的客戶專屬變化來建立數個部署，例如 Application1 CustomerA、Application1 CustomerB 等，而不是建立名稱欄位設定為 Application1 的單一部署。

### <a name="deploy-using-a-setup-package"></a>使用安裝套件進行部署
 第二種可能的部署策略是產生 Microsoft 安裝專案，以執行 ClickOnce 應用程式的初始部署。 您可以使用下列其中一種不同的格式來提供：作為 MSI 部署，做為安裝程式的可執行檔 (。EXE) ，或做為封包 ( .cab) 檔案和批次腳本。

 使用這項技術時，開發人員會為客戶提供包含應用程式檔、應用程式資訊清單和部署資訊清單的部署，作為範本。 客戶會執行安裝程式，它會提示他們輸入部署 URL (使用者將在其中安裝 ClickOnce 應用程式) 的伺服器或檔案共用位置，以及數位憑證。 安裝應用程式也可以選擇提示其他 ClickOnce 設定選項，例如更新檢查間隔。 收集這項資訊之後，安裝程式會產生實際的部署資訊清單、簽署它，然後將 ClickOnce 應用程式發佈至指定的伺服器位置。

 在此情況下，客戶可簽署部署資訊清單的方式有三種：

1. 客戶可以使用憑證授權單位單位所簽發的有效憑證 (CA) 。

2. 這種方法的變化是，客戶可以選擇使用自我簽署憑證來簽署其部署資訊清單。 缺點是，當詢問使用者是否要安裝時，應用程式會顯示「未知的發行者」字樣。 不過，它的好處是，它可防止較小型的客戶花時間和金錢，來取得憑證授權單位單位所發行的憑證。

3. 最後，開發人員可以在安裝套件中包含自己的自我簽署憑證。 這會介紹本主題稍早所討論的應用程式身分識別的潛在問題。

   設定部署專案方法的缺點是建立自訂部署應用程式所需的時間和費用。

### <a name="have-customer-generate-deployment-manifest"></a>讓客戶產生部署資訊清單
 第三個可能的部署策略是只將應用程式檔和應用程式資訊清單遞交給客戶。 在此案例中，客戶會負責使用 .NET Framework SDK 來產生和簽署部署資訊清單。

 這種方法的缺點是需要客戶安裝 .NET Framework SDK 工具，並讓開發人員或系統管理員有能力使用它們。 某些客戶可能會要求解決方案，但不需要對其進行任何技術工作。

## <a name="see-also"></a>另請參閱
- [針對測試和實際執行伺服器部署 ClickOnce 應用程式，而不需進行簽署](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)
- [Walkthrough: Manually deploying a ClickOnce application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) (逐步解說：手動部署 ClickOnce 應用程式)
- [Walkthrough: Manually deploying a ClickOnce application that does not require re-signing and that preserves branding information](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md) (逐步解說：手動部署無須重新簽署，且會保留商標資訊的 ClickOnce 應用程式)