---
description: Vstov4 命名空間的 friendlyName 元素會儲存已安裝的程式清單中顯示的名稱。
title: '&lt;&gt;Visual Studio) 中 (Office 開發的 friendlyName 元素'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: adcf46a2c232176026181283549c0c59fc713603
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223442"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;&gt;Visual Studio) 中 (Office 開發的 friendlyName 元素
  `friendlyName` 命名空間的 `vstov4` 項目會儲存已安裝的程式清單中顯示的名稱。

## <a name="syntax"></a>Syntax

```xml
<friendlyName>
</friendlyName>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `friendlyName` 元素位於 `vstov4` 命名空間。 電腦上的已安裝程式清單和 Microsoft Office 應用程式的 [COM VSTO 增益集] 對話方塊中會顯示值。

 `friendlyName` 項目沒有屬性或子項目。

## <a name="vsto-add-in-example"></a>VSTO 增益集範例

### <a name="description"></a>描述
 下列程式碼範例說明使用 `friendlyName` 部署之應用程式層級方案中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。

### <a name="code"></a>程式碼

```xml
<vstov4:friendlyName>
  ContosoOutlookAddIn
</vstov4:friendlyName>
```

## <a name="see-also"></a>另請參閱

- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
