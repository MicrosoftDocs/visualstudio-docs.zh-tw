---
title: '&lt;&gt;在 Visual Studio) 中 (Office 開發的 p n 元素'
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0490e9423cb747782029eb0fd7254407adb3a607
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955758"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;&gt;在 Visual Studio) 中 (Office 開發的 p n 元素
  `postAction` 命名空間的 `vstav3` 項目包含 `entrypoint` 項目和所有 `postActionData` 項目，這些項目與安裝 Office 方案後執行的部署後動作相關。

## <a name="syntax"></a>Syntax

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `postAction` 項目是選擇項，且位於 `vstav3` 命名空間。 在應用程式資訊清單中，會為每個部署後動作定義一個 `postAction` 項目。

 `postAction` 項目沒有任何屬性。

 `postAction` 具有下列項目。

### <a name="entrypoint"></a>entryPoint
 選擇性。 `entryPoint`命名空間中專案的角色 `vstav3` 定義于[&#60;e&#62; 專案中，&#40;Visual Studio&#41;中的 Office 程式開發](../vsto/entrypoints-element-office-development-in-visual-studio.md)。

### <a name="postactiondata"></a>postActionData
 選擇性。 `postActionData`命名空間中專案的角色 `vstav3` 定義于[&#60;postActionData&#62; 專案中，&#40;Visual Studio&#41;中的 Office 程式開發](../vsto/postactiondata-element-office-development-in-visual-studio.md)。

## <a name="post-deployment-action-example"></a>部署後動作範例

### <a name="description"></a>Description
 下列程式碼範例說明使用 `postAction` 所部署之 Office 解決方案的應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。

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

- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
