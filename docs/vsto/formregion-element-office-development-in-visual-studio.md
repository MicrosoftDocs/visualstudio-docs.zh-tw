---
description: Vstov4 命名空間的 formRegion 元素會識別與 VSTO 增益集相關聯的 Microsoft Office Outlook 表單區域。
title: '&lt;&gt;Visual Studio) 中 (Office 開發的 formRegion 元素'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0851ba9e117b464d3a2fbb9ad9903af17ceda0c4
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221076"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;&gt;Visual Studio) 中 (Office 開發的 formRegion 元素
  `formRegion`命名空間的元素 `vstov4` 會識別與 VSTO 增益集相關聯的 Microsoft Office Outlook 表單區域。

## <a name="syntax"></a>Syntax

```xml
<formRegion
  name>
  <messageClass
    name/>
</formRegion>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `formRegion` 命名空間的 `vstov4` 項目會識別與 Outlook VSTO 增益集相關聯的表單區域。 此項目只有包含表單區域的 Outlook VSTO 增益集需要。

 單一 VSTO 增益集的 `formRegion` 項目中可以定義多個 `formRegions` 項目。

 `formRegion` 項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`name`|必要。 識別表單區域名稱。|

 `formRegion` 項目具有下列子項目。

### <a name="messageclass"></a>messageClass
 `messageClass` 項目會識別與表單區域相關聯的 Outlook 表單。

 `messageClass` 項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`name`|必要。 識別與表單區域相關聯的表單。|

## <a name="example"></a>範例
 下列程式碼範例說明使用 `formRegion` 所部署之 Outlook VSTO 增益集的應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 有三個訊息類別與這個表單區域相關聯。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>另請參閱

- [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)
- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
