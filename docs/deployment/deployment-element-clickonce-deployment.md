---
title: '&lt;部署&gt;項目 （ClickOnce 部署） |Microsoft Docs'
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
ms.openlocfilehash: 5a7a22e683f1db05544f235308dc5ba495f74095
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629517"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;部署&gt;項目 （ClickOnce 部署）
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
 `deployment` 項目是必要的，且位於 `urn:schemas-microsoft-com:asm.v1` 命名空間。 該項目具有下列屬性。


| 屬性 | 說明 |
|--------------------------| - |
| `install` | 必要項。 指定此應用程式是否定義在 Windows 上出現**開始** 功能表和控制項台中**新增或移除程式**應用程式。 有效值為 `true` 和 `false`。 如果`false`，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]一律會從網路中，執行此應用程式的最新版本並不會辨識`subscription`項目。 |
| `minimumRequiredVersion` | 選擇性。 指定可以在用戶端執行此應用程式的最小版本。 如果應用程式的版本號碼小於提供的部署資訊清單中的版本號碼，將不會執行應用程式。 必須以格式指定版本號碼`N.N.N.N`，其中`N`是一個不帶正負號的整數。 如果`install`屬性是`false`，`minimumRequiredVersion`就不能設定。 |
| `mapFileExtensions` | 選擇性。 預設值為 `false`。 如果`true`，部署中的所有檔案必須都有.deploy 副檔名。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 會關閉這些檔案移除此延伸模組，因為它會將它們從 Web 伺服器下載。 如果您發行應用程式使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，它會自動加入此延伸模組的所有檔案。 此參數可讓內的所有檔案[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]區塊的結尾為"unsafe"的擴充功能，例如.exe 的檔案傳輸的網頁伺服器從下載部署。 |
| `disallowUrlActivation` | 選擇性。 預設值為 `false`。 如果`true`，防止藉由按一下 URL，或將 URL 輸入 Internet Explorer 正在啟動已安裝應用程式。 如果`install`屬性不存在，會忽略此屬性。 |
| `trustURLParameters` | 選擇性。 預設值為 `false`。 如果`true`、 允許的 URL 包含查詢字串參數傳遞至應用程式、 多 like 的命令列引數傳遞至命令列應用程式。 如需詳細資訊，請參閱 <<c0> [ 如何： 在線上 ClickOnce 應用程式中擷取查詢字串資訊](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)。<br /><br /> 如果`disallowUrlActivation`屬性是`true`，`trustUrlParameters`必須是從資訊清單中，排除，或明確設定為`false`。 |

 `deployment`元素也包含下列子元素。

## <a name="subscription"></a>訂用帳戶
 選擇性。 包含`update`項目。 `subscription` 項目沒有任何屬性。 如果`subscription`項目不存在，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式永遠不會掃描是否有更新。 如果`install`的屬性`deployment`項目是`false`，則`subscription`項目會被忽略，因為[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]會一律從網路啟動的應用程式使用最新版本。

## <a name="update"></a>更新
 必要項。 這是元素的子系`subscription`項目和包含`beforeApplicationStartup`或`expiration`項目。 `beforeApplicationStartup` 和`expiration`不可同時指定相同的部署資訊清單中。

 `update` 項目沒有任何屬性。

## <a name="beforeapplicationstartup"></a>beforeApplicationStartup
 選擇性。 這是元素的子系`update`項目並沒有任何屬性。 當`beforeApplicationStartup`項目存在，應用程式將會封鎖[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]檢查更新，如果用戶端在線上。 如果這個項目不存在，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]會先掃描是否有指定的值為基礎的更新`expiration`項目。 `beforeApplicationStartup` 和`expiration`不可同時指定相同的部署資訊清單中。

## <a name="expiration"></a>到期
 選擇性。 這是元素的子系`update`項目，並沒有子系。 `beforeApplicationStartup` 和`expiration`不可同時指定相同的部署資訊清單中。 時不會進行更新檢查，並偵測到更新的版本，執行現有的版本時，會快取新的版本。 下一步 啟動再安裝新版本[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。

 `expiration`項目支援下列屬性。

|屬性|說明|
|---------------|-----------------|
|`maximumAge`|必要項。 識別多久目前的更新應該就之前在應用程式執行更新檢查。 時間單位由`unit`屬性。|
|`unit`|必要項。 識別的時間單位`maximumAge`。 有效的單位是`hours`， `days`，和`weeks`。|

## <a name="deploymentprovider"></a>deploymentProvider
 .NET Framework 2.0 中，則需要這個元素如果部署資訊清單包含`subscription`一節。 適用於.NET Framework 3.5 和更新版本，這個元素是選擇性的並將預設為伺服器和部署資訊清單已探索到的檔案路徑。

 這個元素是 `deployment` 元素的子項，並具有下列屬性。


| 屬性 | 說明 |
|------------| - |
| `codebase` | 必要項。 識別的位置，做為統一資源識別元 (URI)，用來更新的部署資訊清單[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。 此項目也允許轉送的 CD 安裝的更新位置。 必須是有效的 URI。 |

## <a name="remarks"></a>備註
 您可以設定您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]掃描在啟動時，更新的應用程式啟動之後，掃描更新，或永遠不檢查更新。 若要在啟動更新掃描，請確認`beforeApplicationStartup`下的項目存在`update`項目。 若要在啟動之後，以掃描更新，請確定`expiration`下的項目存在`update`項目，並會提供 更新間隔。

 若要停用檢查更新，請移除`subscription`項目。 當您指定在部署資訊清單中，永遠不會掃描更新時，您可以仍然手動檢查更新使用<xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A>方法。

 如需有關 deploymentProvider 如何與更新相關聯的詳細資訊，請參閱[選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。

## <a name="examples"></a>範例
 下列程式碼範例說明`deployment`中的項目[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署資訊清單。 此範例會使用`deploymentProvider`元素，以指定慣用的更新位置。

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