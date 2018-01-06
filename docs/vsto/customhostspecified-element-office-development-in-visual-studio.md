---
title: "&lt;customHostSpecified&gt;元素 （在 Visual Studio 中的 Office 程式開發） |Microsoft 文件"
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
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
ms.assetid: 2212b7eb-bf94-4398-b9ea-0ab00203203b
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7f3a90c9a53059a9b356fe44c6c66fabd5821416
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `customHostSpecified`項目會指出此方案不是獨立的應用程式。 Office 方案包含裝載在 Microsoft Office 應用程式的元件。  
  
## <a name="syntax"></a>語法  
  
```  
<customHostSpecified />  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `customHostSpecified` ，則需要 Office 方案的元素。 此元素為`co.v1`命名空間和指定此部署包含將自訂主機，內部部署的元件，並不是獨立的應用程式。  
  
 這個項目是第一個子系`<entrypoint>`應用程式資訊清單中的項目。 可以是中的任何其他子項目`<entrypoint>`項目或[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]將會在安裝期間引發驗證錯誤。  
  
 這個項目具有的屬性和任何子項目。  
  
## <a name="example"></a>範例  
 下列程式碼範例說明`customHostSpecified`Office 方案的應用程式資訊清單中的項目。 這個程式碼範例是 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## <a name="see-also"></a>請參閱  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  