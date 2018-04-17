---
title: '&lt;formRegion&gt;元素 （在 Visual Studio 中的 Office 程式開發） |Microsoft 文件'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: af7dd4f3472692def9f05a937297d54d13c6f0d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `formRegion` 命名空間的 `vstov4` 項目會識別與 VSTO 增益集相關聯的 Microsoft Office Outlook 表單區域。  
  
## <a name="syntax"></a>語法  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `formRegion` 命名空間的 `vstov4` 項目會識別與 Outlook VSTO 增益集相關聯的表單區域。 只有包含表單區域的 Outlook VSTO 增益集才需要這個項目。  
  
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
 下列程式碼範例說明使用 `formRegion` 所部署之 Outlook VSTO 增益集的應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 有三個訊息類別與這個表單區域相關聯。 這個程式碼範例是 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。  
  
```  
<vstov4:formRegion  
    name="OutlookAddIn1.FormRegion1">  
  <vstov4:messageClass name="IPM.Note" />  
  <vstov4:messageClass name="IPM.Contact" />  
  <vstov4:messageClass name="IPM.Appointment" />  
</vstov4:formRegion>  
```  
  
## <a name="see-also"></a>另請參閱  
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  