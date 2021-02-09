---
title: '&lt;&gt;在 Visual Studio) 中 (Office 開發的 d 元素'
description: 瞭解 d 元素如何表示此解決方案不是獨立的應用程式。
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ba5ce54e862862c1e6750c78416fec4d5cf51cdd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99849979"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;&gt;在 Visual Studio) 中 (Office 開發的 d 元素
  `customHostSpecified`元素表示此方案不是獨立的應用程式。 Office 方案包含在 Microsoft Office 應用程式中裝載的元件。

## <a name="syntax"></a>Syntax

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>元素和屬性
 `customHostSpecified`Office 方案需要元素。 此元素位於 `co.v1` 命名空間中，並指定此部署包含將在自訂主機內部署的元件，而不是獨立的應用程式。

 此專案是 `<entrypoint>` 應用程式資訊清單中第一個元素的子系。 該元素中不能有其他子項目， `<entrypoint>` 或在 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 安裝期間會引發驗證錯誤。

 此元素沒有屬性和子項目。

## <a name="example"></a>範例
 下列程式碼範例說明 `customHostSpecified` Office 方案的應用程式資訊清單中的元素。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>另請參閱

- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)