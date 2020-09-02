---
title: '&lt;檔 &gt; 元素 (Visual Studio) 的 Office 開發'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 36d822d60d1a28d48f660f6d358b75bf4a913048
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "63000034"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;檔 &gt; 元素 (Visual Studio) 的 Office 開發
  `document`命名空間的元素會 `vstov4` 儲存檔層級自訂的自訂特定資訊。

## <a name="syntax"></a>語法

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>元素和屬性
 只有檔層級自訂才需要。 `document` 元素位於 `vstov4` 命名空間。 `document` 項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`solutionId`|必要。 Visual Studio Tools for Office 執行時間用來唯一識別檔層級方案的 GUID。 此值會儲存為 _AssemblyLocation 自訂文件屬性。 如需詳細資訊，請參閱 [自訂文件屬性總覽](../vsto/custom-document-properties-overview.md)。|

 `document` 沒有任何子項目。

## <a name="document-level-customization-example"></a>檔層級自訂範例

### <a name="description"></a>描述
 下列程式碼範例說明 `document` 使用部署之檔層級 Office 方案中的元素 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。

### <a name="code"></a>程式碼

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>另請參閱

- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)