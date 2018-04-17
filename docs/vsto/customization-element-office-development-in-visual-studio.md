---
title: '&lt;自訂&gt;元素 （在 Visual Studio 中的 Office 程式開發） |Microsoft 文件'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4384dd8bea4fc5829362ccdb06ea3912607cd263
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;自訂&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `customization` 命名空間的 `vstov4` 項目描述特定的 Office 方案。 文件層級自訂與 VSTO 增益集的子項目不同。  
  
## <a name="syntax-for-document-level-customizations"></a>文件層級自訂的語法  
  
```  
<customization  
  id  
  <document  
    solutionId  
  />  
</customization>  
```  
  
## <a name="syntax-for-vsto-add-ins"></a>VSTO 增益集的語法  
  
```  
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
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `customization` 項目包含自訂的特定資訊。 此項目必須位於下列命名空間中： `vstov4=urn:schemas-microsoft-com:vsto.v4`。 每個 Office 方案都有一個 `customization` 項目。 例如，如果您在多專案的部署中部署三個 Office 方案，則在應用程式資訊清單中會有三個 `customization` 項目。  
  
 組件的子項目也必須在此命名空間中。  
  
 `customization` 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`id`|多專案部署所需。 `id` 項目能唯一地識別 Office 方案。|  
  
### <a name="document-level-customizations"></a>文件層級自訂  
 `customization` 項目具有下列子項目。  
  
#### <a name="document"></a>文件  
 `document`中的項目`vstov4`命名空間中定義[&#60;文件&#62;元素&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/document-element-office-development-in-visual-studio.md)。  
  
### <a name="vsto-add-ins"></a>VSTO 增益集  
 `customization` 項目具有下列子項目。  
  
#### <a name="appaddin"></a>appAddin  
 `appAddin`中的項目`vstov4`命名空間中定義[ &#60;appAddin&#62;元素&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)。  
  
## <a name="example-of-a-document-level-customization"></a>文件層級自訂的範例  
  
### <a name="description"></a>描述  
 下列程式碼範例可說明文件層級自訂的 `customization` 項目。 這個程式碼範例是 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。  
  
### <a name="code"></a>程式碼  
  
```  
<vstov4:customization>  
  <vstov4:document   
    solutionId="73e" />  
</vstov4:customization>  
```  
  
## <a name="example-of-an-vsto-add-in"></a>VSTO 增益集的範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明 VSTO 增益集的 `customization` 項目。 這是包含表單區域的 Outlook VSTO 增益集。 這個程式碼範例是 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。  
  
### <a name="code"></a>程式碼  
  
```  
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
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  