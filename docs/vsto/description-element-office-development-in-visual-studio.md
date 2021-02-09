---
title: '&lt;&gt;在 Visual Studio) 中 (Office 開發的 description 元素'
description: 瞭解 vstov4 命名空間的 description 元素，會儲存出現在 [COM 增益集] 對話方塊中的 Office 方案的描述。
titleSuffix: ''
ms.custom: secdec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9f065dd07e901ee0d59b39f1096cc351cd70bc02
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897593"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;&gt;在 Visual Studio) 中 (Office 開發的 description 元素
  `description` 命名空間的 `vstov4` 元素會儲存 Microsoft Office 應用程式之 [COM 增益集] 對話方塊中所顯示的 Office 解決方案描述。

## <a name="syntax"></a>Syntax

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>元素和屬性
 選擇性。 `description` 元素位於 `vstov4` 命名空間。 它包含 Microsoft Office 應用程式之 [COM 增益集] 對話方塊中所顯示的增益集描述。

 `description` 元素沒有屬性或元素。

## <a name="vsto-add-in-example"></a>VSTO 增益集範例

### <a name="description"></a>Description
 下列程式碼範例說明使用 `description` 部署之應用程式層級解決方案的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]元素。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。

### <a name="code"></a>程式碼

```xml
<vstov4:description>
  ContosoOutlookAddIn - Outlook add-in
  created with Visual Studio Tools for Office
</vstov4:description>
```

## <a name="see-also"></a>另請參閱

- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)