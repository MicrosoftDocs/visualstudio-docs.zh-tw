---
title: '&lt;dependency&gt;元素（ClickOnce 應用程式） |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3aa949aa2f8e718ab0209c54a0ea2160c042a4eb
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252487"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;dependency&gt;元素（ClickOnce 應用程式）
識別應用程式所需的平臺或元件相依性。

## <a name="syntax"></a>語法

```xml

      <dependency>
   <dependentOS
      supportURL
      description
   >
      <osVersionInfo>
         <os
            majorVersion
            minorVersion
            buildNumber
            servicePackMajor
            servicePackMinor
            productType
            suiteType
         />
      </osVersionInfo>
   </dependentOS>
   <dependentAssembly
      dependencyType
      allowDelayedBinding
      group
      codeBase
      size
   >
      <assemblyIdentity
         name
         version
         processorArchitecture
         language
      >
         <hash>
            <dsig:Transforms>
               <dsig:Transform
                  Algorithm
            />
            </dsig:Transforms>
            <dsig:DigestMethod />
            <dsig:DigestValue>
            </dsig:DigestValue>
    </hash>

      </assemblyIdentity>
   </dependentAssembly>
</dependency>
```

## <a name="elements-and-attributes"></a>元素和屬性
 需要`dependency`元素。 同一個應用程式資訊清單`dependency`中可能有多個實例。

 `dependency`元素沒有屬性，且包含下列子專案。

### <a name="dependentos"></a>dependentOS
 選擇性。 `osVersionInfo`包含元素。 和專案互斥：一個或`dependency`另一個必須存在於元素，但不能同時為兩者。 `dependentAssembly` `dependentOS`

 `dependentOS`支援下列屬性。

|屬性|描述|
|---------------|-----------------|
|`supportUrl`|選擇性。 指定相依平臺的支援 URL。 如果找到必要的平臺，則會向使用者顯示此 URL。|
|`description`|選擇性。 以人類看得懂的形式，描述由`dependentOS`元素所描述的作業系統。|

### <a name="osversioninfo"></a>osVersionInfo
 必要項。 這個元素是 `dependentOS` 元素的子項，並包含 `os` 元素。 這個元素沒有屬性。

### <a name="os"></a>os
 必要項。 這個元素是 `osVersionInfo` 元素的子項。 這個項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`majorVersion`|必要項。 指定 OS 的主要版本號碼。|
|`minorVersion`|必要項。 指定 OS 的次要版本號碼。|
|`buildNumber`|必要項。 指定 OS 的組建編號。|
|`servicePackMajor`|必要項。 指定 OS 的 Service Pack 主要號碼。|
|`servicePackMinor`|選擇性。 指定 OS 的 Service Pack 次要號碼。|
|`productType`|選擇性。 識別產品類型值。 有效值為 `server`、`workstation` 及 `domainController`。 例如，針對 Windows 2000 Professional，此屬性值為`workstation`。|
|`suiteType`|選擇性。 識別系統上可用的產品套件，或系統的設定類型。 有效值為 `backoffice`、`blade`、`datacenter`、`enterprise`、`home`、`professional`、`smallbusiness`、`smallbusinessRestricted` 和 `terminal`。 例如，針對 Windows 2000 Professional，此屬性值為`professional`。|

### <a name="dependentassembly"></a>dependentAssembly
 選擇性。 `assemblyIdentity`包含元素。 和專案互斥：一個或`dependency`另一個必須存在於元素，但不能同時為兩者。 `dependentAssembly` `dependentOS`

 `dependentAssembly`具有下列屬性。

