---
title: '&lt;publisherIdentity &gt; 元素 (ClickOnce 部署) |Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157638"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;&gt;ClickOnce 部署 (的 publisherIdentity 元素) 
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

包含簽署此部署資訊清單之發行者的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>元素和屬性  
 `publisherIdentity`簽署的資訊清單需要元素。 下表顯示 `publisherIdentity` 元素支援的屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`name`|必要。 描述發行此應用程式之合作物件的身分識別。|  
|`issuerKeyHash`|必要。 包含憑證簽發者之公開金鑰的 SHA-1 雜湊。|  
  
#### <a name="parameters"></a>參數  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
  
## <a name="subhead"></a>子標題
