---
title: '&lt;&gt; (ClickOnce 應用程式) 的元件元素 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b629243920021adc3833f43f268f05638029dc7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900756"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;&gt;ClickOnce 應用程式)  (assembly 元素
應用程式資訊清單的最上層元素。

## <a name="syntax"></a>語法

```xml

      <assembly
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `assembly`元素是根項目，而且是必要專案。 其第一個包含的元素必須是 `assemblyIdentity` 元素。 資訊清單元素必須是下列其中一個命名空間：

 `urn:schemas-microsoft-com:asm.v1`

 `urn:schemas-microsoft-com:asm.v2`

 `http://www.w3.org/2000/09/xmldsig#`

 元件的子專案也必須位於這些命名空間中（透過繼承或標記）。

 `assembly` 項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`manifestVersion`|必要。 `manifestVersion`屬性必須設定為 `1.0` 。|

## <a name="example"></a>範例
 下列程式碼範例說明 `assembly` 應用程式之應用程式資訊清單中的元素 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 這個程式碼範例是 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)中所提供之較大範例的一部分。

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
```

## <a name="see-also"></a>另請參閱
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
- [\<assembly> 元素](../deployment/assembly-element-clickonce-deployment.md)
