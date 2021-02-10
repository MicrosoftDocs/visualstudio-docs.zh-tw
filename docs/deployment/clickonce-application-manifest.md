---
title: ClickOnce 應用程式資訊清單 |Microsoft Docs
description: 瞭解 ClickOnce 應用程式資訊清單，這是一個 XML 檔案，其中描述使用 ClickOnce 部署的應用程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application manifests [ClickOnce]
- ClickOnce, application manifests
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ccd8389859de3ffce7b04e2da648b2ac2e807a79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936180"
---
# <a name="clickonce-application-manifest"></a>ClickOnce 應用程式資訊清單
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單是 XML 檔案，描述使用部署的應用程式 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單具有下列元素和屬性。

| 元素 | 描述 | 屬性 |
| - | - | - |
| [\<assembly> 元素](../deployment/assembly-element-clickonce-application.md) | 必要。 最上層項目。 | `manifestVersion` |
| [\<assemblyIdentity> 元素](../deployment/assemblyidentity-element-clickonce-application.md) | 必要。 識別應用程式的主要元件 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language` |
| [\<trustInfo> 元素](../deployment/trustinfo-element-clickonce-application.md) | 識別應用程式安全性需求。 | 無 |
| [\<entryPoint> 元素](../deployment/entrypoint-element-clickonce-application.md) | 必要。 識別應用程式程式碼進入點。 | `name` |
| [\<dependency> 元素](../deployment/dependency-element-clickonce-application.md) | 必要。 識別執行應用程式所需的每個相依性。 選擇性地識別需要預先安裝的組件。 | 無 |
| [\<file> 元素](../deployment/file-element-clickonce-application.md) | 選擇性。 識別應用程式所使用的每個 nonassembly 檔。 可以包含與檔案相關聯的元件物件模型 (COM) 隔離資料。 | `name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType` |
| [\<fileAssociation> 元素](../deployment/fileassociation-element-clickonce-application.md) | 選擇性。 識別要與應用程式相關聯的副檔名。 | `extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon` |

## <a name="remarks"></a>備註
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單檔會識別使用部署的應用程式 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 如需 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 的詳細資訊，請參閱 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)。

## <a name="file-location"></a>檔案位置
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單專門用於單一版本的部署。 基於這個理由，應該與部署資訊清單分開儲存它們。 常見的慣例是將它們放在以相關聯版本命名的子目錄中。

 應用程式資訊清單一律必須在部署前簽署。 如果您手動變更應用程式資訊清單，您必須使用 *mage.exe* 重新簽署應用程式資訊清單、更新部署資訊清單，然後重新簽署部署資訊清單。 如需詳細資訊，請參閱 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。

## <a name="file-name-syntax"></a>檔案名稱語法
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單檔案的名稱應該是 `assemblyIdentity` 項目中識別的應用程式完整名稱和副檔名，後面接著副檔名 *.manifest*。 例如，參考 *Example.exe* 應用程式的應用程式資訊清單會使用下列檔案名語法。

 `example.exe.manifest`

## <a name="example"></a>範例
 下列程式碼範例會顯示應用程式的應用程式資訊清單 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。

```xml
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
  <asmv1:assemblyIdentity name="My Application Deployment.exe" version="1.0.0.0" publicKeyToken="43cb1e8e7a352766" language="neutral" processorArchitecture="x86" type="win32" />
  <application />
  <entryPoint>
    <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
  <trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet Unrestricted="true" ID="Custom" SameSite="site" />
        <defaultAssemblyRequest permissionSetReference="Custom" />
      </applicationRequestMinimum>
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">
        <!--
          UAC Manifest Options
          If you want to change the Windows User Account Control level replace the
          requestedExecutionLevel node with one of the following.

        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />

         If you want to utilize File and Registry Virtualization for backward
         compatibility then delete the requestedExecutionLevel node.
    -->
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />
      </requestedPrivileges>
    </security>
  </trustInfo>
  <dependency>
    <dependentOS>
      <osVersionInfo>
        <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
      </osVersionInfo>
    </dependentOS>
  </dependency>
  <dependency>
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
      <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.20506.0" />
    </dependentAssembly>
  </dependency>
  <dependency>
    <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="4096">
      <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />
      <hash>
        <dsig:Transforms>
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
        </dsig:Transforms>
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
        <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>
      </hash>
    </dependentAssembly>
  </dependency>
<publisherIdentity name="CN=DOMAINCONTROLLER\UserMe" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">
...
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>
```

## <a name="see-also"></a>另請參閱
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)