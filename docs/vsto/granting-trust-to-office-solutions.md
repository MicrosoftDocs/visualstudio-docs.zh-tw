---
title: 授與信任給 Office 方案
description: 若要授與信任給 Office 方案，表示修改每部目的電腦的安全性原則，以信任方案元件、部署資訊清單和檔。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f0b81c034ed0f8934da378dc214191d3be1f4506
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848322"
---
# <a name="grant-trust-to-office-solutions"></a>授與信任給 Office 方案
  授與信任給 Office 方案表示修改每部目的電腦的安全性原則，以信任方案元件、應用程式資訊清單、部署資訊清單和檔。 您或終端使用者可以授與信任給 Office 方案。

 您可以簽署應用程式和部署資訊清單，將完全信任授與 Office 方案。

 終端使用者可以在信任提示中做出信任決策，以授與信任給 Office 方案 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a> 簽署應用程式和部署資訊清單，以信任方案
 Office 方案的所有應用程式和部署資訊清單都必須使用可識別發行者的憑證來簽署。 憑證提供進行信任決策的基礎。

 系統會為您建立暫時憑證，並在組建階段授與信任，讓解決方案在您進行調試時執行。 如果您發行以暫時憑證簽署的方案，系統將會提示終端使用者進行信任決策。

 如果您使用已知且受信任的憑證來簽署解決方案，則會自動安裝解決方案，而不會提示使用者進行信任決策。 如需如何取得憑證以進行簽署的詳細資訊，請參閱 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)。 取得憑證之後，您必須將憑證新增至 [信任的發行者] 清單，以明確地信任該憑證。 如需詳細資訊，請參閱 [如何：將信任的發行者新增至 ClickOnce 應用程式的用戶端電腦](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)。

 如果開發人員使用暫時性憑證來簽署解決方案，則系統管理員可以使用資訊清單產生和編輯工具 (*mage.exe*) （這是其中一個 Microsoft .NET Framework 工具），以使用已知且受信任的憑證重新簽署自訂。 如需簽署解決方案的詳細資訊，請參閱 [如何：簽署 Office 方案](../vsto/how-to-sign-office-solutions.md) 和 [如何：簽署應用程式和部署資訊清單](../ide/how-to-sign-application-and-deployment-manifests.md)。

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>使用 ClickOnce 信任提示來信任方案
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 如果沒有信任解決方案憑證的全組織原則，則提示終端使用者進行信任決策。 如果終端使用者授與信任給方案，則會建立包含 URL 和公開金鑰的內含清單專案，以儲存此信任決策。 當您稍後執行受信任的自訂時，系統不會再次提示終端使用者。

 系統管理員可以停 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 用信任提示，或要求只針對使用 Authenticode 憑證簽署的解決方案進行提示。 如需如何針對 MyComputer、LocalIntranet、Internet、TrustedSites 和 UntrustedSites 區域變更這些設定的詳細資訊，請參閱 [如何：設定 ClickOnce 信任提示行為](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)。

## <a name="see-also"></a>另請參閱

- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [授與信任給檔](../vsto/granting-trust-to-documents.md)
- [針對 Office 方案安全性進行疑難排解](../vsto/troubleshooting-office-solution-security.md)
- [Office 方案的特定安全性考慮](../vsto/specific-security-considerations-for-office-solutions.md)