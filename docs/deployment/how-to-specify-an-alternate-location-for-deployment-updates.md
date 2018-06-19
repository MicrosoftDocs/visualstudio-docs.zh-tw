---
title: 如何： 指定部署更新的替代位置 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14c6778d5cad698e6eea541b94df6f8eb793746c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31561346"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>如何：指定部署更新的其他位置
您可以安裝您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式一開始是從光碟或檔案共用，但是這個應用程式必須檢查是否有定期更新從網站上。 使您的應用程式可以在初始安裝後從 Web 本身更新，您可以在部署資訊清單中指定更新的替代位置。  
  
> [!NOTE]
>  您的應用程式必須設定為在本機安裝才能使用這項功能。 如需詳細資訊，請參閱[逐步解說： 手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 此外，如果您安裝[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式從網路上，設定替代位置原因[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]使用該位置的初始安裝和所有後續的更新。 如果您安裝應用程式在本機 （例如，從 CD)，使用原始媒體，執行初始安裝和所有後續的更新都會使用替代位置。  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>使用 MageUI.exe （Windows Form 為基礎的公用程式） 來指定更新的替代位置  
  
1.  開啟.NET Framework 命令提示字元並輸入：  
  
     **mageui.exe**  
  
2.  在**檔案**功能表上，選擇**開啟**開啟您的應用程式部署資訊清單。  
  
3.  選取**部署選項** 索引標籤。  
  
4.  在文字方塊中名為**啟動位置**，目錄會包含應用程式更新的部署資訊清單中輸入的 URL。  
  
5.  儲存部署資訊清單。  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>使用 Mage.exe 來指定更新的替代位置  
  
1.  開啟.NET Framework 命令提示字元。  
  
2.  設定使用下列命令更新的位置。 在此範例中， **HelloWorld.exe.application**是路徑您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]一律.application 副檔名，其應用程式資訊清單和**http://adatum.com/Update/Path**是該的URL[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]會檢查應用程式更新。  
  
     **Mage-更新 HelloWorld.exe.application ProviderUrl http://adatum.com/Update/Path**  
  
3.  儲存檔案。  
  
    > [!NOTE]
    >  您現在需要重新簽署的檔案，使用 Mage.exe。 如需詳細資訊，請參閱[逐步解說： 手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果您從離線媒體例如 CD、 安裝應用程式，而且電腦已上線，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]所指定的 URL 會先檢查`<deploymentProvider>`判斷是否更新位置包含較新版本的部署資訊清單中的標記應用程式。 若是如此，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]從初始安裝目錄中，會直接從該處，應用程式安裝而不是與 common language runtime (CLR) 會決定您的應用程式信任層級使用`<deploymentProvider>`。 如果電腦已離線，或`<deploymentProvider>`無法連線，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]安裝 CD 中，與 CLR 授與信任的安裝點為基礎; 進行 CD 安裝，這表示您的應用程式接收的完全信任。 所有後續的更新都會繼承該信任層級。  
  
 所有[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]使用的應用程式`<deploymentProvider>`應該明確宣告其應用程式資訊清單中，所需的權限，好讓應用程式不會收到不同的不同電腦上的信任層級。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)