---
title: 授與信任給 Office 方案
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1acc6f73dd52bacdfd62aff3b2da62e559c4fda6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890465"
---
# <a name="grant-trust-to-office-solutions"></a>授與信任給 Office 方案
  將信任授與為 Office 方案表示修改每個目標電腦的安全性原則信任方案組件、 應用程式資訊清單、 部署資訊清單和文件。 信任可以由您或使用者授與至 Office 方案之用。

 您可以簽署應用程式和部署資訊清單，以授與完全信任給 Office 方案。

 使用者可以授與信任給 Office 方案進行信任決策中的[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

##  <a name="Signing"></a> 藉由簽署應用程式和部署資訊清單信任方案
 所有的應用程式和部署的 Office 解決方案必須使用識別發行者的憑證來簽署資訊清單。 憑證提供的基礎進行信任決策。

 是為您建立的暫時憑證，並在建置階段授與信任，因此在偵錯時，會執行方案。 如果您發佈使用的暫時憑證簽署的解決方案時，您就會提示使用者進行信任決策。

 如果您登入解決方案中使用已知且受信任的憑證，而不提示使用者進行信任決策會自動安裝方案。 如需如何取得憑證來簽署的詳細資訊，請參閱[ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)。 取得憑證之後，憑證必須明確信任新增至信任的發行者清單。 如需詳細資訊，請參閱[＜How to：新增信任的發行者至 ClickOnce 應用程式的用戶端電腦](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)。

 如果開發人員登入解決方案中使用的暫時憑證，系統管理員可以重新已知且受信任的憑證與自訂使用簽署資訊清單產生和編輯工具 (*mage.exe*)，而這也是Microsoft.NET Framework 工具。 如需有關如何簽署方案的詳細資訊，請參閱[How to:簽署 Office 方案](../vsto/how-to-sign-office-solutions.md)和[How to:簽署應用程式和部署資訊清單](../ide/how-to-sign-application-and-deployment-manifests.md)。

##  <a name="TrustPrompt"></a>使用 ClickOnce 信任提示信任方案
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 會提示使用者進行信任決策，如果沒有整個組織的原則，信任方案的憑證。 如果使用者授與信任給方案，內含清單項目會建立包含 URL 和公開金鑰，來儲存此信任決策。 稍後執行的受信任的自訂時，使用者不會提示一次。

 系統管理員可以停用[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示，或需要提示字元，則只會針對會使用 Authenticode 憑證簽署的解決方案。 如需如何變更這些設定的 MyComputer、 近端內部網路、 網際網路、 TrustedSites 和 UntrustedSites 區域的詳細資訊，請參閱[How to:設定 ClickOnce 信任提示行為](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)。

## <a name="see-also"></a>另請參閱

- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [將信任授與文件](../vsto/granting-trust-to-documents.md)
- [針對 Office 方案安全性進行疑難排解](../vsto/troubleshooting-office-solution-security.md)
- [指定 Office 方案的安全性考量](../vsto/specific-security-considerations-for-office-solutions.md)