---
title: "&lt;postActionData&gt;元素 （在 Visual Studio 中的 Office 程式開發） |Microsoft 文件"
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
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
ms.assetid: e36cbd64-fd27-4413-b293-cf5546fbdfaf
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4a8ccea7fd468f590b927234c9114ae82ee1479f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ltpostactiondatagt-element-office-development-in-visual-studio"></a>&lt;postActionData&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `postActionData` 命名空間的 `vstav3` 項目指定與安裝 Office 方案後所執行之任何部署後動作相關聯的資料。  
  
## <a name="syntax"></a>語法  
  
```  
<postActionData>  
</postActionData>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `postActionData` 項目是選擇項，且位於 `vstav3` 命名空間。 在應用程式資訊清單中，會為每個部署後動作定義一個 `postActionData` 項目。  
  
 `postActions` 項目沒有任何屬性。  
  
 `postActions` 沒有任何子項目。  
  
## <a name="post-deployment-action-example"></a>部署後動作範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明使用 `postAction` 所部署之 Office 方案的應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。  
  
### <a name="code"></a>程式碼  
  
```  
<vstav3:postActionData>  
  data in any format  
</vstav3:postActionData>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  