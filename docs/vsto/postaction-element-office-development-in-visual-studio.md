---
title: '&lt;postAction&gt;元素 （在 Visual Studio 中的 Office 程式開發）'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dcab31eea406da695bdedd21b21c0d86cacea220
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693113"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `postAction` 命名空間的 `vstav3` 項目包含 `entrypoint` 項目和所有 `postActionData` 項目，這些項目與安裝 Office 方案後執行的部署後動作相關。  
  
## <a name="syntax"></a>語法  
  
```xml  
<postAction>  
  <entryPoint>  
  </entryPoint>  
  <postActionData>  
  </postActionData>  
</postAction>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `postAction` 項目是選擇項，且位於 `vstav3` 命名空間。 在應用程式資訊清單中，會為每個部署後動作定義一個 `postAction` 項目。  
  
 `postAction`項目沒有任何屬性。  
  
 `postAction` 具有下列項目。  
  
### <a name="entrypoint"></a>entrypoint  
 選擇性。 角色`entryPoint`中的項目`vstav3`命名空間中定義[&#60;進入點&#62;元素&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)。  
  
### <a name="postactiondata"></a>postActionData  
 選擇性。 角色`postActionData`中的項目`vstav3`命名空間中定義[ &#60;postActionData&#62;元素&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)。  
  
## <a name="post-deployment-action-example"></a>部署後動作範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明使用 `postAction` 所部署之 Office 解決方案的應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是中提供之較大範例的一部分[Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)。  
  
### <a name="code"></a>程式碼  
  
```xml
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
```  
  
## <a name="see-also"></a>另請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  