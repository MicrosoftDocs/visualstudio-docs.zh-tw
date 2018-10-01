---
title: '&lt;publisherIdentity&gt;項目 （ClickOnce 部署） |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 4c11e8ed9a3e0b4341708fc849462fbc476dc395
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491549"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt;項目 （ClickOnce 部署）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[ &lt;publisherIdentity&gt;項目 （ClickOnce 部署）](https://docs.microsoft.com/visualstudio/deployment/publisheridentity-element-clickonce-deployment)。  
  
包含簽署此部署資訊清單之發行者的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `publisherIdentity` ，則需要簽署資訊清單元素。 下表顯示的屬性，`publisherIdentity`項目支援。  
  
|屬性|描述|  
|---------------|-----------------|  
|`name`|必要。 描述發行此應用程式的合作對象的識別。|  
|`issuerKeyHash`|必要。 包含憑證簽發者的公開金鑰的 sha-1 雜湊。|  
  
#### <a name="parameters"></a>參數  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
  
## <a name="subhead"></a>子標題



