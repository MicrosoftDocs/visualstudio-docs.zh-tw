---
title: '&lt;formRegions&gt;元素 （在 Visual Studio 中的 Office 程式開發） |Microsoft 文件'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c51b626c104d5342c00dbd45a2c565315c9c2225
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formRegions&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `formRegions` 命名空間的 `vstov4` 項目包含與 VSTO 增益集相關聯的 Microsoft Office Outlook 表單區域。  
  
## <a name="syntax"></a>語法  
  
```  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `formRegions` 命名空間的 `vstov4` 項目包含 Outlook VSTO 增益集的所有 `formRegion` 項目。 此項目只有包含表單區域的 Outlook VSTO 增益集需要。  
  
 在應用程式資訊清單中，只可以定義一個 `formRegions` 項目。  
  
 `formRegions` 項目沒有任何屬性。  
  
 `formRegions` 項目具有下列項目。  
  
### <a name="formregion"></a>formRegion  
 包含表單區域的 Outlook VSTO 增益集需要。 `formRegion`定義元素[ &#60;formRegion&#62;元素&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)。  
  
## <a name="vsto-add-in-example"></a>VSTO 增益集範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明使用 `formRegions` 所部署之應用程式層級 Office 方案的應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。  
  
### <a name="code"></a>程式碼  
  
```  
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
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  