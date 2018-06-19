---
title: '&lt;進入點&gt;元素 （在 Visual Studio 中的 Office 程式開發）'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoints> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bec51fd4d9e6a140d274f028a0e0286a161ac147
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448385"
---
# <a name="ltentrypointsgt-element-office-development-in-visual-studio"></a>&lt;進入點&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `entryPoints` 命名空間的 `vstav3` 項目包含與 Office 方案相關聯的所有 `entryPoint` 項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
<entryPoints>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
</entryPoints>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `entryPoints` 項目是必要的，且位於 `vstav3` 命名空間。 在應用程式資訊清單中，會為每個 Office 方案定義一個 `entryPoints` 項目。 例如，如果您在多專案的部署中部署三個 Office 方案，則在應用程式資訊清單中會有三個 `entryPoints` 項目。  
  
 `entryPoints` 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|id|多專案部署所需。 Office 方案的名稱。 id 不能包含等號 (=)。|  
  
 `entryPoints` 具有下列項目。  
  
### <a name="entrypoint"></a>entryPoint  
 必要。 角色`entryPoint`中的項目`vstav3`命名空間中定義[ &#60;entryPoint&#62;元素&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)。  
  
## <a name="document-level-customization-example"></a>文件層級自訂範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明使用 `entryPoints` 所部署之文件層級方案的應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是中提供之較大範例的一部分[Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)。  
  
### <a name="code"></a>程式碼  
  
```xml  
<vstav3:entryPoints>  
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
</vstav3:entryPoints>  
```  
  
## <a name="vsto-add-in-example"></a>VSTO 增益集範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明使用 `entryPoints` 所部署之應用程式層級方案的應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是中提供之較大範例的一部分[Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)。  
  
### <a name="code"></a>程式碼  
  
```xml  
<vstav3:entryPoints>  
  <vstav3:entryPoint   
    class="ContosoOutlookAddIn.ThisAddIn">  
    <assemblyIdentity   
      name="ContosoOutlookAddIn"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
</vstav3:entryPoints>  
```  
  
## <a name="multi-project-deployment-example"></a>多專案部署範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明多專案部署的應用程式資訊清單中的 `entryPoints` 項目。 這個程式碼範例是中提供之較大範例的一部分[Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)。  
  
### <a name="code"></a>程式碼  
  
```xml  
<vstav3:entryPoints   
  id="ContosoExcel">  
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
</vstav3:entryPoints>  
<vstav3:entryPoints   
  id="ContosoOutlook">  
  <vstav3:entryPoint   
    class="ContosoOutlookAddIn.ThisAddIn">  
    <assemblyIdentity   
      name="ContosoOutlookAddIn"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
</vstav3:entryPoints>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  