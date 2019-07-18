---
title: HOW TO：指定部署更新的替代位置 |Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d312a213f630c3cc94a5a58ab41ed2014ca13bc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63406577"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>HOW TO：指定部署更新的替代位置
您可以安裝您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式一開始是從光碟或檔案共用，但應用程式必須檢查是否有定期更新，在網站上。 讓您的應用程式可以在其初始安裝後從 Web 自行更新，您可以在您的部署資訊清單中指定更新的替代位置。

> [!NOTE]
> 您的應用程式必須設定為在本機安裝才能使用這項功能。 如需詳細資訊，請參閱[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 此外，如果您安裝[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式從網路中，設定替代位置原因[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]用於初始安裝和所有後續更新中的該位置。 如果您安裝應用程式的本機 （例如，從 CD)，使用原始媒體，來執行初始安裝和所有後續的更新會使用替代的位置。

### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>使用 MageUI.exe （Windows Form 為基礎的公用程式） 來指定更新的替代位置

1. 開啟.NET Framework 命令提示字元並輸入：

     **mageui.exe**

2. 在 **檔案**功能表上，選擇**開啟**開啟您的應用程式部署資訊清單。

3. 選取 [部署選項]  索引標籤。

4. 在文字方塊中名為**啟動位置**，將會包含應用程式更新的部署資訊清單的目錄中輸入的 URL。

5. 儲存部署資訊清單。

### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>使用 Mage.exe，以指定更新的替代位置

1. 開啟 [.NET Framework 命令提示字元]。

2. 設定使用下列命令更新的位置。 在此範例中， *HelloWorld.exe.application*是通往您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單，其一律.application 副檔名，和 *<http://adatum.com/Update/Path>* 是 URL 該[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]會檢查應用程式更新。

    **Mage -Update HelloWorld.exe.application -ProviderUrl http://adatum.com/Update/Path**

3. 儲存檔案。

   > [!NOTE]
   > 您現在需要重新簽署的檔案*Mage.exe*。 如需詳細資訊，請參閱[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。

## <a name="net-framework-security"></a>.NET Framework 安全性
 如果您從離線媒體例如 CD、 安裝應用程式，而且電腦已上線，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]所指定的 URL 會先檢查`<deploymentProvider>`以判斷是否更新位置包含較新版的部署資訊清單中的標記應用程式。 若是如此，請[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]會從初始的安裝目錄，直接從該處，應用程式而不是安裝和 common language runtime (CLR) 會決定您的應用程式信任層級使用`<deploymentProvider>`。 如果電腦處於離線狀態，或`<deploymentProvider>`無法連線，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]安裝 CD，與 CLR 授與信任的安裝點為基礎，進行 CD 安裝，這表示您的應用程式收到的完全信任。 所有後續的更新將會繼承該信任層級。

 所有[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]使用的應用程式`<deploymentProvider>`應該明確宣告其應用程式資訊清單中，所需的權限，以便應用程式不會收到不同的層級的不同電腦上的信任。

## <a name="see-also"></a>另請參閱
- [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)
- [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)
- [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)