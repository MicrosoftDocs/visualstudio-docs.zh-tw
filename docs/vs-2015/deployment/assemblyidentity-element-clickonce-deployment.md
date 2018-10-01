---
title: '&lt;assemblyIdentity&gt;項目 （ClickOnce 部署） |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 4b1f5a0dbf056925b4f2a25356759dccacc3b363
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485089"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity&gt;項目 （ClickOnce 部署）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[ &lt;assemblyIdentity&gt;項目 （ClickOnce 部署）](https://docs.microsoft.com/visualstudio/deployment/assemblyidentity-element-clickonce-deployment)。  
  
識別主要組件的[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式。  
  
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
 `assemblyIdentity`是必要元素。 它包含沒有子項目，並具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`name`|必要。 識別部署的人類看得懂的名稱僅供參考之用。<br /><br /> 如果`name`包含特殊字元，例如單引號或雙引號括住，應用程式可能無法啟動。|  
|`version`|必要。 指定的組件的版本號碼，格式如下： `major.minor.build.revision`。<br /><br /> 此值必須遞增來觸發應用程式更新的更新資訊清單中。|  
|`publicKeyToken`|必要。 指定 16 個字元的十六進位字串，表示用以簽署部署資訊清單的公開金鑰的 sha-1 雜湊值的最後 8 個位元組。 公開金鑰用來登入必須是 2048 位元或更高。<br /><br /> 雖然是簽署組件的建議但非必要，這個屬性是必要的。 如果組件是不帶正負號，您應該從自我簽署的組件複製值，或使用 「 虛擬 」 全部為零的值。|  
|`processorArchitecture`|必要。 指定的處理器。 有效的值為`msil`對所有處理器來說`x86`的 32 位元 Windows`IA64`的 64 位元 Windows 和`Itanium`適用於 Intel 64 位元 Itanium 處理器。|  
|`type`|必要。 使用 Windows 來並行安裝技術的相容性。 唯一允許的值是`win32`。|  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列程式碼範例說明`assemblyIdentity`中的項目[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]部署資訊清單。 此程式碼範例是針對提供之較大範例的一部分[ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)主題。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)   
 [\<組件識別 > 項目](../deployment/assemblyidentity-element-clickonce-application.md)



