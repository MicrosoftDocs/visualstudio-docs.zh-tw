---
title: 選擇 ClickOnce 更新策略 |Microsoft Docs
description: 瞭解 ClickOnce 應用程式如何支援自動更新，以及您可以使用的更新策略。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application updates, ClickOnce
- updates, ClickOnce
- ClickOnce deployment, update strategies
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d546b48ffbbb4d44fb5f2ced11f41826370403e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895072"
---
# <a name="choose-a-clickonce-update-strategy"></a>選擇 ClickOnce 更新策略
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 可提供自動應用程式更新。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式會定期讀取它的部署資訊清單檔，以查看是否有此應用程式的更新可用。 如果有，就會下載及執行應用程式的新版本。 為了提高效率，只有已變更的檔案才會下載。

 設計 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，您必須決定應用程式要使用哪一種策略來查看可用的更新。 您有三種基本的策略可以使用：在應用程式啟動時檢查更新、在應用程式啟動後檢查更新 (在背景執行緒中執行)，或提供更新的使用者介面。

 此外，您可以決定應用程式檢查更新的頻率，而且可以讓更新成為必要。

> [!NOTE]
> 應用程式更新會需要網路連接。 如果沒有網路連接，不論您所選擇的更新策略為何，應用程式將會執行但不檢查更新。

> [!NOTE]
> 在 .NET Framework 2.0 和 .NET Framework 3.0 中，不論應用程式是隨時檢查更新、在啟動之前或之後檢查更新，或者使用 \<xref:System.Deployment.Application> API 檢查更新，您都必須設定部署資訊清單中的 `deploymentProvider`。 專案會 `deploymentProvider` 在 [**發行**] 索引標籤的 [**更新**] 對話方塊中，對應至 [**更新位置**] 欄位的 Visual Studio。這項規則會在 .NET Framework 3.5 中放寬。 如需詳細資訊，請參閱 [部署 ClickOnce 應用程式以進行測試和實際執行伺服器，而不需](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)進行簽署。

## <a name="check-for-updates-after-application-startup"></a>在應用程式啟動後檢查更新
 使用此策略時，應用程式會在執行中時，嘗試在背景中尋找及讀取部署資訊清單檔。 如果有可用的更新，下次使用者執行應用程式時，就會收到下載並安裝更新的提示。

 這項策略最適合低頻寬網路連接或可能需要冗長下載時間的大型應用程式。

 若要啟用此更新策略，請在 [應用程式更新] 對話方塊的 [選擇應用程式應該於何時檢查更新檔] 區段中，按一下 [應用程式啟動之後]。 接著在 [指定應用程式應該要檢查更新檔的頻率] 區段內指定更新間隔。

 這個步驟與在部署資訊清單內變更 [Update] 元素相同，如下所示：

```xml
<!-- When to check for updates -->
<subscription>
   <update>
      <expiration maximumAge="6" unit="hours" />
   </update>
</subscription>
```

## <a name="check-for-updates-before-application-startup"></a>在應用程式啟動之前檢查更新
 預設的策略是在應用程式啟動前，嘗試找出並讀取部署資訊清單檔。 使用此策略時，每次使用者啟動應用程式，應用程式就會嘗試找出並讀取部署資訊清單檔。 如果有更新可用，就會下載並啟動更新。否則，就會啟動現有版本的應用程式。

 這項策略最適合高頻寬網路連接，因為在低頻寬連接上啟動應用程式的延遲時間可能會非常久。

 若要啟用此更新策略，請在 [應用程式更新] 對話方塊的 [選擇應用程式應該於何時檢查更新] 區段中，按一下 [在應用程式啟動前]。

 這個步驟與在部署資訊清單內變更 [Update] 元素相同，如下所示：

```xml
<!-- When to check for updates -->
<subscription>
   <update>
      <beforeApplicationStartup />
   </update>
</subscription>
```
> [!NOTE]
> 針對 .NET 3.1 和更新版本的應用程式，在應用程式啟動之前檢查更新是唯一支援的更新選項。

## <a name="make-updates-required"></a>需要進行更新
 有時候，您可能會想要要求使用者執行更新版本的應用程式。 例如，您可能會對外部資源 (例如 Web 服務) 進行變更，進而導致舊版應用程式無法正確運作。 在這種情況下，您就會想要將更新標記為必要，並防止使用者執行舊版。

