---
title: Office 方案的部署資訊清單
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], deployment manifests
- deployment manifests [Office development in Visual Studio]
- manifests [Office development in Visual Studio], deployment
- Office development in Visual Studio, deployment manifests
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3c96f0d87f5a49add1f0e8cebb61bab9659277e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62972391"
---
# <a name="deployment-manifests-for-office-solutions"></a>Office 方案的部署資訊清單
  部署資訊清單是 XML 檔案，說明 Office 方案的部署設定，以及識別目前的應用程式版本。

 使用 Visual Studio 中的 Office 程式開發[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]中定義的部署資訊清單結構描述[ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)參考。

## <a name="remarks"></a>備註
 Office 方案的部署資訊清單檔會識別目前的版本和其他部署設定。 它會參考應用程式資訊清單，並說明解決方案和解決方案中的所有檔案中的目前版本。

## <a name="file-name-syntax"></a>檔案名稱語法
 部署資訊清單檔案名稱必須以結尾 *.vsto*延伸模組。 雖然它是一種標準[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]部署資訊清單中，若要啟用 Visual Studio Tools for Office 執行階段來處理檔案不同的延伸模組。

## <a name="example"></a>範例
 下列程式碼範例說明 Visual Studio Tools for Office 方案的部署資訊清單。

```xml
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly
  xsi:schemaLocation=
    "urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig="http://www.w3.org/2000/09/xmldsig#"
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <assemblyIdentity
    name="ContosoOfficeSolutions.vsto"
    version="1.0.0.0"
    publicKeyToken="25d0f3ca94156f1f"
    language="neutral"
    processorArchitecture="msil"
    xmlns="urn:schemas-microsoft-com:asm.v1" />
  <description
    asmv2:publisher="Microsoft"
    asmv2:product="ContosoOfficeSolutions"
    xmlns="urn:schemas-microsoft-com:asm.v1" />
  <deployment install="false" mapFileExtensions="true" />
  <dependency>
    <dependentAssembly
      dependencyType="install"
      codebase="ContosoOfficeSolutions.dll.manifest"
      size="13545">
      <assemblyIdentity
        name="ContosoOfficeSolutions.dll"
        version="1.0.0.0"
        publicKeyToken="25d0f3ca94156f1f"
        language="neutral"
        processorArchitecture="msil"
        type="win32" />
      <hash>
        <dsig:Transforms>
          <dsig:Transform Algorithm=
            "urn:schemas-microsoft-com:HashTransforms.Identity" />
        </dsig:Transforms>
        <dsig:DigestMethod Algorithm=
          "http://www.w3.org/2000/09/xmldsig#sha1" />
        <dsig:DigestValue>PoY</dsig:DigestValue>
      </hash>
    </dependentAssembly>
  </dependency>
  <publisherIdentity name="name" issuerKeyHash="003" />
<Signature
  Id="StrongNameSignature"
  xmlns="http://www.w3.org/2000/09/xmldsig#">
  <SignedInfo>
    <CanonicalizationMethod Algorithm=
      "http://www.w3.org/2001/10/xml-exc-c14n#" />
  <SignatureMethod Algorithm=
    "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />
    <Reference URI="">
      <Transforms>
        <Transform Algorithm=
          "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
        <Transform Algorithm=
          "http://www.w3.org/2001/10/xml-exc-c14n#" />
      </Transforms>
      <DigestMethod Algorithm=
        "http://www.w3.org/2000/09/xmldsig#sha1" />
      <DigestValue>5oz</DigestValue>
    </Reference>
  </SignedInfo>
  <SignatureValue>nNG</SignatureValue>
  <KeyInfo Id="StrongNameKeyInfo">
    <KeyValue>
      <RSAKeyValue>
        <Modulus>ufI</Modulus>
        <Exponent>AQAB</Exponent>
      </RSAKeyValue>
    </KeyValue>
    <msrel:RelData
      xmlns:msrel=
        "http://schemas.microsoft.com/windows/rel/2005/reldata">
      <r:license
        xmlns:r="urn:mpeg:mpeg21:2003:01-REL-R-NS"
        xmlns:as=
          "http://schemas.microsoft.com/windows/pki/2005/Authenticode">
        <r:grant>
          <as:ManifestInformation
            Hash="099"
            Description=""
            Url="">
            <as:assemblyIdentity
              name="ContosoOfficeSolutions.vsto"
              version="1.0.0.0"
              publicKeyToken="25d0f3ca94156f1f"
              language="neutral"
              processorArchitecture="msil"
              xmlns="urn:schemas-microsoft-com:asm.v1" />
          </as:ManifestInformation>
          <as:SignedBy />
          <as:AuthenticodePublisher>
            <as:X509SubjectName>CN=DDNET\BAAdmin</as:X509SubjectName>
          </as:AuthenticodePublisher>
        </r:grant>
        <r:issuer>
          <Signature
            Id="AuthenticodeSignature"
            xmlns="http://www.w3.org/2000/09/xmldsig#">
            <SignedInfo>
              <CanonicalizationMethod
                Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" />
              <SignatureMethod
                Algorithm=
                  "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />
              <Reference URI="">
                <Transforms>
                  <Transform Algorithm=
                    "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
                  <Transform Algorithm=
                    "http://www.w3.org/2001/10/xml-exc-c14n#" />
                </Transforms>
                <DigestMethod
                  Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
                <DigestValue>iAd</DigestValue>
              </Reference>
            </SignedInfo>
            <SignatureValue>HL9</SignatureValue>
            <KeyInfo>
              <KeyValue>
                <RSAKeyValue>
                  <Modulus>ufI</Modulus>
                  <Exponent>AQAB</Exponent>
                </RSAKeyValue>
              </KeyValue>
              <X509Data>
                <X509Certificate>MII</X509Certificate>
              </X509Data>
            </KeyInfo>
          </Signature>
        </r:issuer>
      </r:license>
    </msrel:RelData>
  </KeyInfo>
</Signature>
</asmv1:assembly>
```

## <a name="see-also"></a>另請參閱

- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)