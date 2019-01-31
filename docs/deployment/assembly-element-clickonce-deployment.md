---
title: '&lt;組件&gt;項目 （ClickOnce 部署） |Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e6192c7705555e817ed82d452d703f0affd9609
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932697"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;組件&gt;項目 （ClickOnce 部署）
部署資訊清單最上層項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>元素和屬性  
 `assembly`元素是根項目，且需要。 必須是其第一個包含的項目`assemblyIdentity`項目。 資訊清單的項目必須位於下列命名空間： `urn:schemas-microsoft-com:asm.v1`， `urn:schemas-microsoft-com:asm.v2`，和`http://www.w3.org/2000/09/xmldsig#`。 組件的子項目也必須是這些命名空間，繼承或標記。  
  
 `assembly` 項目具有下列屬性。  
  
|屬性|說明|  
|---------------|-----------------|  
|`manifestVersion`|必要項。 此屬性必須設為`1.0`。|  
  
## <a name="example"></a>範例  
 下列程式碼範例說明`assembly`部署使用的應用程式的部署資訊清單中的項目[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]。 此程式碼範例是針對提供之較大範例的一部分[ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)主題。  
  
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
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)   
 [\<組件 > 項目](../deployment/assembly-element-clickonce-application.md)