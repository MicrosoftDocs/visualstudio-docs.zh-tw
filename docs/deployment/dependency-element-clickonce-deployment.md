---
title: '&lt;&gt; (ClickOnce 部署) 的相依性元素 |Microsoft Docs'
description: Dependency 元素會識別要安裝的應用程式版本，以及應用程式資訊清單的位置。
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
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 172f3ea546565554c5f0701b81a88b9ca99b4100
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881096"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;&gt; (ClickOnce 部署) 的相依性元素
識別要安裝的應用程式版本，以及應用程式資訊清單的位置。

## <a name="syntax"></a>Syntax

```xml

      <dependency>
   <dependentAssembly
      preRequisite
      visible
      dependencyType
      codeBase
      size
   >
      <assemblyIdentity
         name
         version
         publicKeyToken
         processorArchitecture
         language
         type
      />
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

   </dependentAssembly>
</dependency>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `dependency`需要元素。 它沒有任何屬性。 部署資訊清單可以有多個 `dependency` 元素。

 `dependency`元素通常會針對應用程式中包含的元件，表示主要應用程式的相依性 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 如果您的 Main.exe 應用程式使用稱為 DotNetAssembly.dll 的元件，則該元件必須列在相依性區段中。 不過，相依性也可以表示其他類型的相依性，例如特定 common language runtime 版本的相依性、全域組件快取中的元件 (GAC) 或 COM 物件。 因為這是一項無接觸的部署技術，所以 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 無法起始這些相依性類型的下載和安裝，但如果有一或多個指定的相依性不存在，就會導致應用程式無法執行。

## <a name="dependentassembly"></a>dependentAssembly
 必要。 這個元素包含 `assemblyIdentity` 元素。 下表顯示支援的屬性 `dependentAssembly` 。

| 屬性 | 描述 |
|------------------| - |
| `preRequisite` | 選擇性。 指定此元件應該已經存在於 GAC 中。 有效值為 `true` 和 `false`。 如果為 `true` ，而且指定的元件不存在於 GAC 中，應用程式將無法執行。 |
| `visible` | 選擇性。 識別最上層應用程式身分識別，包括其相依性。 在內部用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 來管理應用程式的儲存和啟用。 |
| `dependencyType` | 必要。 這項相依性和應用程式之間的關聯性。 有效值為：<br /><br /> -   `install`. 元件代表與目前應用程式不同的安裝。<br />-   `preRequisite`. 目前的應用程式需要元件。 |
| `codebase` | 選擇性。 應用程式資訊清單的完整路徑。 |
| `size` | 選擇性。 應用程式資訊清單的大小（以位元組為單位）。 |

## <a name="assemblyidentity"></a>assemblyIdentity
 必要。 這個元素是 `dependentAssembly` 元素的子項。 的內容 `assemblyIdentity` 必須與 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單中所述的內容相同。 下表顯示元素的屬性 `assemblyIdentity` 。

|屬性|描述|
|---------------|-----------------|
|`Name`|必要。 識別應用程式的名稱。|
|`Version`|必要。 以下列格式指定應用程式的版本號碼： `major.minor.build.revision`|
|`publicKeyToken`|必要。 指定16個字元的十六進位字串，表示用來簽署應用程式或元件之公開金鑰的 SHA-1 雜湊最後8個位元組。 用來簽署的公開金鑰必須是2048位或更高的版本。|
|`processorArchitecture`|必要。 指定微處理器。 有效的值 `x86` 適用于32位 windows 和 `IA64` 64 位 windows。|
|`Language`|選擇性。 識別元件的兩個部分語言代碼。 例如，EN-US，代表美式英文 (US ) 。 預設為 `neutral`。 此元素位於 `asmv2` 命名空間中。|
|`type`|選擇性。 可回溯相容于 Windows 並存安裝技術。 唯一允許的值為 `win32` 。|

## <a name="hash"></a>雜湊
 `hash`元素是元素的選擇性子專案 `file` 。 `hash` 項目沒有任何屬性。

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用應用程式中所有檔案的演算法雜湊做為安全性檢查，以確保在部署後不會變更任何檔案。 如果 `hash` 未包含此元素，則不會執行這項檢查。 因此， `hash` 不建議省略元素。

## <a name="dsigtransforms"></a>dsig:Transforms
 專案 `dsig:Transforms` 是專案的必要子項目 `hash` 。 `dsig:Transforms` 項目沒有任何屬性。

## <a name="dsigtransform"></a>dsig:Transform
 專案 `dsig:Transform` 是專案的必要子項目 `dsig:Transforms` 。 下表顯示元素的屬性 `dsig:Transform` 。

| 屬性 | 描述 |
|-------------| - |
| `Algorithm` | 用來計算此檔案摘要的演算法。 目前唯一使用的值 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 為 `urn:schemas-microsoft-com:HashTransforms.Identity` 。 |

## <a name="dsigdigestmethod"></a>dsig:DigestMethod
 專案 `dsig:DigestMethod` 是專案的必要子項目 `hash` 。 下表顯示元素的屬性 `dsig:DigestMethod` 。

| 屬性 | 描述 |
|-------------| - |
| `Algorithm` | 用來計算此檔案摘要的演算法。 目前唯一使用的值 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 為 `http://www.w3.org/2000/09/xmldsig#sha1` 。 |

## <a name="dsigdigestvalue"></a>dsig:DigestValue
 專案 `dsig:DigestValue` 是專案的必要子項目 `hash` 。 `dsig:DigestValue` 項目沒有任何屬性。 它的文字值是指定之檔案的計算雜湊。

## <a name="remarks"></a>備註
 部署資訊清單通常會有一個 `assemblyIdentity` 識別應用程式資訊清單名稱和版本的單一元素。

## <a name="example-1"></a>範例 1
 下列程式碼範例顯示 `dependency` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署資訊清單中的元素。

```xml
<!-- Identify the assembly dependencies -->
<dependency>
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />
    <hash>
      <dsig:Transforms>
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
      </dsig:Transforms>
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>
    </hash>
  </dependentAssembly>
</dependency>
```

## <a name="example-2"></a>範例 2
 下列程式碼範例會指定已安裝在 GAC 中之元件的相依性。

```xml
<dependency>
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />
  </dependentAssembly>
</dependency>
```

## <a name="example-3"></a>範例 3
 下列程式碼範例會針對特定版本的 common language runtime 指定相依性。

```xml
<dependency>
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />
  </dependentAssembly>
</dependency>
```

## <a name="example-4"></a>範例 4
 下列程式碼範例會指定作業系統相依性。

```xml
<dependency>
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">
      <osVersionInfo>
         <os majorVersion="4" minorVersion="10" />
      </osVersionInfo>
   </dependentOS>
</dependency>
```

## <a name="see-also"></a>另請參閱
- [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)
- [\<dependency> 元素](../deployment/dependency-element-clickonce-application.md)