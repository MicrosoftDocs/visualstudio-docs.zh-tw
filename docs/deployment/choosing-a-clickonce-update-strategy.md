---
title: "選擇 ClickOnce 更新策略 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application updates, ClickOnce
- updates, ClickOnce
- ClickOnce deployment, update strategies
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
caps.latest.revision: "23"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 6c7d8b1562b821129b3b9f0e6881f7a47a3a95da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="choosing-a-clickonce-update-strategy"></a>選擇 ClickOnce 更新策略
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 可以提供應用程式自動更新。 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式會定期讀取它以查看是否有可用更新，應用程式的部署資訊清單檔。 如果有，就會下載及執行應用程式的新版本。 為了提高效率，只有已變更的檔案才會下載。  
  
 設計 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，您必須決定應用程式要使用哪一種策略來查看可用的更新。 您有三種基本的策略可以使用：在應用程式啟動時檢查更新、在應用程式啟動後檢查更新 (在背景執行緒中執行)，或提供更新的使用者介面。  
  
 此外，您可以決定應用程式檢查更新的頻率，而且可以讓更新成為必要。  
  
> [!NOTE]
>  應用程式更新會需要網路連接。 如果沒有網路連接，不論您所選擇的更新策略為何，應用程式將會執行但不檢查更新。  
  
> [!NOTE]
>  在 .NET Framework 2.0 和 .NET Framework 3.0 中，不論應用程式是隨時檢查更新、在啟動之前或之後檢查更新，或者使用 <xref:System.Deployment.Application> API 檢查更新，您都必須設定部署資訊清單中的 `deploymentProvider`。 `deploymentProvider` Visual Studio 中的項目對應**更新位置**欄位**更新**對話方塊中的 [**發行**] 索引標籤。.NET Framework 3.5 則放寬了此規則。 如需詳細資訊，請參閱[部署 ClickOnce 應用程式的測試和實際執行伺服器，而 Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)。  
  
## <a name="checking-for-updates-after-application-startup"></a>在應用程式啟動後檢查更新  
 使用此策略時，應用程式會在執行中時，嘗試在背景中尋找及讀取部署資訊清單檔。 如果有可用的更新，下次使用者執行應用程式時，就會收到下載並安裝更新的提示。  
  
 這項策略最適合低頻寬網路連接或可能需要冗長下載時間的大型應用程式。  
  
 若要啟用此更新策略，請按一下**應用程式啟動後**中**選擇應用程式應該於何時檢查更新**區段**應用程式更新**對話方塊。 然後在區段中指定更新間隔**指定應用程式應該要檢查更新的頻率**。  
  
 這等同於變更**更新**部署中的項目資訊清單，如下所示：  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <expiration maximumAge="6" unit="hours" />  
   </update>  
</subscription>  
```  
  
## <a name="checking-for-updates-before-application-startup"></a>在應用程式啟動前檢查更新  
 預設的策略是在應用程式啟動前，嘗試找出並讀取部署資訊清單檔。 使用此策略時，每次使用者啟動應用程式，應用程式就會嘗試找出並讀取部署資訊清單檔。 如果有更新可用，就會下載並啟動更新。否則，就會啟動現有版本的應用程式。  
  
 這項策略最適合高頻寬網路連接，因為在低頻寬連接上啟動應用程式的延遲時間可能會非常久。  
  
 若要啟用此更新策略，請按一下**應用程式啟動之前**中**選擇應用程式應該於何時檢查更新**區段**應用程式更新**對話方塊。  
  
 這等同於變更**更新**部署中的項目資訊清單，如下所示：  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <beforeApplicationStartup />  
   </update>  
</subscription>  
```  
  
## <a name="making-updates-required"></a>讓更新成為必要  
 有時候，您可能會想要要求使用者執行更新版本的應用程式。 例如，您可能會對外部資源 (例如 Web 服務) 進行變更，進而導致舊版應用程式無法正確運作。 在這種情況下，您就會想要將更新標記為必要，並防止使用者執行舊版。  
  
