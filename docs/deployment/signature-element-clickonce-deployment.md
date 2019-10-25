---
title: '&lt;Signature&gt; 元素（ClickOnce 部署） |Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f69dcec6bbee5358184b74a71274cb26e4de60b3
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806841"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Signature&gt; 元素（ClickOnce 部署）
包含對此部署資訊清單進行數位簽章時所需的資訊。

## <a name="syntax"></a>語法

```xml

      <Signature> 
   XML signature information 
</Signature>
```

## <a name="remarks"></a>備註
 使用信封簽名來簽署部署資訊清單是選擇性的，但建議使用。 如需有關簽署 XML 檔案的詳細資訊，請參閱[http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/)所述的全球資訊網協會建議的「xml 簽章語法和處理」。

 如果您想要簽署資訊清單，則必須提供所有檔案的雜湊。 無法簽署含有未雜湊之檔案的資訊清單，因為使用者無法確認未雜湊檔案的內容。

## <a name="example"></a>範例
 下列程式碼範例說明 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署中所使用之部署資訊清單中的 `Signature` 元素。

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

## <a name="see-also"></a>請參閱
- [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)