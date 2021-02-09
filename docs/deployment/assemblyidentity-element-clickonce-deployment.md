---
title: '&lt;assemblyIdentity &gt; 元素 (ClickOnce 部署) |Microsoft Docs'
description: ClickOnce 部署中需要 assemblyIdentity 元素。 它不包含任何子項目，而且具有本文所述的屬性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bc689c80d033c6b92178f020c0d3273f6ec86ca7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911353"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;&gt;ClickOnce 部署 (的 assemblyIdentity 元素) 
識別應用程式的主要元件 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。

## <a name="syntax"></a>Syntax

```xml

      <assemblyIdentity  
   name 
   version
   publicKeyToken
   processorArchitecture
    type
/>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `assemblyIdentity`需要元素。 它不包含任何子項目，而且具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`name`|必要。 識別部署的人類可讀取名稱，以供參考之用。<br /><br /> 如果 `name` 包含特殊字元，例如單引號或雙引號，則應用程式可能無法啟動。|
|`version`|必要。 指定元件的版本號碼，格式如下： `major.minor.build.revision` 。<br /><br /> 此值必須在更新的資訊清單中遞增，以觸發應用程式更新。|
|`publicKeyToken`|必要。 指定16個字元的十六進位字串，表示用來簽署部署資訊清單之公開金鑰的 SHA-1 雜湊值最後8個位元組。 用來簽署的公開金鑰必須是2048位或更高的版本。<br /><br /> 雖然建議簽署元件，但卻是選擇性的，但這是必要屬性。 如果元件未簽署，您應該從自我簽署的元件複製值，或使用所有零的「虛擬」值。|
|`processorArchitecture`|必要。 指定處理器。 有效的值適用 `msil` 于所有處理器、 `x86` 32 位 windows、 `IA64` 64 位 windows 和 `Itanium` Intel 64 位 Itanium 處理器。|
|`type`|必要。 與 Windows 並存安裝技術的相容性。 唯一允許的值為 `win32` 。|

## <a name="remarks"></a>備註

## <a name="example"></a>範例
 下列程式碼範例說明 `assemblyIdentity` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署資訊清單中的元素。 這個程式碼範例是針對 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md) 主題提供之較大範例的一部分。

```xml
<!-- Identify the deployment. -->
<assemblyIdentity
  name="My Application Deployment.app"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>另請參閱
- [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)
- [\<assemblyIdentity> 元素](../deployment/assemblyidentity-element-clickonce-application.md)