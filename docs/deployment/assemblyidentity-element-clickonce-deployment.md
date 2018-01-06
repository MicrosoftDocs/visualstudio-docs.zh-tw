---
title: "&lt;assemblyIdentity&gt;元素 （ClickOnce 部署） |Microsoft 文件"
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
helpviewer_keywords: <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: "23"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 51643b8db91c9f8c2961b319d47cdfb7789f6a4d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity&gt;元素 （ClickOnce 部署）
識別主要組件的[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。  
  
## <a name="syntax"></a>語法  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `assemblyIdentity`項目為必要。 它包含沒有子項目，並具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`name`|必要。 識別部署的人類看得懂的名稱僅供參考之用。<br /><br /> 如果`name`包含特殊字元，例如單引號或雙引號括應用程式可能會無法啟動。|  
|`version`|必要。 指定的版本號碼的組件，以下列格式： `major.minor.build.revision`。<br /><br /> 此值必須遞增觸發應用程式更新的更新資訊清單中。|  
|`publicKeyToken`|必要。 指定 16 個字元的十六進位字串，表示最後 8 個位元組用以簽署部署資訊清單的公開金鑰的 sha-1 雜湊值。 用於簽章的公開金鑰必須是 2048 位元或更高。<br /><br /> 雖然建議您簽署組件，但選擇性的這是必要屬性。 如果組件是不帶正負號，您應該從自我簽署的組件複製的值，或使用"dummy"值為全部為零。|  
|`processorArchitecture`|必要。 指定處理器。 有效值為`msil`適用於所有處理器，`x86`適用於 32 位元 Windows`IA64`適用於 64 位元 Windows 和`Itanium`Intel 64 位元 Itanium 處理器。|  
|`type`|必要。 與 Windows-並存安裝技術相容。 唯一允許的值是`win32`。|  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列程式碼範例說明`assemblyIdentity`中的項目[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署資訊清單。 這個程式碼範例是針對所提供之較大範例的一部分[ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)主題。  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>請參閱  
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity > 項目](../deployment/assemblyidentity-element-clickonce-application.md)