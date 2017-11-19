---
title: "授與信任給 Office 方案 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
ms.assetid: 6c33e614-d367-4556-9e76-0f302ad0f929
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: da7f4695bc817a66761c579b4c5af85b59ee041f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="granting-trust-to-office-solutions"></a>授與信任給 Office 方案
  授與信任給 Office 方案表示修改每個目標的電腦可以信任方案組件、 應用程式資訊清單中，部署資訊清單和文件的安全性原則。 由您或使用者時，可以授信任 Office 方案。  
  
 您可以簽署應用程式和部署資訊清單，以授與完全信任給 Office 方案。  
  
 使用者可以讓授與信任給 Office 方案中的信任決策[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a>信任方案透過簽署應用程式和部署資訊清單  
 所有應用程式和部署的 Office 解決方案必須使用識別發行者的憑證來簽署資訊清單。 憑證提供的基礎進行信任決策。  
  
 為您建立暫時憑證，並在建置階段授與信任，所以在偵錯時，方案才能執行。 如果您發行的暫時憑證簽署的解決方案，將會提示使用者進行信任決策。  
  
 如果您簽署方案的已知且受信任的憑證，而不提示使用者進行信任決策會自動安裝方案。 如需如何取得簽署憑證的詳細資訊，請參閱[ClickOnce 和 Authenticode](/visualstudio/deployment/clickonce-and-authenticode)。 取得憑證之後，憑證必須明確受到以將其加入受信任的發行者清單。 如需詳細資訊，請參閱[如何： 新增 ClickOnce 應用程式的用戶端電腦受信任的發行者](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications)。  
  
 如果開發人員簽署方案的暫時憑證，系統管理員可以重新使用資訊清單產生和編輯工具 (mage.exe)，也就是其中一種 Microsoft.NET Framework 工具簽署已知且受信任憑證的自訂。 如需簽署方案的詳細資訊，請參閱[如何： 簽署 Office 方案](../vsto/how-to-sign-office-solutions.md)和[如何： 簽署應用程式和部署資訊清單](/visualstudio/ide/how-to-sign-application-and-deployment-manifests)。  
  
##  <a name="TrustPrompt"></a>使用 ClickOnce 信任提示，信任方案  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]會提示使用者信任方案的憑證沒有整個組織的原則，進行信任決策。 如果終端使用者授與信任給方案，就會建立內含清單項目包含 URL 和公開金鑰，來儲存此信任決策。 當執行信任的自訂更新版本中，不會再次提示使用者。  
  
 系統管理員可以停用[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示，或需要提示則只會針對解決方案使用 Authenticode 憑證所簽署。 如需如何變更這些設定的 MyComputer、 近端內部網路、 網際網路、 TrustedSites 和 UntrustedSites 區域的詳細資訊，請參閱[How to： 設定 ClickOnce 信任提示行為](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior)。  
  
## <a name="see-also"></a>另請參閱  
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [授與信任給文件](../vsto/granting-trust-to-documents.md)   
 [Office 方案安全性疑難排解](../vsto/troubleshooting-office-solution-security.md)   
 [指定 Office 方案的安全性考量](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  