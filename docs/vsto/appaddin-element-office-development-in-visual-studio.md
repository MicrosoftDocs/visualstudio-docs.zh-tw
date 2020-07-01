---
title: '&lt;appAddin &gt; 元素（Visual Studio 中的 Office 開發）'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1bf9ea990d12bd24adee3f6a24a39fa43c74fb71
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531634"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin &gt; 元素（Visual Studio 中的 Office 開發）
  命名空間的**appAddin**元素會 `vstov4` 儲存 VSTO 增益集的自訂特定資訊。

## <a name="syntax"></a>語法

```xml
<appAddin
  application
  loadBehavior
  keyName>
  <friendlyName>
  <description>
  <formRegions></formRegions>
</appAddin>
```

## <a name="elements-and-attributes"></a>元素和屬性
 **AppAddin**元素是必要專案，且位於 `vstov4` 命名空間中。 應用程式資訊清單中只有一個定義的**appAddin**元素。

 **AppAddin**元素具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|**應用程式**|必要。 識別 Microsoft Office 應用程式。 該值可以為下列其中一種：Excel、InfoPath、Outlook、PowerPoint、Project、Visio 或 Word。|
|**loadBehavior**|選擇性。 根據預設， **loadBehavior**會藉由將此值設定為來啟用。 若要進行偵錯，可以將此值設定為 2 來停用 VSTO 增益集。 如需詳細資訊，請參閱在[VSTO 增益集的登錄專案](../vsto/registry-entries-for-vsto-add-ins.md)中標題為 LoadBehavior 值的表格。|
|**名**|必要。 這個值是該應用程式載入 VSTO 增益集時將要使用的登錄機碼名稱。 如需詳細資訊，請參閱[VSTO 增益集的登錄專案](../vsto/registry-entries-for-vsto-add-ins.md)。|

 **AppAddin**元素具有下列子項目。

### <a name="friendlyname"></a>friendlyName
 選擇性。 &#60;friendlyName&#62; 元素中說明的**friendlyname**元素[&#40;Visual Studio&#41;中的 Office 開發](../vsto/friendlyname-element-office-development-in-visual-studio.md)。

### <a name="description"></a>description
 選擇性。 **描述**元素會在[Visual Studio&#41;中 &#40;Office 開發&#60;描述&#62; 元素](../vsto/description-element-office-development-in-visual-studio.md)中說明。

### <a name="formregions"></a>formRegions
 只有包含表單區域的 Outlook VSTO 增益集需要。 &#60;F s&#62; 元素中會說明**f s**元素[&#40;Visual Studio&#41;中的 Office 開發](../vsto/formregions-element-office-development-in-visual-studio.md)。

## <a name="vsto-add-in-example"></a>VSTO 增益集範例

### <a name="description"></a>描述
 下列程式碼範例說明使用所部署之 Outlook 方案中的**appAddin**元素 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 。 這個程式碼範例是[Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中提供之較大範例的一部分。

### <a name="code"></a>程式碼

```xml
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
```

## <a name="see-also"></a>另請參閱

- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)