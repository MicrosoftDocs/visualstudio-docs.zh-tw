---
title: HOW TO：加入用戶端電腦中的受信任的發行者，ClickOnce 應用程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 295e2e774d2f6221b9064449e33c6777072aa4d2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55014571"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>HOW TO：將信任發行者新增到 ClickOnce 應用程式的用戶端電腦
您可以使用信任的應用程式部署來設定用戶端電腦，以較高的信任等級執行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，而不提示使用者。 下列程序示範如何使用命令列工具 CertMgr.exe 將發行者的憑證新增至用戶端電腦上的受信任發行者存放區。  
  
 您使用的命令會根據發行憑證的憑證授權單位 (CA) 是否為用戶端信任的根而略有不同。 如果 Windows 用戶端電腦是網域的一部分，則會以清單形式包含視為受信任根的 CA。 系統管理員通常會設定此清單。 如果您的憑證是由其中一個受信任根所發出，或由鏈結至其中一個受信任根的 CA 所發出，則可以將憑證新增至用戶端的受信任根存放區。 另一方面，如果您的憑證不是由其中一個受信任根所發出，則必須將憑證新增至用戶端的受信任根存放區和受信任發行者存放區。  
  
> [!NOTE]
>  您必須透過這種方式在下列用戶端電腦上新增憑證：要部署需要更高權限之 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的用戶端電腦。 手動或透過部署至用戶端的應用程式，即可新增憑證。 您只需要設定這些電腦一次，之後，就可以部署使用相同憑證簽署之任意數目的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。  
  
 您也可以使用 <xref:System.Security.Cryptography.X509Certificates.X509Store> 類別，以程式設計方式將憑證新增至存放區。  
  
 如需信任的應用程式部署概觀，請參閱[受信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)。  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>將憑證新增至受信任根下的受信任發行者存放區  
  
1.  從 CA 取得數位憑證。  
  
2.  將憑證匯出成 Base64 X.509 (*.cer*) 格式。 如需憑證格式的詳細資訊，請參閱 [Export a certificate](http://go.microsoft.com/fwlink/?LinkId=164793) (匯出憑證)。  
  
3.  從用戶端電腦的命令提示字元中，執行下列命令：  
  
     **certmgr.exe -add certificate.cer -c -s -r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>將憑證新增至不同根下的受信任發行者存放區  
  
1.  從 CA 取得數位憑證。  
  
2.  將憑證匯出成 Base64 X.509 (*.cer*) 格式。 如需憑證格式的詳細資訊，請參閱 [匯出憑證](http://go.microsoft.com/fwlink/?LinkId=164793)。  
  
3.  從用戶端電腦的命令提示字元中，執行下列命令：  
  
     **certmgr.exe -add good.cer -c -s -r localMachine Root**  
  
     **certmgr.exe -add good.cer -c -s -r localMachine TrustedPublisher**  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)   
 [信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)   
 [如何：啟用 ClickOnce 安全性設定](../deployment/how-to-enable-clickonce-security-settings.md)   
 [如何：為 ClickOnce 應用程式設定安全性區域](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [如何：為 ClickOnce 應用程式設定自訂權限](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [如何：以限制的權限對 ClickOnce 應用程式進行偵錯](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [如何：將信任的發行者新增至 ClickOnce 應用程式的用戶端電腦](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [如何：設定 ClickOnce 信任提示行為](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)