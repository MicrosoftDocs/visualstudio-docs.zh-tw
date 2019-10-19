---
title: '&lt;deprecated &gt; （JavaScript） |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 343f3ebe4bea7ee999f60741c189f35defb0ac7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665810"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;deprecated&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定取代函式或方法。

## <a name="syntax"></a>語法

```
<deprecated
    type="deprecate|remove"
    locid="descriptionID">description
</deprecated>
```

#### <a name="parameters"></a>參數
 `type` 選擇項。 指定是否要在未來的版本中移除函式或方法，或是函式或方法是否已移除，而且其使用方式可能會導致錯誤。 設定為 `deprecate` 以指定未來版本將移除函式或方法。 設定為 `remove`，指定已移除函式或方法。

 `locid` 選擇項。 關於函式或方法的當地語系化資訊識別項。 該識別項會是成員識別碼，或對應由 OpenAjax 中繼資料所定義訊息包中的 `name` 屬性值。 識別項類型會依據在 [\<loc>](../ide/loc-javascript.md) 元素中指定的格式而有所不同。

 `description` 選擇項。 即將淘汰之函數或方法的描述。

## <a name="remarks"></a>備註
 用來標注函式的元素（包括 `<deprecated>`）必須放在函式主體中的任何語句之前。 當您將函式標示為已被取代時，建議您將其[\<summary >](../ide/summary-javascript.md)元素取代為 `<deprecated>` 元素。

## <a name="example"></a>範例
 下列程式碼示範如何使用 `<deprecated>` 元素。

```javascript
function areaFunction(radiusParam) {
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

```

## <a name="see-also"></a>另請參閱
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)
