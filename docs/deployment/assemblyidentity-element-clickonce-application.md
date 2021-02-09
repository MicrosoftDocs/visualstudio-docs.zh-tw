---
title: '&lt;&gt;ClickOnce 應用程式)  (assemblyIdentity 元素 |Microsoft Docs'
description: ClickOnce 應用程式中需要 assemblyIdentity 元素。 它不包含任何子項目，而且具有本文所述的屬性。
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
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 92b5c1d323634bbb242cdccb54890908d5668803
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911388"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;&gt;ClickOnce 應用程式)  (assemblyIdentity 元素
識別部署在部署中的應用程式 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。

## <a name="syntax"></a>Syntax

```xml

      <assemblyIdentity
   name
   version
   publicKeyToken
   processorArchitecture
   language
/>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `assemblyIdentity`需要元素。 它不包含任何子項目，而且具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`Name`|必要。 識別應用程式的名稱。<br /><br /> 如果 `Name` 包含特殊字元，例如單引號或雙引號，則應用程式可能無法啟動。|
|`Version`|必要。 以下列格式指定應用程式的版本號碼： `major.minor.build.revision`|
|`publicKeyToken`|選擇性。 指定16個字元的十六進位字串，表示用 `SHA-1` 來簽署應用程式或元件之公開金鑰雜湊值的最後8個位元組。 用來簽署目錄的公開金鑰必須是2048位或更高的版本。<br /><br /> 雖然建議簽署元件，但卻是選擇性的，但這是必要屬性。 如果元件未簽署，您應該從自我簽署的元件複製值，或使用所有零的「虛擬」值。|
|`processorArchitecture`|必要。 指定處理器。 有效的值適用 `msil` 于所有處理器、 `x86` 32 位 windows、 `IA64` 64 位 windows 和 `Itanium` Intel 64 位 Itanium 處理器。|
|`language`|必要。 識別兩個部分的語言代碼 (例如， `en-US` 元件的) 。 此元素位於 `asmv2` 命名空間中。 如果未指定，預設值為 `neutral` 。|

## <a name="examples"></a>範例

### <a name="description"></a>描述
 下列程式碼範例說明 `assemblyIdentity` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單中的元素。 這個程式碼範例是 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)中所提供之較大範例的一部分。

### <a name="code"></a>程式碼

```xml
<asmv1:assemblyIdentity
  name="My Application Deployment.exe"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  type="win32" />
```

## <a name="see-also"></a>另請參閱
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
- [\<assemblyIdentity> 元素](../deployment/assemblyidentity-element-clickonce-deployment.md)