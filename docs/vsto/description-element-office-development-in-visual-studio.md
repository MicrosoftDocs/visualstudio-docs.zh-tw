---
title: "&lt;描述&gt;元素 （在 Visual Studio 中的 Office 程式開發） |Microsoft 文件"
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
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
ms.assetid: 27c90f8c-393d-4557-9371-2e4e3c4a2d95
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a4978233c9172dd07cc034cba7f0d0f76374f231
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;描述&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `description` 命名空間的 `vstov4` 元素會儲存 Microsoft Office 應用程式之 [COM 增益集] 對話方塊中所顯示的 Office 解決方案描述。  
  
## <a name="syntax"></a>語法  
  
```  
<description>  
</description>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 選擇項。 `description` 元素位於 `vstov4` 命名空間。 它包含 Microsoft Office 應用程式之 [COM 增益集] 對話方塊中所顯示的增益集描述。  
  
 `description` 元素沒有屬性或元素。  
  
## <a name="vsto-add-in-example"></a>VSTO 增益集範例  
  
### <a name="description"></a>vstov4  
 下列程式碼範例說明使用 `description` 部署之應用程式層級解決方案的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]元素。 這個程式碼範例是 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。  
  
### <a name="code"></a>程式碼  
  
```  
<vstov4:description>  
  ContosoOutlookAddIn - Outlook add-in   
  created with Visual Studio Tools for Office  
</vstov4:description>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  