> [!NOTE]
> 雖然您可以使用其他更新策略來要求更新，不過選取 [在應用程式啟動前] 選項是保證不會執行舊版的唯一方式。 在啟動時若偵測到強制更新，使用者就必須接受更新或關閉應用程式。

 若要將更新標記為必要項，請在 [應用程式更新] 對話方塊中按一下 [指定此應用程式的最小必要版本]，然後指定發行版本 (**主要**、**次要**、**建置**、**修訂**)，這樣會指定可安裝應用程式的最低版本號碼。

 這項設定與在部署資訊清單中設定 [Deployment] 元素的 **minimumRequiredVersion** 屬性相同，例如：

```xml
<deployment install="true" minimumRequiredVersion="1.0.0.0">
```

## <a name="specify-update-intervals"></a>指定更新間隔
 您也可以指定應用程式檢查更新的頻率。 若要這樣做，請根據本主題前面「在應用程式啟動後檢查更新」一節所述的方式，將應用程式指定為在啟動後檢查更新。

 若要指定更新間隔，請在 [應用程式更新] 對話方塊中設定 **指定應用程式應該要檢查更新檔的頻率** 屬性。

 這項設定與在部署資訊清單中設定 [Update] 元素的 **maximumAge** 和 **unit** 屬性相同。

 例如，您可能會想要在應用程式每次執行時檢查、每週檢查一次，或每月檢查一次。 如果在指定的時間沒有網路連接，就會在應用程式下次執行時執行更新檢查。

## <a name="provide-a-user-interface-for-updates"></a>提供更新的使用者介面
 使用這項策略時，應用程式開發人員就會提供一個使用者介面，以便讓使用者選擇應用程式檢查更新的時間以及頻率。 例如，您可能會提供 [立即檢查更新檔] 命令，或是有不同更新間隔選項的 [更新設定] 對話方塊。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署 API 提供了讓您以程式設計方式自行設計更新使用者介面的架構。 如需詳細資訊，請參閱 <xref:System.Deployment.Application>。

 如果應用程式是使用部署 API 來控制它本身的更新邏輯，您應該要封鎖更新檢查，如下一節「封鎖更新檢查」所述。

 這項策略最適合在您需要針對不同使用者使用不同的更新策略時。

## <a name="block-update-checking"></a>封鎖更新檢查
 您也可以防止應用程式檢查更新。 例如，您可能有一個永遠不會更新的簡單應用程式，但想要利用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署所提供的簡易安裝功能。

 如果您的應用程式使用部署 Api 來執行它自己的更新，您也應該封鎖更新檢查;請參閱本主題稍早的「提供更新的使用者介面」。

 若要禁止更新檢查，請取消選取 [應用程式更新] 對話方塊中的 [應用程式應該檢查更新] 核取方塊。

 此外，您也可以從部署資訊清單中移除 `<Subscription>` 標記，藉以封鎖更新檢查。

## <a name="permission-elevation-and-updates"></a>權限提高和更新
 如果 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的新版本需要使用比舊版本更高的信任層級才能執行，則 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 將會提示使用者，詢問使用者是否要對應用程式授與這個較高的信任層級。 如果使用者拒絕授與較高的信任層級，則不會安裝更新。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 將會在下一次重新啟動時，再次提示使用者安裝此應用程式。 如果使用者在這時拒絕授與較高的信任層級，而且此更新未標記為必要項，則會執行舊版的應用程式。 不過，如果此更新為必要項，則使用者必須接受較高的信任層級之後，才會執行此應用程式。

 如果您使用受信任的應用程式部署，就不會出現授與信任層級的提示。 如需詳細資訊，請參閱 [受信任的應用程式部署總覽](../deployment/trusted-application-deployment-overview.md)。

## <a name="see-also"></a>另請參閱
- <xref:System.Deployment.Application>
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
- [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)
- [ClickOnce 執行應用程式更新的方式](../deployment/how-clickonce-performs-application-updates.md)
- [How to: Manage updates for a ClickOnce application (如何：管理 ClickOnce 應用程式的更新)](../deployment/how-to-manage-updates-for-a-clickonce-application.md)
