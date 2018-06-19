---
title: 授與信任給 Office 方案
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cfce58ca765e7e3710ecb55a1c84c09f0ee14f52
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447241"
---
# <a name="grant-trust-to-office-solutions"></a>授與信任給 Office 方案
  授與信任給 Office 方案表示修改每個目標電腦的安全性原則信任方案組件、 應用程式資訊清單中，部署資訊清單和文件。 由您或使用者時，可以授信任 Office 方案。  
  
 您可以簽署應用程式和部署資訊清單，以授與完全信任給 Office 方案。  
  
 使用者可以讓授與信任給 Office 方案中的信任決策[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> 信任方案所簽署應用程式和部署資訊清單  
 所有應用程式和部署的 Office 解決方案必須使用識別發行者的憑證來簽署資訊清單。 憑證提供的基礎進行信任決策。  
  
 為您建立暫時憑證，並在建置階段授與信任，所以在偵錯時，方案才能執行。 如果您發行的暫時憑證簽署的解決方案，將會提示使用者進行信任決策。  
  
 如果您簽署方案的已知且受信任的憑證，而不提示使用者進行信任決策會自動安裝方案。 如需如何取得簽署憑證的詳細資訊，請參閱[ClickOnce 和 Authenticode](/visualstudio/deployment/clickonce-and-authenticode)。 取得憑證之後，憑證必須明確受到以將其加入受信任的發行者清單。 如需詳細資訊，請參閱[如何： 新增信任的發行者至 ClickOnce 應用程式的用戶端電腦](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications)。  
  
 如果開發人員簽署方案的暫時憑證，系統管理員可以重新已知且受信任的憑證與自訂使用簽署資訊清單產生和編輯工具 (*mage.exe*)，這是其中一個Microsoft.NET Framework 工具。 如需簽署方案的詳細資訊，請參閱[如何： 簽署 Office 方案](../vsto/how-to-sign-office-solutions.md)和[如何： 簽署應用程式和部署資訊清單](/visualstudio/ide/how-to-sign-application-and-deployment-manifests)。  
  
##  <a name="TrustPrompt"></a>使用 ClickOnce 信任提示，信任方案  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 會提示使用者信任方案的憑證沒有整個組織的原則，進行信任決策。 如果終端使用者授與信任給方案，就會建立內含清單項目包含 URL 和公開金鑰，來儲存此信任決策。 當執行信任的自訂更新版本中，不會再次提示使用者。  
  
 系統管理員可以停用[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示，或需要提示則只會針對解決方案使用 Authenticode 憑證所簽署。 如需如何變更這些設定的 MyComputer、 近端內部網路、 網際網路、 TrustedSites 和 UntrustedSites 區域的詳細資訊，請參閱[How to： 設定 ClickOnce 信任提示行為](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior)。  
  
## <a name="see-also"></a>另請參閱  
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [將信任授與文件](../vsto/granting-trust-to-documents.md)   
 [疑難排解 Office 方案安全性](../vsto/troubleshooting-office-solution-security.md)   
 [指定 Office 方案的安全性考量](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  