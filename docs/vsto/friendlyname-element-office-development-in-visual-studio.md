---
title: '&lt;friendlyName&gt;元素 （在 Visual Studio 中的 Office 程式開發）'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 26842ab926ed7ef0ea2cfd62bf032c25b2c69d02
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548472"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;friendlyName&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `friendlyName` 命名空間的 `vstov4` 項目會儲存已安裝的程式清單中顯示的名稱。  
  
## <a name="syntax"></a>語法  
  
```xml
<friendlyName>  
</friendlyName>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `friendlyName` 項目位於 `vstov4` 命名空間。 電腦上的已安裝程式清單和 Microsoft Office 應用程式的 [COM VSTO 增益集] 對話方塊中會顯示值。  
  
 `friendlyName` 項目沒有屬性或子項目。  
  
## <a name="vsto-add-in-example"></a>VSTO 增益集範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明使用 `friendlyName` 部署之應用程式層級方案中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是中提供之較大範例的一部分[Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)。  
  
### <a name="code"></a>程式碼  
  
```xml  
<vstov4:friendlyName>  
  ContosoOutlookAddIn  
</vstov4:friendlyName>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  