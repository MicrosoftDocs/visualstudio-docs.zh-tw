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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf7a68d5d3567305e4f70049d76a1c260ddecf25
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410013"
---
# <a name="grant-trust-to-office-solutions"></a>授與信任給 Office 方案
  授與信任給 Office 方案，表示修改每部目的電腦的安全性原則，以信任解決方案元件、應用程式資訊清單、部署資訊清單和檔。 您或使用者可以將信任授與 Office 方案。

 您可以簽署應用程式和部署資訊清單，將完全信任授與 Office 方案。

 使用者可以藉由在 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示中做出信任決策，授與信任給 Office 方案。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="Signing"></a>簽署應用程式和部署資訊清單以信任解決方案
 Office 方案的所有應用程式和部署資訊清單都必須使用可識別發行者的憑證來簽署。 憑證提供了一種基礎來進行信任決策。

 系統會為您建立暫時憑證，並在組建階段授與信任，讓解決方案在您進行調試時執行。 如果您發行使用暫時憑證簽署的解決方案，系統會提示使用者進行信任決策。

 如果您使用已知且受信任的憑證來簽署解決方案，將會自動安裝解決方案，而不會提示使用者進行信任決策。 如需如何取得憑證以進行簽署的詳細資訊，請參閱[ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)。 取得憑證之後，您必須將憑證新增至信任的發行者清單，以明確地信任該憑證。 如需詳細資訊，請參閱[如何：將信任的發行者新增至 ClickOnce 應用程式的用戶端電腦](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)。

 如果開發人員使用暫時憑證簽署解決方案，則系統管理員可以使用資訊清單產生和編輯工具（*mage.exe*）（這是其中一個 Microsoft .NET Framework 工具），以已知且受信任的憑證重新簽署自訂。 如需簽署解決方案的詳細資訊，請參閱[如何：簽署 Office 方案](../vsto/how-to-sign-office-solutions.md)和[如何：簽署應用程式和部署資訊清單](../ide/how-to-sign-application-and-deployment-manifests.md)。

## <a name="TrustPrompt"></a>使用 ClickOnce 信任提示來信任解決方案
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 會在沒有信任解決方案憑證的全組織原則時，提示使用者進行信任決策。 如果使用者將信任授與方案，則會建立包含 URL 和公開金鑰的內含清單專案，以儲存這項信任決策。 稍後執行受信任的自訂時，系統不會再次提示使用者。

 系統管理員可以停用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示，或要求只針對使用 Authenticode 憑證簽署的解決方案進行提示。 如需如何變更 MyComputer、LocalIntranet、Internet、TrustedSites 和 UntrustedSites 區域的這些設定的詳細資訊，請參閱[如何：設定 ClickOnce 信任提示行為](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)。

## <a name="see-also"></a>另請參閱

- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [授與信任給檔](../vsto/granting-trust-to-documents.md)
- [針對 Office 方案安全性進行疑難排解](../vsto/troubleshooting-office-solution-security.md)
- [Office 方案的特定安全性考慮](../vsto/specific-security-considerations-for-office-solutions.md)