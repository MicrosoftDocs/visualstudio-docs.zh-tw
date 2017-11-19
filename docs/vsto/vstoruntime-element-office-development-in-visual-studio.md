---
title: "&lt;vstoRuntime&gt;元素 （在 Visual Studio 中的 Office 程式開發） |Microsoft 文件"
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
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
ms.assetid: e59a8a61-9ff2-4032-9983-4a1e289e70a7
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d6ac2393a5cfd27b2909fb5a5d63ff0260941e4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoRuntime&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `vstoRuntime` 命名空間的 `vstav3` 項目包含特定 Office 方案支援的 Visual Studio Tools for Office Runtime 版本。  
  
## <a name="syntax"></a>語法  
  
```  
<vstoRuntime  
    release  
    version  
    supportUrl />  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `vstoRuntime` 項目是必要項，且位於 `vstav3` 命名空間。 如果 Office 方案支援兩種 Visual Studio Tools for Office Runtime 版本，應用程式資訊清單中會有兩個 `vstoRuntime` 項目。  
  
 `vstoRuntime` 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`release`|必要項。 Visual Studio Tools for Office Runtime 的發行版本。|  
|`version`|必要項。 Visual Studio Tools for Office Runtime 的版本號碼。|  
|`supportUrl`|選擇項。 Visual Studio Tools for Office Runtime 的安裝位置連結。|  
  
 `vstoRuntime` 沒有任何項目。  
  
## <a name="example"></a>範例  
 下列程式碼範例說明使用 `vstoRuntime` 所部署之 Office 方案的應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。  
  
```  
<vstav3:vstoRuntime  
    release="VSTOR40Beta1"  
    version="10.0.20303"  
    supportUrl="http://www.microsoft.com" />  
```  
  
## <a name="see-also"></a>另請參閱  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  