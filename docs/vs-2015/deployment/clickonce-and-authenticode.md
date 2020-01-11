---
title: ClickOnce 和 Authenticode |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- .pfx files
- ClickOnce deployment, Authenticode
- Authenticode, ClickOnce
- ClickOnce deployment, certificates
- ClickOnce deployment, security
ms.assetid: ab5b6712-f32a-4e33-842f-e88ab4818ccf
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e48039a618f7e8eef7f2c6e9f097da87e37d0f5
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847780"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce 和 Authenticode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Authenticode * 是一項 Microsoft 技術，使用業界標準的密碼編譯，以驗證應用程式發行者真實性的數位憑證來簽署應用程式代碼。 使用 Authenticode 部署應用程式， [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 可以降低特洛伊木馬程式的風險。 特洛伊木馬程式是誤以為來自於已建立、可信任來源的合法程式，其實是惡意第三方的病毒或其他有害的程式。 使用數位憑證簽署 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署是選擇性的步驟，用以確認組件和檔案未遭竄改。  
  
 下列各節說明 Authenticode 使用的不同數位簽章類型、如何使用憑證授權單位 (CA) 驗證憑證、憑證的時間戳記角色，以及憑證可用的儲存方法。  
  
## <a name="authenticode-and-code-signing"></a>Authenticode 與程式碼簽署  
 *數位憑證* 是包含密碼編譯公用/私密金鑰組的檔案，以及描述憑證發行對象與憑證發行單位的發行者中繼資料。  
  
 Authenticode 憑證有各種類型。 每種都有專門針對的簽章類型。 若為 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式，您必須擁有可有效簽署程式碼的 Authenticode 憑證。 若嘗試使用另一種憑證類型簽署 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式，例如數位電子郵件憑證，它會無法運作。 如需詳細資訊，請參閱 [Introduction to Code Signing](https://msdn.microsoft.com/library/ms537361.aspx)(程式碼簽署簡介)。  
  
 有三種方法可以取得程式碼簽署憑證︰  
  
- 向憑證廠商購買。  
  
- 由貴組織負責建立數位憑證的群組提供。  
  
- 使用隨附於 [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]的 MakeCert.exe，自己產生憑證。  
  
### <a name="how-using-certificate-authorities-helps-users"></a>如何使用憑證授權單位幫助使用者  
 使用 MakeCert 公用程式產生的憑證通常稱為「*自我*憑證」或「*測試憑證*」。這種憑證的運作方式與 .snk 檔案在 .NET Framework 中的運作方式相同。 它只有公開/私密密碼編譯金鑰組，不包含任何可驗證的發行者資訊。 您可以使用自助憑證部署在內部網路高度信任的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式。 不過，當這些應用程式在用戶端電腦上執行時， [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 會視之為來自未知的發行者。 根據預設，使用自我憑證簽署並透過網際網路部署的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式，不能使用受信任的應用程式部署。  
  
 相反地，來自 CA 的憑證，例如，憑證廠商或貴企業內部的部門，能為您的使用者提供更高的安全性。 它不只會識別簽署軟體的發行者，還會檢查簽署的 CA 驗證身分識別。 如果 CA 不是根授權單位，Authenticode 也會「鏈結」回根授權單位，確認 CA 有權發行憑證。 為了更高的安全性，您應該盡可能使用 CA 發出的憑證。  
  
 如需產生自我憑證的詳細資訊，請參閱[Makecert （憑證建立工具）](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)。  
  
### <a name="timestamps"></a>時間戳記  
 簽署 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式所用的憑證會在一定時間後過期，通常是十二個月。 為免經常需要使用新憑證重新簽署應用程式， [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 支援時間戳記。 使用時間戳記簽署應用程式後，只要時間戳記有效，憑證即使到期仍被接受。 這可讓使用過期憑證，但時間戳記有效的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式，能夠下載並執行。 它也允許使用過期憑證的已安裝應用程式，能夠繼續下載並安裝更新。  
  
 若要在應用程式伺服器中包含時間戳記，必須有可用的時間戳記伺服器。 如需如何選取時間戳記伺服器的資訊，請參閱 [How to: Sign Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md)。  
  
### <a name="updating-expired-certificates"></a>更新過期的憑證  
 在舊版的 .NET Framework 中，更新憑證已過期的應用程式可能會導致應用程式停止運作。 為解決此問題，請使用下列其中一種方法：  
  
- 將 .NET Framework 更新至 2.0 SP1 版或更新版本 (Windows XP)，或 3.5 版或更新版本 (Windows Vista)。  
  
- 解除安裝應用程式，並重新安裝具有有效憑證的新版本。  
  
- 建立可更新憑證的命令列組件。 此程序的逐步資訊，請參閱 [Microsoft 支援文章 925521](https://support.microsoft.com/kb/925521)。  
  
### <a name="storing-certificates"></a>儲存憑證  
  
- 您可以將憑證儲存為檔案系統的 .pfx 檔，或儲存在金鑰容器內。 Windows 網域的使用者可以有多個金鑰容器。 MakeCert.exe 預設將憑證儲存在您個人的金鑰容器中，除非您另行指定，才會改儲存為 .pfx。 Mage.exe 和 MageUI.exe 是建立 [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] 部署的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 工具，可讓您使用以任一方式儲存的憑證。  
  
## <a name="see-also"></a>請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe (資訊清單產生和編輯工具)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
