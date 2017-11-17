---
title: "&lt;assemblyIdentity&gt;元素 （ClickOnce 應用程式） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: "20"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: db313077fa7903b2bdb2fbbe6b76aa80c940fecd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity&gt;元素 （ClickOnce 應用程式）
識別應用程式部署在[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署。  
  
## <a name="syntax"></a>語法  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `assemblyIdentity`項目為必要。 它包含沒有子項目，並具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Name`|必要項。 識別應用程式的名稱。<br /><br /> 如果`Name`包含特殊字元，例如單引號或雙引號括應用程式可能會無法啟動。|  
|`Version`|必要項。 指定應用程式的版本號碼，格式如下：`major.minor.build.revision`|  
|`publicKeyToken`|選擇項。 指定 16 個字元的十六進位字串，表示最後 8 個位元組`SHA-1`簽署的應用程式或組件之公開金鑰的雜湊值。 公開金鑰用來簽署類別目錄必須是 2048 位元或更高。<br /><br /> 雖然建議您簽署組件，但選擇性的這是必要屬性。 如果組件是不帶正負號，您應該從自我簽署的組件複製的值，或使用"dummy"值為全部為零。|  
|`processorArchitecture`|必要項。 指定處理器。 有效值為`msil`適用於所有處理器，`x86`適用於 32 位元 Windows`IA64`適用於 64 位元 Windows 和`Itanium`Intel 64 位元 Itanium 處理器。|  
|`language`|必要項。 識別兩部分語言代碼 (例如， `en-US`) 的組件。 此元素為`asmv2`命名空間。 如果未指定，預設值是`neutral`。|  
  
## <a name="examples"></a>範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明`assemblyIdentity`中的項目[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單。 這個程式碼範例是中提供之較大範例的一部分[ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)。  
  
### <a name="code"></a>程式碼  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity > 項目](../deployment/assemblyidentity-element-clickonce-deployment.md)