| 屬性 | 描述 |
|-----------------------| - |
| `dependencyType` | 必要項。 指定相依性類型。 有效值為 `preprequisite` 和 `install`。 元件會當做[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式的一部分進行安裝。 `install` 元件必須存在於全域組件快取（GAC）中， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式才能安裝。 `prerequisite` |
| `allowDelayedBinding` | 必要項。 指定是否可以在執行時間以程式設計方式載入元件。 |
| `group` | 選擇性。 如果屬性設定為`install`，則會指定只視需要安裝的已命名元件群組。 `dependencyType` 如需詳細資訊，請參閱[逐步解說：依需求使用設計工具以 ClickOnce 部署 API 下載組件](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)。<br /><br /> 如果設定為`framework` ， `dependencyType`且屬性設定為`prerequisite`，則會將元件指定為 .NET Framework 的一部分。 在 .NET Framework 4 和更新版本上安裝時，不會檢查此元件的全域 assembly 快取（GAC）。 |
| `codeBase` | 當屬性設定`dependencyType`為`install`時，這是必要的。 相依元件的路徑。 可以是絕對路徑，或相對於資訊清單之程式碼基底的路徑。 此路徑必須是有效的 URI，組件資訊清單才會是有效的。 |
| `size` | 當屬性設定`dependencyType`為`install`時，這是必要的。 相依元件的大小（以位元組為單位）。 |

### <a name="assemblyidentity"></a>assemblyIdentity
 必要項。 這個元素是 `dependentAssembly` 元素的子項，並具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`name`|必要項。 識別應用程式的名稱。|
|`version`|必要項。 以下列格式指定應用程式的版本號碼：`major.minor.build.revision`|
|`publicKeyToken`|選擇性。 指定16個字元的十六進位字串，表示用來簽署應用程式或`SHA-1`元件之公開金鑰雜湊值的最後8個位元組。 用來簽署目錄的公開金鑰必須是2048位或更多。|
|`processorArchitecture`|選擇性。 指定處理器。 有效的值`x86`為32位 windows 和`I64` 64 位 windows。|
|`language`|選擇性。 識別元件的兩個部分語言代碼，例如 EN-US。|

### <a name="hash"></a>雜湊
 元素是`assemblyIdentity`元素的選擇性子專案。 `hash` `hash` 項目沒有任何屬性。

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]會使用應用程式中所有檔案的演算法雜湊做為安全性檢查，以確保在部署後不會變更任何檔案。 如果未包含此元素，則不會執行此檢查。`hash` 因此，不建議`hash`省略元素。

### <a name="dsigtransforms"></a>dsig:Transforms
 元素是`hash`元素的必要子系。 `dsig:Transforms` `dsig:Transforms` 項目沒有任何屬性。

### <a name="dsigtransform"></a>dsig:Transform
 元素是`dsig:Transforms`元素的必要子系。 `dsig:Transform` `dsig:Transform` 項目具有下列屬性。

| 屬性 | 描述 |
|-------------| - |
| `Algorithm` | 用來計算此檔案摘要的演算法。 目前所使用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]的唯一值是`urn:schemas-microsoft-com:HashTransforms.Identity`。 |

### <a name="dsigdigestmethod"></a>dsig:DigestMethod
 元素是`hash`元素的必要子系。 `dsig:DigestMethod` `dsig:DigestMethod` 項目具有下列屬性。

| 屬性 | 描述 |
|-------------| - |
| `Algorithm` | 用來計算此檔案摘要的演算法。 目前所使用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]的唯一值是`http://www.w3.org/2000/09/xmldsig#sha1`。 |

### <a name="dsigdigestvalue"></a>dsig:DigestValue
 元素是`hash`元素的必要子系。 `dsig:DigestValue` `dsig:DigestValue` 項目沒有任何屬性。 其文字值是指定檔案的計算雜湊。

## <a name="remarks"></a>備註
 應用程式所使用的所有元件都必須有`dependency`對應的元素。 相依元件不包含必須在全域組件快取中預先安裝為平臺元件的元件。

## <a name="example"></a>範例
 下列[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]程式碼範例說明`dependency`應用程式資訊清單中的元素。 這個程式碼範例是針對[ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)主題提供之較大範例的一部分。

```xml
<dependency>
  <dependentOS>
    <osVersionInfo>
      <os
        majorVersion="4"
        minorVersion="10"
        buildNumber="0"
        servicePackMajor="0" />
    </osVersionInfo>
  </dependentOS>
</dependency>
<dependency>
  <dependentAssembly
    dependencyType="preRequisite"
    allowDelayedBinding="true">
    <assemblyIdentity
      name="Microsoft.Windows.CommonLanguageRuntime"
      version="4.0.20506.0" />
  </dependentAssembly>
</dependency>

<dependency>
  <dependentAssembly
    dependencyType="install"
    allowDelayedBinding="true"
    codebase="MyApplication.exe"
    size="4096">
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <hash>
      <dsig:Transforms>
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
      </dsig:Transforms>
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>
    </hash>
  </dependentAssembly>
</dependency>
```

## <a name="see-also"></a>另請參閱
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
- [\<dependency > 元素](../deployment/dependency-element-clickonce-deployment.md)