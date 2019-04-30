---
title: '&lt;描述&gt;項目 （ClickOnce 部署） |Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c359b188894c40f017e3d2a0e06d52de87e9c5f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928804"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;描述&gt;項目 （ClickOnce 部署）
識別用來建立 shell 的存在的應用程式資訊和**新增或移除程式**控制台 中的項目。

## <a name="syntax"></a>語法

```xml

      <description 
   publisher 
   product
   suiteName
   supportUrl
/>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `description` 項目是必要的，且位於 `urn:schemas-microsoft-com:asm.v1` 命名空間。 它包含沒有子項目，並具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`publisher`|必要項。 識別在 Windows 中的圖示位置所使用的公司名稱**開始** 功能表並**新增或移除程式**在控制台中，當部署已安裝的項目。|
|`product`|必要項。 識別完整的產品名稱。 用來做為安裝在 Windows 中的圖示的標題**啟動**功能表。|
|`suiteName`|選擇性。 識別的子資料夾中`publisher`在 Windows 中的資料夾**啟動**功能表。|
|`supportUrl`|選擇性。 指定支援 URL 所示**新增或移除程式**控制台 中的項目。 此 URL 的捷徑也會建立在 Windows 中的應用程式支援**啟動**功能表上，當將部署設定進行安裝。|

## <a name="remarks"></a>備註
 所有的部署設定中需要的 description 項目。

## <a name="example"></a>範例
 下列程式碼範例說明`description`中的項目[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署資訊清單。 此程式碼範例是針對提供之較大範例的一部分[ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)主題。

```xml
<description
  asmv2:publisher="My Company Name"
  asmv2:product="My Application"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>另請參閱
- [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)