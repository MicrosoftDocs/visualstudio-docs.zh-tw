---
title: '&lt;&gt; (ClickOnce 應用程式) 的相依性元素 |Microsoft Docs'
description: Dependency 專案會識別應用程式所需的平臺或元件相依性。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e716c0e9ebe88a8007296f1dad870424a0def0b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881109"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;&gt; (ClickOnce 應用程式) 的相依性元素
識別應用程式所需的平臺或元件相依性。

## <a name="syntax"></a>Syntax

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
 `dependency`需要元素。 `dependency`在相同的應用程式資訊清單中，可能會有多個實例。

 `dependency`元素沒有任何屬性，而且包含下列子項目。

### <a name="dependentos"></a>dependentOS
 選擇性。 包含 `osVersionInfo` 元素。 `dependentOS`和 `dependentAssembly` 元素是互斥的：一個或多個專案必須存在於 `dependency` 元素，但不能同時存在兩者。

 `dependentOS` 支援下列屬性。

|屬性|描述|
|---------------|-----------------|
|`supportUrl`|選擇性。 指定相依平臺的支援 URL。 如果找到必要的平臺，則會向使用者顯示此 URL。|
|`description`|選擇性。 描述以人們看得懂的形式，也就是元素所描述的作業系統 `dependentOS` 。|

### <a name="osversioninfo"></a>osVersionInfo
 必要。 這個元素是 `dependentOS` 元素的子項，並包含 `os` 元素。 這個元素沒有屬性。

### <a name="os"></a>os
 必要。 這個元素是 `osVersionInfo` 元素的子項。 這個項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`majorVersion`|必要。 指定作業系統的主要版本號碼。|
|`minorVersion`|必要。 指定 OS 的次要版本號碼。|
|`buildNumber`|必要。 指定 OS 的組建編號。|
|`servicePackMajor`|必要。 指定 OS 的 service pack 主要號碼。|
|`servicePackMinor`|選擇性。 指定 OS 的 service pack 次要號碼。|
|`productType`|選擇性。 識別產品類型值。 有效值是 `server`、`workstation` 和 `domainController`。 例如，針對 Windows 2000 Professional，這個屬性值為 `workstation` 。|
|`suiteType`|選擇性。 識別系統或系統的設定類型上可用的產品套件。 有效值為 `backoffice`、`blade`、`datacenter`、`enterprise`、`home`、`professional`、`smallbusiness`、`smallbusinessRestricted` 和 `terminal`。 例如，針對 Windows 2000 Professional，這個屬性值為 `professional` 。|

### <a name="dependentassembly"></a>dependentAssembly
 選擇性。 包含 `assemblyIdentity` 元素。 `dependentOS`和 `dependentAssembly` 元素是互斥的：一個或多個專案必須存在於 `dependency` 元素，但不能同時存在兩者。

 `dependentAssembly` 具有下列屬性。

| 屬性 | 描述 |
|-----------------------| - |
| `dependencyType` | 必要。 指定相依性類型。 有效值為 `preprequisite` 和 `install`。 `install`元件會安裝為應用程式的一部分 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 `prerequisite`元件必須存在於全域組件快取 (GAC) ， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式才能安裝。 |
| `allowDelayedBinding` | 必要。 指定是否可在執行時間以程式設計方式載入元件。 |
| `group` | 選擇性。 如果 `dependencyType` 屬性設定為，則 `install` 會指定只隨需安裝的命名元件群組。 如需詳細資訊，請參閱[逐步解說：下載組件隨選與 ClickOnce 部署應用程式開發介面使用設計工具](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)。<br /><br /> 如果設定為， `framework` 且 `dependencyType` 屬性設定為，則會將 `prerequisite` 元件指定為 .NET Framework 的一部分。 在 .NET Framework 4 和更新版本上安裝時，不會檢查此元件的 global assembly cache (GAC) 。 |
| `codeBase` | 當屬性設定為時，則為必要項 `dependencyType` `install` 。 相依元件的路徑。 可能是絕對路徑或相對於資訊清單程式碼基底的路徑。 此路徑必須是有效的 URI，才能讓組件資訊清單有效。 |
| `size` | 當屬性設定為時，則為必要項 `dependencyType` `install` 。 相依元件的大小（以位元組為單位）。 |

### <a name="assemblyidentity"></a>assemblyIdentity
 必要。 這個元素是 `dependentAssembly` 元素的子項，並具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`name`|必要。 識別應用程式的名稱。|
|`version`|必要。 以下列格式指定應用程式的版本號碼： `major.minor.build.revision`|
|`publicKeyToken`|選擇性。 指定16個字元的十六進位字串，表示用 `SHA-1` 來簽署應用程式或元件之公開金鑰雜湊值的最後8個位元組。 用來簽署目錄的公開金鑰必須是2048位或更多。|
|`processorArchitecture`|選擇性。 指定處理器。 有效的值 `x86` 適用于32位 windows 和 `I64` 64 位 windows。|
|`language`|選擇性。 識別元件的兩個部分語言代碼，例如 EN-US。|

### <a name="hash"></a>雜湊
 `hash`元素是元素的選擇性子專案 `assemblyIdentity` 。 `hash` 項目沒有任何屬性。

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用應用程式中所有檔案的演算法雜湊做為安全性檢查，以確保在部署後不會變更任何檔案。 如果 `hash` 未包含此元素，則不會執行這項檢查。 因此， `hash` 不建議省略元素。

### <a name="dsigtransforms"></a>dsig:Transforms
 專案 `dsig:Transforms` 是專案的必要子項目 `hash` 。 `dsig:Transforms` 項目沒有任何屬性。

### <a name="dsigtransform"></a>dsig:Transform
 專案 `dsig:Transform` 是專案的必要子項目 `dsig:Transforms` 。 `dsig:Transform` 項目具有下列屬性。

| 屬性 | 描述 |
|-------------| - |
| `Algorithm` | 用來計算此檔案摘要的演算法。 目前唯一使用的值 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 為 `urn:schemas-microsoft-com:HashTransforms.Identity` 。 |

### <a name="dsigdigestmethod"></a>dsig:DigestMethod
 專案 `dsig:DigestMethod` 是專案的必要子項目 `hash` 。 `dsig:DigestMethod` 項目具有下列屬性。

| 屬性 | 描述 |
|-------------| - |
| `Algorithm` | 用來計算此檔案摘要的演算法。 目前唯一使用的值 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 為 `http://www.w3.org/2000/09/xmldsig#sha1` 。 |

### <a name="dsigdigestvalue"></a>dsig:DigestValue
 專案 `dsig:DigestValue` 是專案的必要子項目 `hash` 。 `dsig:DigestValue` 項目沒有任何屬性。 它的文字值是指定之檔案的計算雜湊。

## <a name="remarks"></a>備註
 應用程式所使用的所有元件都必須有對應的 `dependency` 元素。 相依元件不包含必須預先安裝在全域組件快取中作為平臺元件的元件。

## <a name="example"></a>範例
 下列程式碼範例說明 `dependency` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單中的元素。 這個程式碼範例是針對 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md) 主題提供之較大範例的一部分。

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
- [\<dependency> 元素](../deployment/dependency-element-clickonce-deployment.md)