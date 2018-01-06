---
title: "&lt;部署&gt;元素 （ClickOnce 部署） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
helpviewer_keywords: <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: "30"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 0caff13f84208152b3fa2ff4e56a7a2c7f0b6dd7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;部署&gt;元素 （ClickOnce 部署）
識別用於更新部署及公開至系統的屬性。  
  
## <a name="syntax"></a>語法  
  
```  
  
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
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `deployment` 為必要元素，位於 `urn:schemas-microsoft-com:asm.v1` 命名空間。 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`install`|必要。 指定此應用程式是否定義出現在 Windows**啟動**功能表和控制台中**新增或移除程式**應用程式。 有效值為 `true` 和 `false`。 如果`false`，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]一律會從網路上執行此應用程式的最新版本並不會辨識`subscription`項目。|  
|`minimumRequiredVersion`|選擇性。 指定可以在用戶端執行此應用程式的最小版本。 如果應用程式的版本號碼小於部署資訊清單中提供的版本號碼，將不會執行應用程式。 必須以格式指定版本號碼`N.N.N.N`，其中`N`是不帶正負號的整數。 如果`install`屬性是`false`，`minimumRequiredVersion`不能設定。|  
|`mapFileExtensions`|選擇性。 預設值為 `false`。 如果`true`，在部署中的所有檔案都必須都有.deploy 副檔名。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]將會關閉這些檔案帶狀這項擴充功能，因為它會將它們從 Web 伺服器下載。 如果您發行應用程式使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，它會自動加入此延伸模組的所有檔案。 此參數可讓內的所有檔案[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]封鎖了 「 安全 」 擴充功能，例如.exe 的檔案傳輸的網頁伺服器從下載部署。|  
|`disallowUrlActivation`|選擇性。 預設值為 `false`。 如果`true`，避免透過按一下 URL，或將 URL 輸入 Internet Explorer 正在啟動已安裝應用程式。 如果`install`屬性不存在，會忽略此屬性。|  
|`trustURLParameters`|選擇性。 預設值為 `false`。 如果`true`、 允許的 URL 包含查詢字串參數傳遞至應用程式、 多 like 的命令列引數會傳遞至命令列應用程式。 如需詳細資訊，請參閱[How to： 在線上 ClickOnce 應用程式中擷取查詢字串資訊](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)。<br /><br /> 如果`disallowUrlActivation`屬性是`true`，`trustUrlParameters`必須排除從資訊清單，或明確設定為`false`。|  
  
 `deployment`項目也包含下列子元素。  
  
## <a name="subscription"></a>訂用帳戶  
 選擇性。 包含`update`項目。 `subscription`項目沒有任何屬性。 如果`subscription`項目不存在，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式永遠不會掃描是否有更新。 如果`install`屬性`deployment`項目是`false`、`subscription`項目會被忽略，因為[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]一律從網路啟動的應用程式會使用最新版本。  
  
## <a name="update"></a>更新  
 必要。 這個項目是子系`subscription`項目與包含`beforeApplicationStartup`或`expiration`項目。 `beforeApplicationStartup`和`expiration`無法同時指定相同的部署資訊清單中。  
  
 `update`項目沒有任何屬性。  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 選擇性。 這個項目是子系`update`項目，但沒有屬性。 當`beforeApplicationStartup`項目存在，應用程式將會遭到封鎖時[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]檢查更新，如果用戶端在線上。 如果這個項目不存在，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]會針對指定的值為基礎的更新會先掃描`expiration`項目。 `beforeApplicationStartup`和`expiration`無法同時指定相同的部署資訊清單中。  
  
## <a name="expiration"></a>到期日  
 選擇性。 這個項目是子系`update`項目，並沒有子系。 `beforeApplicationStartup`和`expiration`無法同時指定相同的部署資訊清單中。 時不會進行更新檢查已偵測到更新的版本，執行現有的版本時，會快取新的版本。 在下一步 啟動然後安裝新版本[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。  
  
 `expiration`項目支援下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`maximumAge`|必要。 識別如何舊目前的更新應該就之前在應用程式執行更新檢查。 時間單位由`unit`屬性。|  
|`unit`|必要。 識別的時間單位`maximumAge`。 有效的單位是`hours`， `days`，和`weeks`。|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 針對.NET Framework 2.0 中，則需要這個元素的部署資訊清單包含如果`subscription`> 一節。 適用於.NET Framework 3.5 和更新版本，此元素為選擇性，而且將會預設為伺服器和部署資訊清單已探索到的檔案路徑。  
  
 這個元素是 `deployment` 元素的子項，並具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`codebase`|必要。 識別的位置，做為統一資源識別元 (URI)，用來更新部署資訊清單的[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。 這個項目也可以轉送 CD 為基礎的安裝的更新位置。 必須是有效的 URI。|  
  
## <a name="remarks"></a>備註  
 您可以設定您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]掃描更新，在啟動時，應用程式啟動之後，掃描更新，或永遠不檢查更新。 若要掃描更新，在啟動時，請確認`beforeApplicationStartup`元素底下有`update`項目。 若要在啟動後掃描更新，請確認`expiration`元素底下有`update`項目，而且所提供的更新間隔。  
  
 若要停用檢查更新，請移除`subscription`項目。 當您指定永遠不會掃描更新部署資訊清單中時，您可以仍然可以手動檢查更新使用<xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A>方法。  
  
 如需有關 deploymentProvider 如何與更新相關聯的詳細資訊，請參閱[選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
## <a name="examples"></a>範例  
 下列程式碼範例說明`deployment`中的項目[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署資訊清單。 此範例會使用`deploymentProvider`指示慣用的更新位置的項目。  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## <a name="see-also"></a>請參閱  
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)