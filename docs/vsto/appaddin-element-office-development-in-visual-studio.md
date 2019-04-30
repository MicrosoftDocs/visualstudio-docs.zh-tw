---
title: '&lt;appAddin&gt;元素 （在 Visual Studio 中的 Office 程式開發）'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 2116576acb06e6291749d9c0176fcf4ebb426739
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953240"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  **AppAddin**項目`vstov4`命名空間會儲存為 VSTO 增益集的自訂特定資訊。

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
 **AppAddin**是必要項目，且位於`vstov4`命名空間。 只有一個**appAddin**應用程式資訊清單中所定義的項目。

 **AppAddin**項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|**application**|必要項。 識別 Microsoft Office 應用程式。 值可以是下列其中一項：Excel、 InfoPath、 Outlook、 PowerPoint、 Project、 Visio 或 Word。|
|**loadBehavior**|選擇性。 根據預設， **loadBehavior**將此值設為啟用。 若要進行偵錯，可以將此值設定為 2 來停用 VSTO 增益集。 如需詳細資訊，請參閱標題為 LoadBehavior 值的表格[VSTO 增益集的登錄項目](../vsto/registry-entries-for-vsto-add-ins.md)。|
|**keyName**|必要項。 這個值是該應用程式載入 VSTO 增益集時將要使用的登錄機碼名稱。 如需詳細資訊，請參閱 < [VSTO 增益集的登錄項目](../vsto/registry-entries-for-vsto-add-ins.md)。|

 **AppAddin**項目具有下列子項目。

### <a name="friendlyname"></a>friendlyName
 選擇性。 **FriendlyName**項目述[ &#60;friendlyName&#62;項目的&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)。

### <a name="description"></a>描述
 選擇性。 **描述**項目述[&#60;描述&#62;項目的&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/description-element-office-development-in-visual-studio.md)。

### <a name="formregions"></a>formRegions
 只有包含表單區域的 Outlook VSTO 增益集才需要。 **FormRegions**項目述[ &#60;formRegions&#62;項目的&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)。

## <a name="vsto-add-in-example"></a>VSTO 增益集範例

### <a name="description"></a>描述
 下列程式碼範例說明**appAddin**部署之 Outlook 方案中的項目[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]。 此程式碼範例是中提供之較大範例的一部分[Application manifests for Office 方案](../vsto/application-manifests-for-office-solutions.md)。

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