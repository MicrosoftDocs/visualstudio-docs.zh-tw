---
title: "&lt;entryPoint&gt;元素 （在 Visual Studio 中的 Office 程式開發） |Microsoft 文件"
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
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
ms.assetid: 0c9d22d0-0852-4260-89c6-b83f24e48793
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a5ef93ab759f4e64607685d3d44fddfbf6c2c2dc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;entryPoint&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  每個 `entryPoint` 命名空間的 `vstav3` 項目都會識別出安裝這個 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 應用程式時應該執行的自訂組件。  
  
## <a name="syntax"></a>語法  
  
```  
<entryPoint class>  
    <assemblyIdentity />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `entryPoint` 項目是必要的，且位於 `vstav3` 命名空間。  
  
 每個 `entryPoint` 項目只可以包含一個自訂組件。 在應用程式資訊清單中可以定義多個 `entryPoint` 項目。  
  
 `entryPoint` 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`class`|必要。 識別要執行的自訂組件。 這個屬性的語法是 *NamespaceName.ClassName*。|  
  
 `entryPoint` 具有下列項目。  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 必要。 `assemblyIdentity` 命名空間中的 `vstav3` 項目參考 `assemblyIdentity` 應用程式資訊清單中的現有 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 項目。  
  
 角色`assemblyIdentity`和其屬性定義於[&#60; assemblyIdentity &#62;元素 &#40;ClickOnce 應用程式 &#41;](/visualstudio/deployment/assemblyidentity-element-clickonce-application).  
  
## <a name="document-level-customization-example"></a>文件層級自訂範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明使用 `entryPoint` 所部署之文件層級 Office 解決方案應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。  
  
### <a name="code"></a>程式碼  
  
```  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.ThisWorkbook">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet1">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet2">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet3">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
```  
  
## <a name="vsto-add-in-example"></a>VSTO 增益集範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明使用 `entryPoint` 所部署之應用程式層級 Office 解決方案應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。  
  
### <a name="code"></a>程式碼  
  
```  
<vstav3:entryPoint   
  class="ContosoOutlookAddIn.ThisAddIn">  
  <assemblyIdentity   
    name="ContosoOutlookAddIn"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
```  
  
## <a name="see-also"></a>請參閱  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  