> [!NOTE]
>  雖然您可以使用其他的更新策略中需要更新，檢查**應用程式啟動之前**是保證不能執行較舊版本的唯一方式。 在啟動時若偵測到強制更新，使用者就必須接受更新或關閉應用程式。  
  
 若要將標示為必要項目，按一下 更新**指定此應用程式的最小必要的版本**中**應用程式會更新**對話方塊方塊，然後再指定發行版本 (**主要**，**次要**，**建置**，**修訂**)，其中指定可以安裝的應用程式的最低版本號碼。  
  
 這是設定相同**minimumRequiredVersion**屬性**部署**部署資訊清單中; 中的項目，例如：  
  
```  
<deployment install="true" minimumRequiredVersion="1.0.0.0">  
```  
  
## <a name="specifying-update-intervals"></a>指定更新間隔  
 您也可以指定應用程式檢查更新的頻率。 若要這樣做，請根據本主題前面「在應用程式啟動後檢查更新」一節所述的方式，將應用程式指定為在啟動後檢查更新。  
  
 若要指定更新間隔，請設定**指定應用程式應該要檢查更新的頻率**中的屬性**應用程式更新** 對話方塊。  
  
 這是設定相同**maximumAge**和**單元**屬性**更新**部署資訊清單中的項目。  
  
 例如，您可能會想要在應用程式每次執行時檢查、每週檢查一次，或每月檢查一次。 如果在指定的時間沒有網路連接，就會在應用程式下次執行時執行更新檢查。  
  
## <a name="providing-a-user-interface-for-updates"></a>提供更新的使用者介面  
 使用這項策略時，應用程式開發人員就會提供一個使用者介面，以便讓使用者選擇應用程式檢查更新的時間以及頻率。 例如，您可能會提供 [立即檢查更新檔] 命令，或是有不同更新間隔選項的 [更新設定] 對話方塊。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署 Api 提供的架構開發您自己的更新使用者介面。 如需詳細資訊，請參閱 <xref:System.Deployment.Application>。  
  
 如果應用程式是使用部署 API 來控制它本身的更新邏輯，您應該要封鎖更新檢查，如下一節「封鎖更新檢查」所述。  
  
 這項策略最適合在您需要針對不同使用者使用不同的更新策略時。  
  
## <a name="blocking-update-checking"></a>封鎖更新檢查  
 您也可以防止應用程式檢查更新。 例如，您可能有一個永遠不會更新的簡單應用程式，但想要利用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署所提供的簡易安裝功能。  
  
 如果應用程式是使用部署 API 來執行它本身的更新，您也應該要封鎖更新檢查；請參閱本主題前面的「提供更新的使用者介面」。  
  
 若要封鎖更新檢查，請清除**應用程式應該檢查更新檔**應用程式的 [更新] 對話方塊中核取方塊。  
  
 此外，您也可以從部署資訊清單中移除 `<Subscription>` 標記，藉以封鎖更新檢查。  
  
## <a name="permission-elevation-and-updates"></a>使用權限提高和更新  
 如果 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的新版本需要使用比舊版本更高的信任層級才能執行，則 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 將會提示使用者，詢問使用者是否要對應用程式授與這個較高的信任層級。 如果使用者拒絕授與較高的信任層級，則不會安裝更新。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 將會在下一次重新啟動時，再次提示使用者安裝此應用程式。 如果使用者在這時拒絕授與較高的信任層級，而且此更新未標記為必要項，則會執行舊版的應用程式。 不過，如果此更新為必要項，則使用者必須接受較高的信任層級之後，才會執行此應用程式。  
  
 如果您使用受信任的應用程式部署，就不會出現授與信任層級的提示。 如需詳細資訊，請參閱 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Deployment.Application>   
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 執行應用程式更新的方式](../deployment/how-clickonce-performs-application-updates.md)   
 [如何：管理 ClickOnce 應用程式的更新](../deployment/how-to-manage-updates-for-a-clickonce-application.md)