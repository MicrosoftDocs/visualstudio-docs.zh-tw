---
title: '&lt;描述&gt;元素 （ClickOnce 部署） |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06a8f1a1e5ec5f4663ed999566158d104c6a7364
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31564242"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;描述&gt;元素 （ClickOnce 部署）
識別應用程式資訊用於建立 shell 的存在和**新增或移除程式**控制台 中的項目。  
  
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
 `description` 為必要元素，位於 `urn:schemas-microsoft-com:asm.v1` 命名空間。 它包含沒有子項目，並具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`publisher`|必要。 識別用於在 Windows 中的圖示位置的公司名稱**啟動**功能表和**新增或移除程式**項目在控制台中，當將部署設定安裝。|  
|`product`|必要。 識別完整的產品名稱。 做為安裝在 Windows 中的圖示標題**啟動**功能表。|  
|`suiteName`|選擇性。 識別的子資料夾中`publisher`中 Windows 資料夾**啟動**功能表。|  
|`supportUrl`|選擇性。 指定如下所示的支援 URL**新增或移除程式**控制台 中的項目。 此 URL 的捷徑也會建立應用程式中的支援 Windows**啟動**功能表上，將部署設定安裝。|  
  
## <a name="remarks"></a>備註  
 所有的部署設定中需要的描述項目。  
  
## <a name="example"></a>範例  
 下列程式碼範例說明`description`中的項目[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署資訊清單。 這個程式碼範例是針對所提供之較大範例的一部分[ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)主題。  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)