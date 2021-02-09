---
title: '&lt;&gt; (ClickOnce 部署) 的 description 元素 |Microsoft Docs'
description: Description 元素會識別用來建立 shell 存在性的應用程式資訊，以及主控台中的 [新增或移除程式] 專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8dee33fca027ce47ede8315f7956479ee2394382
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893083"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;&gt;ClickOnce 部署 (description 元素) 
識別用來建立 shell 存在性的應用程式資訊，以及主控台中的 [ **新增或移除程式** ] 專案。

## <a name="syntax"></a>Syntax

```xml

      <description 
   publisher 
   product
   suiteName
   supportUrl
/>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `description` 項目是必要的，且位於 `urn:schemas-microsoft-com:asm.v1` 命名空間。 它不包含任何子項目，而且具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`publisher`|必要。 當部署已設定為安裝時，識別用於 Windows [ **開始** ] 功能表中的圖示位置，以及主控台中的 [ **新增或移除程式** ] 專案的公司名稱。|
|`product`|必要。 識別完整的產品名稱。 用來當做 Windows [ **開始** ] 功能表中所安裝圖示的標題。|
|`suiteName`|選擇性。 `publisher`在 Windows [**開始**] 功能表中，識別資料夾內的子資料夾。|
|`supportUrl`|選擇性。 指定主控台中的 [ **新增或移除程式** ] 專案所顯示的支援 URL。 當部署設定為安裝時，也會針對 Windows [ **開始** ] 功能表中的應用程式支援，建立此 URL 的快捷方式。|

## <a name="remarks"></a>備註
 所有部署設定中都需要 description 元素。

## <a name="example"></a>範例
 下列程式碼範例說明 `description` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署資訊清單中的元素。 這個程式碼範例是針對 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md) 主題提供之較大範例的一部分。

```xml
<description
  asmv2:publisher="My Company Name"
  asmv2:product="My Application"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>另請參閱
- [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)