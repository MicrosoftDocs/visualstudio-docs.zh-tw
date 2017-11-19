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
ms.openlocfilehash: c7ad3bb1e62e2ea98f5afe1de5cc9eb49f711234
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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
  
## <a name="see-also"></a>另請參閱  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  