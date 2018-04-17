---
title: '&lt;postActions&gt;元素 （在 Visual Studio 中的 Office 程式開發） |Microsoft 文件'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2c4dafa1c5ac7ef296ba388ecdfd93d00afef708
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ltpostactionsgt-element-office-development-in-visual-studio"></a>&lt;postActions&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `postActions` 命名空間的 `vstav3` 項目包含描述安裝 Office 方案後所執行之部署後動作的所有 `postAction` 項目。  
  
## <a name="syntax"></a>語法  
  
```  
<postActions>  
  <postAction>  
    <entryPoint>  
    </entryPoint>  
    <postActionData>  
    </postActionData>  
  </postAction>  
</postActions>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `postActions` 項目是選擇項，且位於 `vstav3` 命名空間。 在應用程式資訊清單中，只會定義一個 `postActions` 項目。  
  
 `postActions` 項目沒有任何屬性。  
  
 `postActions` 具有下列項目：  
  
### <a name="postaction"></a>postAction  
 選擇性。 角色`postAction`中的項目`vstav3`命名空間中定義[ &#60;postAction&#62;元素&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)。  
  
## <a name="post-deployment-action-example"></a>部署後動作範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明使用 `postActions` 所部署之 Office 方案的應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。  
  
### <a name="code"></a>程式碼  
  
```  
<vstav3:postActions>  
  <vstav3:postAction>  
    <vstav3:entryPoint   
      class="PostDeploymentAction.PostDeploymentActionSample">  
      <assemblyIdentity   
        name="PostDeploymentAction"   
        version="1.0.0.0"   
        language="neutral"   
        processorArchitecture="msil" />  
    </vstav3:entryPoint>  
    <vstav3:postActionData>  
    </vstav3:postActionData>  
  </vstav3:postAction>  
</vstav3:postActions>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  