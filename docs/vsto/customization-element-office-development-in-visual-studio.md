---
title: '&lt;&gt;在 Visual Studio) 中 (Office 開發的自訂元素'
description: 瞭解 vstov4 命名空間的自訂元素如何描述特定的 Office 方案。
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0f50b441393e9d07dcd0b409248f199484022654
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844110"
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;&gt;在 Visual Studio) 中 (Office 開發的自訂元素
  `customization` 命名空間的 `vstov4` 項目描述特定的 Office 方案。 文件層級自訂與 VSTO 增益集的子項目不同。

## <a name="syntax-for-document-level-customizations"></a>檔層級自訂的語法

```xml
<customization
  id
  <document
    solutionId
  />
</customization>
```

## <a name="syntax-for-vsto-add-ins"></a>VSTO 增益集的語法

```xml
<customization
  id
  <appAddin
    application
    loadBehavior
    keyName>
  <friendlyName></friendlyName>
  <description></description>
  <formRegions></formRegions>
</customization>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `customization` 項目包含自訂的特定資訊。 此項目必須位於下列命名空間： `vstov4=urn:schemas-microsoft-com:vsto.v4`。 每個 Office 方案都有一個 `customization` 項目。 例如，如果您在多專案的部署中部署三個 Office 方案，則在應用程式資訊清單中會有三個 `customization` 項目。

 組件的子項目也必須在此命名空間中。

 `customization` 項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`id`|多專案部署所需。 `id` 項目能唯一地識別 Office 方案。|

### <a name="document-level-customizations"></a>Document-Level 自訂
 `customization` 項目具有下列子項目。

#### <a name="document"></a>文件
 `document`命名空間中的元素 `vstov4` 會在&#60;檔&#62; 專案中定義， [&#40;Visual Studio&#41;中的 Office 程式開發](../vsto/document-element-office-development-in-visual-studio.md)。

### <a name="vsto-add-ins"></a>VSTO 增益集
 `customization` 項目具有下列子項目。

#### <a name="appaddin"></a>appAddin
 `appAddin`命名空間中的元素 `vstov4` 會在&#60;appAddin&#62; 專案中定義， [&#40;Visual Studio&#41;中的 Office 程式開發](../vsto/appaddin-element-office-development-in-visual-studio.md)。

## <a name="example-of-a-document-level-customization"></a>檔層級自訂的範例

### <a name="description"></a>描述
 下列程式碼範例可說明文件層級自訂的 `customization` 項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。

### <a name="code"></a>程式碼

```xml
<vstov4:customization>
  <vstov4:document
    solutionId="73e" />
</vstov4:customization>
```

## <a name="example-of-a-vsto-add-in"></a>VSTO 增益集範例

### <a name="description"></a>描述
 下列程式碼範例說明 `customization` VSTO 增益集的元素。 這是包含表單區域的 Outlook VSTO 增益集。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。

### <a name="code"></a>程式碼

```xml
<vstov4:customization>
  <vstov4:appAddIn
    application="Outlook"
    loadBehavior="3"
    keyName="ContosoOutlookAddIn">
    <vstov4:friendlyName>
      ContosoOutlookAddIn
    </vstov4:friendlyName>
    <vstov4:description>
      ContosoOutlookAddIn - Outlook VSTO Add-in
      created with Visual Studio Tools for Office
    </vstov4:description>
    <vstov4:formRegions>
      <vstov4:formRegion
          name="OutlookAddIn1.FormRegion1">
        <vstov4:messageClass name="IPM.Note" />
        <vstov4:messageClass name="IPM.Contact" />
        <vstov4:messageClass name="IPM.Appointment" />
      </vstov4:formRegion>
    </vstov4:formRegions>
  </vstov4:appAddIn>
</vstov4:customization>
```

## <a name="see-also"></a>另請參閱

- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)