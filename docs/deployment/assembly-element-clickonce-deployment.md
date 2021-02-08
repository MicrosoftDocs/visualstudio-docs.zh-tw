---
title: '&lt;&gt; (ClickOnce 部署的元件元素) |Microsoft Docs'
description: Assembly 元素是根項目，而且是 ClickOnce 部署中的必要專案。 其第一個包含的元素必須是 assemblyIdentity 元素。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b7838e0a212bbc1e743783255106bb44561fbe62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837758"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;&gt;ClickOnce 部署 (的 assembly 元素) 
部署資訊清單的最上層元素。

## <a name="syntax"></a>Syntax

```xml

      <assembly  
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `assembly`元素是根項目，而且是必要專案。 其第一個包含的元素必須是 `assemblyIdentity` 元素。 資訊清單元素必須位於下列命名空間： `urn:schemas-microsoft-com:asm.v1` 、 `urn:schemas-microsoft-com:asm.v2` 和 `http://www.w3.org/2000/09/xmldsig#` 。 元件的子專案也必須位於這些命名空間中（透過繼承或標記）。

 `assembly` 項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`manifestVersion`|必要。 這個屬性必須設定為 `1.0` 。|

## <a name="example"></a>範例
 下列程式碼範例說明 `assembly` 使用部署之應用程式的部署資訊清單中的元素 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 這個程式碼範例是針對 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md) 主題提供之較大範例的一部分。

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
```

## <a name="see-also"></a>另請參閱
- [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)
- [\<assembly> 元素](../deployment/assembly-element-clickonce-application.md)