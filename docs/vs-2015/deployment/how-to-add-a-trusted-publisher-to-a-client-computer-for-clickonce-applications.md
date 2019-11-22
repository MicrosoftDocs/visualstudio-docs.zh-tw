---
title: 如何：將受信任的發行者新增至 ClickOnce 應用程式的用戶端電腦 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b535737860b846aadecb6b73b4bd26659db37b1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74289704"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>如何：新增信任發行者至 ClickOnce 應用程式的用戶端電腦
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用信任的應用程式部署來設定用戶端電腦，以較高的信任等級執行 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式，而不提示使用者。 下列程序示範如何使用命令列工具 CertMgr.exe 將發行者的憑證新增至用戶端電腦上的受信任發行者存放區。  
  
 您使用的命令會根據發行憑證的憑證授權單位 (CA) 是否為用戶端信任的根而略有不同。 如果 Windows 用戶端電腦是網域的一部分，則會以清單形式包含視為受信任根的 CA。 系統管理員通常會設定此清單。 如果您的憑證是由其中一個受信任根所發出，或由鏈結至其中一個受信任根的 CA 所發出，則可以將憑證新增至用戶端的受信任根存放區。 另一方面，如果您的憑證不是由其中一個受信任根所發出，則必須將憑證新增至用戶端的受信任根存放區和受信任發行者存放區。  
  
> [!NOTE]
> 您必須透過這種方式在下列用戶端電腦上新增憑證：要部署需要更高權限之 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式的用戶端電腦。 手動或透過部署至用戶端的應用程式，即可新增憑證。 您只需要設定這些電腦一次，之後，就可以部署使用相同憑證簽署之任意數目的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式。  
  
 您也可以使用 <xref:System.Security.Cryptography.X509Certificates.X509Store> 類別，以程式設計方式將憑證新增至存放區。  
  
 如需信任的應用程式部署的概觀，請參閱 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>將憑證新增至受信任根下的受信任發行者存放區  
  
1. 從 CA 取得數位憑證。  
  
2. 將憑證匯出成 Base64 X.509 (.cer) 格式。 如需憑證格式的詳細資訊，請參閱 [匯出憑證](https://go.microsoft.com/fwlink/?LinkId=164793)。  
  
3. 從用戶端電腦的命令提示字元中，執行下列命令：  
  
     **certmgr.exe -add certificate.cer -c -s -r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>將憑證新增至不同根下的受信任發行者存放區  
  
1. 從 CA 取得數位憑證。  
  
2. 將憑證匯出成 Base64 X.509 (.cer) 格式。 如需憑證格式的詳細資訊，請參閱 [匯出憑證](https://go.microsoft.com/fwlink/?LinkId=164793)。  
  
3. 從用戶端電腦的命令提示字元中，執行下列命令：  
  
     **certmgr.exe -add good.cer -c -s -r localMachine Root**  
  
     **certmgr.exe -add good.cer -c -s -r localMachine TrustedPublisher**  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)   
 [受信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)   
 [如何：啟用 ClickOnce 安全性設定](../deployment/how-to-enable-clickonce-security-settings.md)   
 [How to: Set a Security Zone for a ClickOnce Application](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [How to: Set Custom Permissions for a ClickOnce Application](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [How to: Debug a ClickOnce Application with Restricted Permissions](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [如何：新增信任發行者至 ClickOnce 應用程式的用戶端電腦](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [如何：設定 ClickOnce 信任提示行為](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
