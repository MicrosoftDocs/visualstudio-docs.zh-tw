---
title: '&lt;&gt;ClickOnce 部署 (的 Signature 元素) |Microsoft Docs'
description: Signature 元素包含數位簽署此部署資訊清單所需的資訊。 簽署部署資訊清單是選擇性的，但建議使用。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5d95398285d9106719f3c2444d54202b81cfee4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877495"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;&gt;ClickOnce 部署 (的 Signature 元素) 
包含對此部署資訊清單進行數位簽章時所需的資訊。

## <a name="syntax"></a>語法

```xml

<Signature> 
   XML signature information 
</Signature>
```

## <a name="remarks"></a>備註
 使用信封簽章簽署部署資訊清單是選擇性的，但建議使用。 如需有關簽署 XML 檔案的詳細資訊，請參閱中所述的「XML 簽章語法和處理」全球資訊網協會建議 [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/) 。

 如果您想要簽署資訊清單，則必須提供所有檔案的雜湊。 因為使用者無法驗證未雜湊檔案的內容，所以無法簽署具有未雜湊之檔案的資訊清單。

## <a name="example"></a>範例
 下列程式碼範例說明 `Signature` 部署中使用的部署資訊清單中的元素 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。

```xml
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
  <SignedInfo>
    <CanonicalizationMethod Algorithm=
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />
    <SignatureMethod Algorithm=
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />
    <Reference URI="">
      <Transforms>
        <Transform Algorithm=
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
      </Transforms>
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <DigestValue>d2z5AE...</DigestValue>
    </Reference>
  </SignedInfo>
  <SignatureValue>
4PHj6SaopoLp...
  </SignatureValue>
  <KeyInfo>
    <X509Data>
      <X509Certificate>
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...
      </X509Certificate>
    </X509Data>
  </KeyInfo>
</Signature>
```

## <a name="see-also"></a>另請參閱
- [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)
