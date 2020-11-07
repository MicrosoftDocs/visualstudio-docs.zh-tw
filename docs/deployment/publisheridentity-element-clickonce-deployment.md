---
title: '&lt;publisherIdentity &gt; 元素 (ClickOnce 部署) |Microsoft Docs'
description: PublisherIdentity 元素包含簽署部署資訊清單之發行者的相關資訊。 簽署的資訊清單需要元素。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1eb4b67bfdca13c63480f3dde82004d87cd4a12a
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350682"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;&gt;ClickOnce 部署 (的 publisherIdentity 元素) 
包含簽署此部署資訊清單之發行者的資訊。

## <a name="syntax"></a>語法

```xml
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

## <a name="exceptions"></a>例外

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求

## <a name="subhead"></a>子標題