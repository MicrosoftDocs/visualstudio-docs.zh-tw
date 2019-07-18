---
title: '&lt;publisherIdentity&gt;項目 （ClickOnce 部署） |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 486e0bc5059e041f02e8dac4836c5ff59b27f63e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157638"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt;項目 （ClickOnce 部署）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
|屬性|說明|  
|---------------|-----------------|  
|`name`|必要項。 描述發行此應用程式的合作對象的識別。|  
|`issuerKeyHash`|必要項。 包含憑證簽發者的公開金鑰的 sha-1 雜湊。|  
  
#### <a name="parameters"></a>參數  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
  
## <a name="subhead"></a>子標題
