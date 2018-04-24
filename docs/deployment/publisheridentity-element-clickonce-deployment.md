---
title: '&lt;publisherIdentity&gt;元素 （ClickOnce 部署） |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ad10cae4ebd3aee6b65ad408ea3a3df3f82fd02
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt;元素 （ClickOnce 部署）
包含簽署此部署資訊清單之發行者的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `publisherIdentity` ，則需要已簽署的元素。 下表顯示的屬性，`publisherIdentity`項目支援。  
  
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