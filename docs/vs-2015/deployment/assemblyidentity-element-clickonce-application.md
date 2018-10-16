---
title: '&lt;assemblyIdentity&gt;項目 （ClickOnce 應用程式） |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: d16fdf182845eb2ae916da95b7677112b968b60f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49249037"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity&gt;項目 （ClickOnce 應用程式）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

識別應用程式部署在[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]部署。  
  
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
 `assemblyIdentity`是必要元素。 它包含沒有子項目，並具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Name`|必要。 識別應用程式的名稱。<br /><br /> 如果`Name`包含特殊字元，例如單引號或雙引號括住，應用程式可能無法啟動。|  
|`Version`|必要。 指定應用程式的版本號碼，格式如下： `major.minor.build.revision`|  
|`publicKeyToken`|選擇性。 指定 16 個字元的十六進位字串，表示最後 8 個位元組`SHA-1`簽署的應用程式或組件之公開金鑰的雜湊值。 公開金鑰用來簽署類別目錄必須是 2048 位元或更高。<br /><br /> 雖然是簽署組件的建議但非必要，這個屬性是必要的。 如果組件是不帶正負號，您應該從自我簽署的組件複製值，或使用 「 虛擬 」 全部為零的值。|  
|`processorArchitecture`|必要。 指定的處理器。 有效的值為`msil`對所有處理器來說`x86`的 32 位元 Windows`IA64`的 64 位元 Windows 和`Itanium`適用於 Intel 64 位元 Itanium 處理器。|  
|`language`|必要。 識別兩個組件語言代碼 (例如`en-US`) 的組件。 此元素為`asmv2`命名空間。 如果未指定，預設值是`neutral`。|  
  
## <a name="examples"></a>範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明`assemblyIdentity`中的項目[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式資訊清單。 此程式碼範例是中提供之較大範例的一部分[Ndptecclick](../deployment/clickonce-application-manifest.md)。  
  
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
 [\<組件識別 > 項目](../deployment/assemblyidentity-element-clickonce-deployment.md)



