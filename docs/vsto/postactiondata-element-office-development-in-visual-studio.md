---
title: '&lt;postActionData&gt;元素 （在 Visual Studio 中的 Office 程式開發）'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f27cf59f157c0760ea0c204a8c079dd4616777da
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947266"
---
# <a name="ltpostactiondatagt-element-office-development-in-visual-studio"></a>&lt;postActionData&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `postActionData` 命名空間的 `vstav3` 項目指定與安裝 Office 方案後所執行之任何部署後動作相關聯的資料。

## <a name="syntax"></a>語法

```xml
<postActionData>
</postActionData>
```

## <a name="elements-and-attributes"></a>項目和屬性
 `postActionData` 項目是選擇項，且位於 `vstav3` 命名空間。 在應用程式資訊清單中，會為每個部署後動作定義一個 `postActionData` 項目。

 `postActions` 項目沒有任何屬性。

 `postActions` 沒有任何子項目。

## <a name="post-deployment-action-example"></a>部署後動作範例

### <a name="description"></a>描述
 下列程式碼範例說明使用 `postAction` 所部署之 Office 方案的應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 此程式碼範例是中提供之較大範例的一部分[Application manifests for Office 方案](../vsto/application-manifests-for-office-solutions.md)。

### <a name="code"></a>程式碼

```xml
<vstav3:postActionData>
  data in any format
</vstav3:postActionData>
```

## <a name="see-also"></a>另請參閱

- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
