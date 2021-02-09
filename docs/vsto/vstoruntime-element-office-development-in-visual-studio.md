---
title: '&lt;&gt;在 Visual Studio) 中 (Office 開發的 v m e 元素'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c866db5f691db56e68f6980c9c07d21ee15c0ae5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921754"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;&gt;在 Visual Studio) 中 (Office 開發的 v m e 元素
  `vstoRuntime` 命名空間的 `vstav3` 項目包含特定 Office 方案支援的 Visual Studio Tools for Office Runtime 版本。

## <a name="syntax"></a>Syntax

```xml
<vstoRuntime
    release
    version
    supportUrl />
```

## <a name="elements-and-attributes"></a>元素和屬性
 `vstoRuntime` 項目是必要的，且位於 `vstav3` 命名空間。 如果 Office 方案支援兩種 Visual Studio Tools for Office Runtime 版本，應用程式資訊清單中會有兩個 `vstoRuntime` 項目。

 `vstoRuntime` 項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`release`|必要。 Visual Studio Tools for Office Runtime 的發行版本。|
|`version`|必要。 Visual Studio Tools for Office Runtime 的版本號碼。|
|`supportUrl`|選擇性。 Visual Studio Tools for Office Runtime 的安裝位置連結。|

 `vstoRuntime` 沒有任何項目。

## <a name="example"></a>範例
 下列程式碼範例說明使用 `vstoRuntime` 所部署之 Office 方案的應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。

```xml
<vstav3:vstoRuntime
    release="VSTOR40Beta1"
    version="10.0.20303"
    supportUrl="http://www.microsoft.com" />
```

## <a name="see-also"></a>另請參閱

- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
