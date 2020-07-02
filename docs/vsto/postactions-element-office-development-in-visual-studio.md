---
title: '&lt;P s &gt; 元素（Visual Studio 中的 Office 開發）'
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bfe9ae171f0f6fac1c2b5add5340de1c11f3da0f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544413"
---
# <a name="ltpostactionsgt-element-office-development-in-visual-studio"></a>&lt;P s &gt; 元素（Visual Studio 中的 Office 開發）
  `postActions` 命名空間的 `vstav3` 項目包含描述安裝 Office 方案後所執行之部署後動作的所有 `postAction` 項目。

## <a name="syntax"></a>語法

```xml
<postActions>
  <postAction>
    <entryPoint>
    </entryPoint>
    <postActionData>
    </postActionData>
  </postAction>
</postActions>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `postActions` 項目是選擇項，且位於 `vstav3` 命名空間。 在應用程式資訊清單中，只會定義一個 `postActions` 項目。

 `postActions` 項目沒有任何屬性。

 `postActions` 具有下列項目。

### <a name="postaction"></a>postAction
 選擇性。 `postAction`命名空間中元素的角色 `vstav3` 是在[Visual Studio&#41;的&#60;p n&#62; 元素 &#40;Office 開發](../vsto/postaction-element-office-development-in-visual-studio.md)中定義。

## <a name="post-deployment-action-example"></a>部署後動作範例

### <a name="description"></a>描述
 下列程式碼範例說明使用 `postActions` 所部署之 Office 方案的應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是[Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中提供之較大範例的一部分。

### <a name="code"></a>程式碼

```xml
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

- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
