---
title: '&lt;簽章&gt;項目 （ClickOnce 部署） |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df18b63ff306525cba74ef0932c97edd64eee797
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942128"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;簽章&gt;項目 （ClickOnce 部署）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

包含對此部署資訊清單進行數位簽章時所需的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>備註  
 使用包裹簽章為部署資訊清單簽署是選擇性的但建議使用。 如需有關簽署 XML 檔案，請參閱全球資訊網協會建議事項 「 XML 簽章語法和處理，」 所述[ http://www.w3.org/TR/xmldsig-core/ ](http://www.w3.org/TR/xmldsig-core/)。  
  
 如果您想要登入您的資訊清單，就必須提供雜湊的所有檔案。 無法簽署資訊清單的檔案，不會進行雜湊，因為使用者無法驗證雜湊檔案的內容。  
  
## <a name="example"></a>範例  
 下列程式碼範例說明`Signature`中所使用的部署資訊清單中的項目[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]部署。  
  
```  
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
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)
