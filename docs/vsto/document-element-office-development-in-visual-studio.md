---
title: '&lt;文件&gt;元素 （在 Visual Studio 中的 Office 程式開發）'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 07d8172ec4e56352c2244aef02d947ac48833ab7
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447331"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;文件&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `document`元素`vstov4`命名空間儲存文件層級自訂的自訂特定資訊。  
  
## <a name="syntax"></a>語法  
  
```xml  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 只有需要文件層級自訂。 `document`元素為`vstov4`命名空間。 `document`元素都具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`solutionId`|必要。 由 Visual Studio Tools for Office runtime 用來唯一識別文件層級方案的 GUID。 這個值會儲存為 _AssemblyLocation 自訂文件屬性。 如需詳細資訊，請參閱[自訂文件屬性概觀](../vsto/custom-document-properties-overview.md)。|  
  
 `document` 沒有任何子項目。  
  
## <a name="document-level-customization-example"></a>文件層級自訂範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明`document`所部署之文件層級 Office 方案中的項目[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]。 這個程式碼範例是中提供之較大範例的一部分[Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)。  
  
### <a name="code"></a>程式碼  
  
```xml
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>另請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  