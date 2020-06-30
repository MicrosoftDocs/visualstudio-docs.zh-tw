---
title: '&lt;d &gt; 元素（Visual Studio 中的 Office 開發）'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 689848f14b4540a54489b4ea5bbad67e493fe276
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544907"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;d &gt; 元素（Visual Studio 中的 Office 開發）
  `customHostSpecified`元素表示此方案不是獨立應用程式。 Office 方案包含裝載于 Microsoft Office 應用程式內的元件。

## <a name="syntax"></a>語法

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>元素和屬性
 `customHostSpecified`Office 方案需要元素。 此元素位於 `co.v1` 命名空間中，指定此部署包含將部署在自訂主機內且不是獨立應用程式的元件。

 這個元素是 `<entrypoint>` 應用程式資訊清單中第一個元素的子系。 該元素中不能有其他子項目， `<entrypoint>` 或在 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 安裝期間將會引發驗證錯誤。

 這個元素沒有屬性，而且沒有子專案。

## <a name="example"></a>範例
 下列程式碼範例說明 `customHostSpecified` Office 方案的應用程式資訊清單中的元素。 這個程式碼範例是[Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中提供之較大範例的一部分。

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>另請參閱

- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)