---
description: Vstov4 命名空間的 F s 元素包含與 VSTO 增益集相關聯的 Microsoft Office Outlook 表單區域。
title: '&lt;&gt;Visual Studio) 中 (Office 開發的 f s 元素'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7c8fd7e0ced0fadcd945388a9730513b2a591ed0
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223455"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;&gt;Visual Studio) 中 (Office 開發的 f s 元素
  `formRegions`命名空間的元素 `vstov4` 包含與 VSTO 增益集相關聯的 Microsoft Office Outlook 表單區域。

## <a name="syntax"></a>Syntax

```xml
<formRegions>
  <formRegion>
  </formRegion>
</formRegions>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `formRegions` 命名空間的 `vstov4` 項目包含 Outlook VSTO 增益集的所有 `formRegion` 項目。 此項目只有包含表單區域的 Outlook VSTO 增益集需要。

 在應用程式資訊清單中，只可以定義一個 `formRegions` 項目。

 `formRegions` 項目沒有任何屬性。

 `formRegions` 項目具有下列項目。

### <a name="formregion"></a>formRegion
 包含表單區域的 Outlook VSTO 增益集需要。 專案 `formRegion` 定義于 [&#60;formRegion&#62; 專案中，&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)。

## <a name="vsto-add-in-example"></a>VSTO 增益集範例

### <a name="description"></a>描述
 下列程式碼範例說明使用 `formRegions` 所部署之應用程式層級 Office 方案的應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。

### <a name="code"></a>程式碼

```xml
<vstov4:formRegions>
  <vstov4:formRegion
      name="OutlookAddIn1.FormRegion1">
    <vstov4:messageClass name="IPM.Note" />
    <vstov4:messageClass name="IPM.Contact" />
    <vstov4:messageClass name="IPM.Appointment" />
  </vstov4:formRegion>
</vstov4:formRegions>
```

## <a name="see-also"></a>另請參閱

- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
