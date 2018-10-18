---
title: '&lt;描述&gt;項目 （ClickOnce 部署） |Microsoft Docs'
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
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 8ddba6356ab051dbad27e55eefd53a517b47a21a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224766"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;描述&gt;項目 （ClickOnce 部署）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

識別用來建立 shell 的存在的應用程式資訊和**新增或移除程式**控制台 中的項目。  
  
## <a name="syntax"></a>語法  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `description` 項目是必要的，且位於 `urn:schemas-microsoft-com:asm.v1` 命名空間。 它包含沒有子項目，並具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`publisher`|必要。 識別在 Windows 中的圖示位置所使用的公司名稱**開始** 功能表並**新增或移除程式**在控制台中，當部署已安裝的項目。|  
|`product`|必要。 識別完整的產品名稱。 用來做為安裝在 Windows 中的圖示的標題**啟動**功能表。|  
|`suiteName`|選擇性。 識別的子資料夾中`publisher`在 Windows 中的資料夾**啟動**功能表。|  
|`supportUrl`|選擇性。 指定支援 URL 所示**新增或移除程式**控制台 中的項目。 此 URL 的捷徑也會建立在 Windows 中的應用程式支援**啟動**功能表上，當將部署設定進行安裝。|  
  
## <a name="remarks"></a>備註  
 所有的部署設定中需要的 description 項目。  
  
## <a name="example"></a>範例  
 下列程式碼範例說明`description`中的項目[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]部署資訊清單。 此程式碼範例是針對提供之較大範例的一部分[ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)主題。  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)



