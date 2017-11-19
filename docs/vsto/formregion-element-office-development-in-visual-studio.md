---
title: "&lt;formRegion&gt;元素 （在 Visual Studio 中的 Office 程式開發） |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: application manifests [Office development in Visual Studio], <formRegion> element
ms.assetid: d397cf31-c0ef-47f0-860a-cd816e4bf6eb
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f0c34dc6e3cc7fd9339e9f2a183bcc11d54008e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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
|`name`|必要項。 識別表單區域名稱。|  
  
 `formRegion` 項目具有下列子項目。  
  
### <a name="messageclass"></a>messageClass  
 `messageClass` 項目會識別與表單區域相關聯的 Outlook 表單。  
  
 `messageClass` 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`name`|必要項。 識別與表單區域相關聯的表單。|  
  
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
  
  