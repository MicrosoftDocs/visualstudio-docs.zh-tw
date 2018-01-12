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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 048ad687b8754d09bd1e217e49bee2898d7791e3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
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
|`release`|必要。 Visual Studio Tools for Office Runtime 的發行版本。|  
|`version`|必要。 Visual Studio Tools for Office Runtime 的版本號碼。|  
|`supportUrl`|選擇性。 Visual Studio Tools for Office Runtime 的安裝位置連結。|  
  
 `vstoRuntime` 沒有任何項目。  
  
## <a name="example"></a>範例  
 下列程式碼範例說明使用 `vstoRuntime` 所部署之 Office 方案的應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。  
  
```  
<vstav3:vstoRuntime  
    release="VSTOR40Beta1"  
    version="10.0.20303"  
    supportUrl="http://www.microsoft.com" />  
```  
  
## <a name="see-also"></a>請參閱  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  