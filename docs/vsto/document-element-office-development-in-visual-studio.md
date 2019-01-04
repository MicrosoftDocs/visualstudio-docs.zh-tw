---
title: '&lt;文件&gt;元素 （在 Visual Studio 中的 Office 程式開發）'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2c1798815ee3216d6f3bb41eae70ae3e2cdc0121
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854748"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;文件&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `document`項目`vstov4`命名空間會儲存文件層級自訂的自訂特定資訊。

## <a name="syntax"></a>語法

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>項目和屬性
 只有需要文件層級自訂。 `document` 元素位於 `vstov4` 命名空間。 `document` 項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`solutionId`|必要項。 Visual Studio Tools for Office 執行階段用來唯一識別文件層級方案的 GUID。 這個值會儲存為 _AssemblyLocation 自訂文件屬性。 如需詳細資訊，請參閱 <<c0> [ 自訂文件屬性概觀](../vsto/custom-document-properties-overview.md)。|

 `document` 沒有任何子項目。

## <a name="document-level-customization-example"></a>文件層級自訂範例

### <a name="description"></a>描述
 下列程式碼範例說明`document`您可以使用部署之文件層級 Office 方案中的項目[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]。 此程式碼範例是中提供之較大範例的一部分[Application manifests for Office 方案](../vsto/application-manifests-for-office-solutions.md)。

### <a name="code"></a>程式碼

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>另請參閱

- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)