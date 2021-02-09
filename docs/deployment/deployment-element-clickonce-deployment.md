---
title: '&lt;&gt;ClickOnce 部署 (的 deployment 元素) |Microsoft Docs'
description: Deployment 元素會識別用來部署更新和暴露于系統的屬性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 369d48c76ed82825021622af35141ef12ff42c76
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893902"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;&gt;ClickOnce 部署 (的 deployment 元素) 
識別用於更新部署及公開至系統的屬性。

## <a name="syntax"></a>Syntax

```xml

      <deployment
   install
   minimumRequiredVersion
   mapFileExtensions
   disallowUrlActivation
   trustUrlParameters
>
   <subscription>
         <update>
            <beforeApplicationStartup/>
            <expiration
               maximumAge
               unit
            />
         </update>
   </subscription>
   <deploymentProvider
      codebase
   />
</deployment>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `deployment` 項目是必要的，且位於 `urn:schemas-microsoft-com:asm.v2` 命名空間。 元素具有下列屬性。

| 屬性 | 描述 |
|--------------------------| - |
| `install` | 必要。 指定此應用程式是否會在 Windows [ **開始** ] 功能表和 [主控台 **新增或移除程式** ] 應用程式中定義狀態。 有效值為 `true` 和 `false`。 如果 `false` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 為，一律會從網路執行這個應用程式的最新版本，而且不會辨識 `subscription` 元素。 |
| `minimumRequiredVersion` | 選擇性。 指定可在用戶端上執行的此應用程式的最小版本。 如果應用程式的版本號碼小於部署資訊清單中提供的版本號碼，應用程式將不會執行。 版本號碼必須以格式指定 `N.N.N.N` ，其中 `N` 是不帶正負號的整數。 如果 `install` 屬性為 `false` ，則 `minimumRequiredVersion` 不得設定。 |
| `mapFileExtensions` | 選擇性。 預設值為 `false`。 如果 `true` 為，則部署中的所有檔案都必須有 .deploy 副檔名。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 從 Web 服務器下載這些檔案後，就會立即從這些檔案中移除此延伸模組。 如果您使用發行您的應用程式 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，它會自動將此延伸模組新增至所有檔案。 此參數可讓您 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 從 Web 服務器下載部署內的所有檔案，以封鎖以 "unsafe" 擴充功能（例如 .exe）結尾的檔案。 |
| `disallowUrlActivation` | 選擇性。 預設值為 `false`。 如果為 `true` ，則會在 Internet Explorer 中按一下 url 或輸入 url，以防止已安裝的應用程式啟動。 如果 `install` 屬性不存在，則會忽略這個屬性。 |
| `trustURLParameters` | 選擇性。 預設值為 `false`。 如果 `true` 為，則允許 URL 包含傳遞至應用程式的查詢字串參數，很類似命令列引數會傳遞至命令列應用程式。 如需詳細資訊，請參閱 [如何：在線上 ClickOnce 應用程式中取得查詢字串資訊](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)。<br /><br /> 如果 `disallowUrlActivation` 屬性為 `true` ，則 `trustUrlParameters` 必須從資訊清單中排除，或將明確設定為 `false` 。 |

 `deployment`元素也包含下列子項目。

## <a name="subscription"></a>訂用帳戶
 選擇性。 包含 `update` 元素。 `subscription` 項目沒有任何屬性。 如果專案不 `subscription` 存在， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式將永遠不會掃描更新。 如果 `install` 元素的屬性 `deployment` 為，則會 `false` `subscription` 忽略元素，因為 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 從網路啟動的應用程式一律會使用最新版本。

## <a name="update"></a>update
 必要。 這個元素是元素的子系 `subscription` ，並且包含 `beforeApplicationStartup` 或 `expiration` 元素。 `beforeApplicationStartup` 而且 `expiration` 不能同時在相同的部署資訊清單中指定。

 `update` 項目沒有任何屬性。

## <a name="beforeapplicationstartup"></a>beforeApplicationStartup
 選擇性。 這個元素是元素的子系 `update` ，而且沒有任何屬性。 當 `beforeApplicationStartup` 元素存在時，如果用戶端在線上，就會封鎖應用程式 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 檢查是否有更新。 如果這個元素不存在， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 則會先根據為元素指定的值掃描更新 `expiration` 。 `beforeApplicationStartup` 而且 `expiration` 不能同時在相同的部署資訊清單中指定。

## <a name="expiration"></a>expiration
 選擇性。 這個元素是元素的子系 `update` ，而且沒有子系。 `beforeApplicationStartup` 而且 `expiration` 不能同時在相同的部署資訊清單中指定。 當更新檢查發生並偵測到更新的版本時，新版本會在現有版本執行時快取。 新版本接著會在下一次啟動 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時安裝。

 `expiration`元素支援下列屬性。

|屬性|描述|
|---------------|-----------------|
|`maximumAge`|必要。 識別目前的更新在應用程式執行更新檢查之前應該如何成為舊的。 時間單位是由屬性所決定 `unit` 。|
|`unit`|必要。 識別的時間單位 `maximumAge` 。 有效的單位為 `hours` 、 `days` 和 `weeks` 。|

## <a name="deploymentprovider"></a>deploymentProvider
 針對 .NET Framework 2.0，如果部署資訊清單包含區段，則需要這個元素 `subscription` 。 在 .NET Framework 3.5 和更新版本中，這個元素是選擇性的，而且會預設為探索到部署資訊清單的伺服器和檔案路徑。

 這個元素是 `deployment` 元素的子項，並具有下列屬性。

| 屬性 | 描述 |
|------------| - |
| `codebase` | 必要。 以用來更新應用程式之部署資訊清單的統一資源識別元 (URI) 來識別位置 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 這個元素也允許轉送以 CD 為基礎之安裝的更新位置。 必須是有效的 URI。 |

## <a name="remarks"></a>備註
 您可以將 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式設定為在啟動時掃描更新、在啟動後掃描更新，或永遠不檢查更新。 若要在啟動時掃描更新，請確定元素 `beforeApplicationStartup` 存在於 `update` 元素之下。 若要在啟動之後掃描更新，請確定 `expiration` 元素存在於 `update` 元素底下，且已提供更新間隔。

 若要停用檢查更新，請移除 `subscription` 元素。 當您在部署資訊清單中指定為永不掃描更新時，仍可使用方法手動檢查更新 <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> 。

 如需有關 deploymentProvider 如何與更新相關的詳細資訊，請參閱 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。

## <a name="examples"></a>範例
 下列程式碼範例說明 `deployment` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署資訊清單中的元素。 此範例會使用 `deploymentProvider` 元素來指出慣用的更新位置。

```xml
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">
    <subscription>
      <update>
        <expiration maximumAge="6" unit="hours" />
      </update>
    </subscription>
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />
  </deployment>
```

## <a name="see-also"></a>另請參閱
- [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)