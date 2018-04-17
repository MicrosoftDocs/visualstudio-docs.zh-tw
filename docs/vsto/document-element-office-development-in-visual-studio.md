---
title: '&lt;文件&gt;元素 （在 Visual Studio 中的 Office 程式開發） |Microsoft 文件'
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
ms.openlocfilehash: 0e33e638937a02589a08e3ba2bebf9d3e9aeb1a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;文件&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `document`元素`vstov4`命名空間儲存文件層級自訂的自訂特定資訊。  
  
## <a name="syntax"></a>語法  
  
```  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 只有需要文件層級自訂。 `document`元素為`vstov4`命名空間。 `document`元素都具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`solutionId`|必要。 由 Visual Studio Tools for Office runtime 用來唯一識別文件層級方案的 GUID。 這個值會儲存為 _AssemblyLocation 自訂文件屬性。 如需詳細資訊，請參閱 [Custom Document Properties Overview](../vsto/custom-document-properties-overview.md)。|  
  
 `document` 沒有任何子項目。  
  
## <a name="document-level-customization-example"></a>文件層級自訂範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明`document`所部署之文件層級 Office 方案中的項目[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]。 這個程式碼範例是 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。  
  
### <a name="code"></a>程式碼  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>另請參閱  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  