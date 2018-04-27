---
title: '&lt;appAddin&gt;元素 （在 Visual Studio 中的 Office 程式開發） |Microsoft 文件'
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 85fda0db34bf104032e82d5725ff4d3d7aa772cb
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `appAddin` 命名空間的 `vstov4` 項目會儲存自訂 VSTO 增益集特定的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
<appAddin  
  application  
  loadBehavior  
  keyName>  
  <friendlyName>  
  <description>  
  <formRegions></formRegions>  
</appAddin>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `appAddin` 項目是必要的，且位於 `vstov4` 命名空間。 在應用程式資訊清單中，只可以定義一個 `appAddin` 項目。  
  
 `appAddin` 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`application`|必要。 識別 Microsoft Office 應用程式。 該值可以為下列其中一種：Excel、InfoPath、Outlook、PowerPoint、Project、Visio 或 Word。|  
|`loadBehavior`|選擇性。 根據預設，將此值設定為下列值時，會啟用 `loadBehavior` 。 若要進行偵錯，可以將此值設定為 2 來停用 VSTO 增益集。 如需詳細資訊，請參閱 [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md)中標題為 LoadBehavior 值的表格。|  
|`keyName`|必要。 這個值是該應用程式載入 VSTO 增益集時將要使用的登錄機碼名稱。 如需詳細資訊，請參閱 [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md)。|  
  
 `appAddin` 項目具有下列子項目。  
  
### <a name="friendlyname"></a>friendlyName  
 選擇性。 `friendlyName`項目中會說明[ &#60;friendlyName&#62;元素&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)。  
  
### <a name="description"></a>描述  
 選擇性。 `description`項目中會說明[&#60;描述&#62;元素&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/description-element-office-development-in-visual-studio.md)。  
  
### <a name="formregions"></a>formRegions  
 只有包含表單區域的 Outlook VSTO 增益集才需要。 `formRegions`項目中會說明[ &#60;formRegions&#62;元素&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)。  
  
## <a name="vsto-add-in-example"></a>VSTO 增益集範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明使用 `appAddin` 部署之 Outlook 方案中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。  
  
### <a name="code"></a>程式碼  
  
```  
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
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  