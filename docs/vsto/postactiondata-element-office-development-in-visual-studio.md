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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cda7829fc615c64be75f295a0cbc26b2ebbc7eea
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865433"
---
# <a name="ltpostactiondatagt-element-office-development-in-visual-studio"></a>&lt;postActionData&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `postActionData` 命名空間的 `vstav3` 項目指定與安裝 Office 方案後所執行之任何部署後動作相關聯的資料。

## <a name="syntax"></a>語法

```xml
<postActionData>
</postActionData>
```

## <a name="elements-and-attributes"></a>元素和屬性
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
