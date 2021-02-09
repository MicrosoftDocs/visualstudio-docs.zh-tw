---
title: '&lt;Customerrorreporting> &gt; 元素 (ClickOnce 部署) |Microsoft Docs'
description: Customerrorreporting> 元素會指定發生錯誤時要顯示的 URI，而不是顯示例外狀況堆疊的錯誤對話方塊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b168b3bcb90ae758609698de306928eb7e13d909
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888481"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;&gt;ClickOnce 部署 (的 customerrorreporting> 元素) 
指定要在錯誤發生時顯示的 URI。

## <a name="syntax"></a>語法

```xml
<customErrorReporting
   uri
/>
```

## <a name="remarks"></a>備註
 這是選擇性的項目。 如果沒有，則會 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 顯示 [錯誤] 對話方塊，顯示例外狀況堆疊。 如果專案 `customErrorReporting` 存在，則 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 會改為顯示參數所指示的 URI `uri` 。 目標 URI 將包含外部例外狀況類別、內部例外狀況類別，以及內部例外狀況訊息作為參數。

 使用這個元素可將錯誤報表功能新增至您的應用程式。 由於產生的 URI 包含錯誤類型的相關資訊，您的網站可以剖析該資訊並顯示，例如適當的疑難排解畫面。

## <a name="example"></a>範例
 下列程式碼片段會顯示 `customErrorReporting` 元素，以及產生的 URI。

```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />

Example Generated Error:
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.
```

## <a name="see-also"></a>另請參閱
- [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)