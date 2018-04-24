---
title: ClickOnce 部署資訊清單 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce, deployment manifests
- deployment manifests [ClickOnce]
ms.assetid: 8457e615-e3b6-4990-8dcf-11bc590e4e9b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dd67f3db61662535a0a8522575e716886602f5b7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="clickonce-deployment-manifest"></a>ClickOnce 部署資訊清單
部署資訊清單是 XML 檔案，描述 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署，包括要部署的目前 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式版本之識別。  
  
 部署資訊清單具有下列項目和屬性。  
  
|項目|描述|屬性|  
|-------------|-----------------|----------------|  
|[\<組件 > 項目](../deployment/assembly-element-clickonce-deployment.md)|必要。 最上層項目。|`manifestVersion`|  
|[\<assemblyIdentity > 項目](../deployment/assemblyidentity-element-clickonce-deployment.md)|必要。 識別此 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的應用程式資訊清單。|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `culture`|  
|[\<描述 > 項目](../deployment/description-element-clickonce-deployment.md)|必要。 識別應用程式資訊用於建立 shell 的存在和**新增或移除程式**控制台 中的項目。|`publisher`<br /><br /> `product`<br /><br /> `supportUrl`|  
|[\<部署 > 項目](../deployment/deployment-element-clickonce-deployment.md)|選擇性。 識別用於更新部署及公開至系統的屬性。|`install`<br /><br /> `minimumRequiredVersion`<br /><br /> `mapFileExtensions`<br /><br /> `disallowUrlActivation`<br /><br /> `trustUrlParameters`|  
|[\<w > 項目](../deployment/compatibleframeworks-element-clickonce-deployment.md)|必要。 識別安裝及執行此應用程式所需的 .NET Framework 版本。|`SupportUrl`|  
|[\<相依性 > 項目](../deployment/dependency-element-clickonce-deployment.md)|必要。 識別部署所要安裝的應用程式版本，以及應用程式資訊清單的位置。|`preRequisite`<br /><br /> `visible`<br /><br /> `dependencyType`<br /><br /> `codebase`<br /><br /> `size`|  
|[\<publisherIdentity > 項目](../deployment/publisheridentity-element-clickonce-deployment.md)|簽署資訊清單的必要項。 包含簽署此部署資訊清單之發行者的資訊。|`Name`<br /><br /> `issuerKeyHash`|  
|[\<簽章 > 項目](../deployment/signature-element-clickonce-deployment.md)|選擇性。 包含對此部署資訊清單進行數位簽章時所需的資訊。|無|  
|[\<customErrorReporting > 項目](../deployment/customerrorreporting-element-clickonce-deployment.md)|選擇性。 指定要在錯誤發生時顯示的 URI。|URI|  
  
## <a name="remarks"></a>備註  
 部署資訊清單檔會識別 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式部署，包含目前的版本與其他部署設定。 這會參考應用程式資訊清單，其中描述此應用程式的目前版本和部署內包含的所有檔案。  
  
 如需詳細資訊，請參閱 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)。  
  
## <a name="file-location"></a>檔案位置  
 部署資訊清單檔案會參考目前應用程式版本的正確應用程式資訊清單。 當您提供新版本的應用程式部署時，必須更新部署資訊清單才能參考新的應用程式資訊清單。  
  
 部署資訊清單檔必須以強式名稱的方式命名，同時也可以包含發行者驗證的憑證。  
  
## <a name="file-name-syntax"></a>檔名語法  
 部署資訊清單的檔名必須以 .application 副檔名做為結尾。  
  
## <a name="examples"></a>範例  
 下列程式碼範例會說明部署資訊清單。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
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
  <assemblyIdentity   
    name="My Application Deployment.app"  
    version="1.0.0.0"  
    publicKeyToken="43cb1e8e7a352766"  
    language="neutral"  
    processorArchitecture="x86"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <description  
    asmv2:publisher="My Company Name"  
    asmv2:product="My Application"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <deployment install="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="0" unit="days" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="\\myServer\sampleDeployment\MyApplicationDeployment.application" />  
  </deployment>  
  <compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
    <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.20506" />  
    <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.20506" />  
  </compatibleFrameworks>  
  <dependency>  
    <dependentAssembly  
      dependencyType="install"  
      codebase="1.0.0.0\My Application Deployment.exe.manifest"  
      size="6756">  
      <assemblyIdentity  
        name="My Application Deployment.exe"  
        version="1.0.0.0"  
        publicKeyToken="43cb1e8e7a352766"  
        language="neutral"  
        processorArchitecture="x86"  
        type="win32" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>E506x9FwNauks7UjQywmzgtd3FE=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAIN\MyUsername" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
...  
</Signature></asmv1:assembly>  
```  
  
## <a name="see-also"></a>另請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)