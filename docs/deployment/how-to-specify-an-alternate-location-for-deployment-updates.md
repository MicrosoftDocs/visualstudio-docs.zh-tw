---
title: 如何-指定部署更新的替代位置 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: c71586c43fa1a71205d61ae21fb94c267daf497d
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381908"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>如何：指定部署更新的替代位置
您可以 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 從 CD 或檔案共用一開始安裝您的應用程式，但應用程式必須檢查網路上的定期更新。 您可以在部署資訊清單中指定更新的替代位置，讓您的應用程式可以在其初始安裝之後，從 Web 更新其本身。

> [!NOTE]
> 您的應用程式必須設定為在本機安裝，才能使用這項功能。 如需詳細資訊，請參閱[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 此外，如果您 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 從網路安裝應用程式，設定替代位置會導致 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 在初始安裝和所有後續更新中使用該位置。 如果您在本機安裝應用程式（例如，從 CD），則會使用原始媒體來執行初始安裝，而所有後續更新都會使用替代位置。

### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>使用 MageUI.exe （Windows Forms 為基礎的公用程式）指定更新的替代位置

1. 開啟 .NET Framework 命令提示字元，然後輸入：

     **mageui.exe**

2. 在 [檔案 **] 功能表上，選擇 [** **開啟**] 以開啟應用程式的部署資訊清單。

3. 選取 [部署選項]**** 索引標籤。

4. 在名為 [**啟動位置**] 的文字方塊中，輸入將包含應用程式更新之部署資訊清單的目錄 URL。

5. 儲存部署資訊清單。

### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>使用 Mage.exe 指定更新的替代位置

1. 開啟 .NET Framework 命令提示字元。

2. 使用下列命令來設定更新位置。 在此範例中， *HelloWorld.exe。應用*程式是 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單的路徑，它一律會有. 應用程式副檔名，而 `http://adatum.com/Update/Path` 是 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 會檢查應用程式更新的 URL。

    **Mage-更新 HelloWorld.exe。應用程式-ProviderUrl HTTP： \/ /adatum.com/Update/Path**

3. 儲存檔案。

   > [!NOTE]
   > 您現在必須使用*Mage.exe*重新簽署檔案。 如需詳細資訊，請參閱[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。

## <a name="net-framework-security"></a>.NET Framework 安全性
 如果您從離線媒體（例如 CD）安裝應用程式，且電腦已上線，會 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 先檢查部署資訊清單中的標記所指定的 URL， `<deploymentProvider>` 以判斷更新位置是否包含較新版本的應用程式。 如果有，則會 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 直接從該處安裝應用程式，而不是從初始安裝目錄，而 common language runtime （CLR）會使用來判斷您的應用程式信任層級 `<deploymentProvider>` 。 如果電腦已離線或無法連線 `<deploymentProvider>` ，會 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 從光碟片安裝，而且 CLR 會根據安裝點授與信任; 若是 CD 安裝，這表示您的應用程式會收到完全信任。 所有後續更新都會繼承該信任層級。

 所有 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用的應用程式 `<deploymentProvider>` 應該在其應用程式資訊清單中明確宣告其所需的許可權，讓應用程式不會在不同的電腦上收到不同的信任層級。

## <a name="see-also"></a>另請參閱
- [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)
- [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)
- [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)