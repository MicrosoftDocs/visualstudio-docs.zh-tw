---
title: '&lt;deployment&gt;元素（ClickOnce 部署） |Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 988ce0859ab24377395cc4077f9e6fa42e0487a5
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887851"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;deployment&gt;元素（ClickOnce 部署）
識別用於更新部署及公開至系統的屬性。

## <a name="syntax"></a>語法

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
 `deployment` 項目是必要的，且位於 `urn:schemas-microsoft-com:asm.v2` 命名空間。 該項目具有下列屬性。

| 屬性 | 描述 |
|--------------------------| - |
| `install` | 必要項。 指定此應用程式是否會在 Windows [**開始**] 功能表和 [控制台] [**新增或移除程式**] 應用程式中定義目前狀態。 有效值為 `true` 和 `false`。 如果`false`是[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ，一律會從網路執行這個應用程式的最新版本， `subscription`而且不會辨識元素。 |
| `minimumRequiredVersion` | 選擇性。 指定此應用程式可在用戶端上執行的最小版本。 如果應用程式的版本號碼小於部署資訊清單中提供的版本號碼，應用程式將不會執行。 版本號碼必須以格式`N.N.N.N`指定，其中`N`是不帶正負號的整數。 如果屬性為`false` ，`minimumRequiredVersion`則不得設定。 `install` |
| `mapFileExtensions` | 選擇性。 預設值為 `false`。 如果`true`為，則部署中的所有檔案都必須具有 .deploy 副檔名。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]當這些檔案從 Web 服務器下載時，將會立即從這些檔案中去除。 如果您使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]來發行應用程式，它會自動將此延伸模組新增至所有檔案。 此參數可從 Web 服務器下載[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署中的所有檔案，以封鎖以「不安全」副檔名結尾的檔案（例如 .exe）的傳輸。 |
| `disallowUrlActivation` | 選擇性。 預設值為 `false`。 如果`true`是，請在 Internet Explorer 中按一下 url 或輸入 url，以防止已安裝的應用程式啟動。 `install`如果屬性不存在，則會忽略這個屬性。 |
| `trustURLParameters` | 選擇性。 預設值為 `false`。 如果`true`是，允許 URL 包含傳入應用程式的查詢字串參數，就像命令列引數一樣，會傳遞至命令列應用程式。 如需詳細資訊，請參閱[如何：在線上 ClickOnce 應用程式中擷取查詢字串資訊](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)。<br /><br /> 如果屬性為`true` `false`， `trustUrlParameters`則必須從資訊清單中排除，或明確地設定為。 `disallowUrlActivation` |

 `deployment`元素也包含下列子項目。

## <a name="subscription"></a>訂用帳戶
 選擇性。 `update`包含元素。 `subscription` 項目沒有任何屬性。 如果元素不存在，應用程式永遠不會掃描更新。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `subscription` 如果`deployment`元素`install`的屬性為`false`，則會忽略`subscription`元素，因為從網路啟動的應用程式一律使用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]最新版本。

## <a name="update"></a>更新
 必要項。 這個元素是`subscription`元素的子系，而且包含`beforeApplicationStartup`或`expiration`專案。 `beforeApplicationStartup`和`expiration`不能同時在相同的部署資訊清單中指定。

 `update` 項目沒有任何屬性。

## <a name="beforeapplicationstartup"></a>beforeApplicationStartup
 選擇性。 這個元素是`update`元素的子系，而且沒有任何屬性。 當元素存在時，如果用戶端在線上， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]則會在檢查更新時封鎖應用程式。 `beforeApplicationStartup` 如果這個元素不存在， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]將會先根據為`expiration`元素指定的值來掃描更新。 `beforeApplicationStartup`和`expiration`不能同時在相同的部署資訊清單中指定。

## <a name="expiration"></a>到期
 選擇性。 這個元素是`update`元素的子系，而且沒有子系。 `beforeApplicationStartup`和`expiration`不能同時在相同的部署資訊清單中指定。 當更新檢查發生並偵測到更新的版本時，新版本會在現有版本執行時快取。 新版本接著會在下一次啟動[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式時安裝。

 `expiration`元素支援下列屬性。

|屬性|描述|
|---------------|-----------------|
|`maximumAge`|必要項。 識別目前的更新在應用程式執行更新檢查之前應如何成為舊的版本。 時間單位是由`unit`屬性所決定。|
|`unit`|必要項。 識別的時間`maximumAge`單位。 有效的單位`hours`為`days`、和`weeks`。|

## <a name="deploymentprovider"></a>deploymentProvider
 針對 .NET Framework 2.0，如果部署資訊清單包含`subscription`區段，則需要這個元素。 針對 .NET Framework 3.5 和更新版本，這個元素是選擇性的，而且會預設為探索到部署資訊清單的伺服器和檔案路徑。

 這個元素是 `deployment` 元素的子項，並具有下列屬性。

| 屬性 | 描述 |
|------------| - |
| `codebase` | 必要項。 識別用來更新[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式之部署資訊清單的「統一資源識別元（URI）」位置。 此元素也允許轉送以 CD 為基礎之安裝的更新位置。 必須是有效的 URI。 |

## <a name="remarks"></a>備註
 您可以將[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式設定為在啟動時掃描更新、在啟動後掃描更新，或永遠不檢查更新。 若要在啟動時掃描更新，請確定`beforeApplicationStartup`專案是否存在於`update`元素之下。 若要在啟動之後掃描更新，請確定`expiration` `update`專案位於元素底下，而且已提供更新間隔。

 若要停用更新檢查，請`subscription`移除元素。 當您在部署資訊清單中指定永遠不會掃描更新時，您仍然可以使用<xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A>方法來手動檢查更新。

 如需有關 deploymentProvider 如何與更新產生關聯的詳細資訊，請參閱[選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。

## <a name="examples"></a>範例
 下列程式碼範例說明`deployment` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署資訊清單中的元素。 此範例會使用`deploymentProvider`專案來表示慣用的更新位置。

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