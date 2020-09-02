---
title: '&lt;param&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca6207d22d82e607fa589f944230b36b46e633c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670365"
---
# <a name="ltparamgt-javascript"></a>&lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定函數或方法中參數的檔資訊。

## <a name="syntax"></a>語法

```
<param name="parameterName" type="ParameterType"
    integer="true|false" domElement="true|false"
    mayBeNull="true|false" elementType="ArrayElementType"
    elementInteger="true|false" elementDomElement="true|false"
    elementMayBeNull="true|false" locid="descriptionID"
    parameterArray="true|false" optional="true|false"
    value="code">description
</param>
```

#### <a name="parameters"></a>參數
 需要 `name`。 參數名稱。

 `type` 選擇項。 參數的資料類型。 類型可以是下列其中之一：

- ECMAScript 5 規格中的 ECMAScript 語言類型，例如 `Number` 和 `Object` 。

- DOM 物件，例如 `HTMLElement`、`Window`和 `Document`。

- JavaScript 建構函式。

  `integer` 選擇項。 如果 `type` 為 `Number` ，則指定參數是否為整數。 設定為， `true` 表示參數為整數; 否則設定為 `false` 。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。

  `domElement` 選擇項。 這個屬性已取代為優先於其的 `type` 屬性。 這個屬性會指定記載的參數是否為 DOM 元素。 設定為， `true` 指定參數為 DOM 元素; 否則設定為 `false` 。 如果 `type` 屬性未設定且 `domElement` 設定為，則 IntelliSense 會在 `true` `HTMLElement` 執行語句完成時，將記載的參數視為。

  `mayBeNull` 選擇項。 指定記載的參數是否可以設定為 null。 設定為， `true` 表示參數可以設定為 null，否則設定為 `false` 。 預設值是 `false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。

  `elementType` 選擇項。 如果 `type` 是 `Array`，這個屬性會指定陣列中的元素類型。

  `elementInteger` 選擇項。 如果 `type` 是 `Array` 且 `elementType` 是 `Number`，這個屬性會指定陣列中的元素是否為整數。 設定為 `true` 指出陣列中的元素為整數；否則設定為 `false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。

  `elementDomElement` 選擇項。 這個屬性已取代為優先於其的 `elementType` 屬性。 如果 `type` 是 `Array`，這個屬性會指定陣列中的元素是否為 DOM 元素。 設定為 `true` 指定該元素為 DOM 元素；否則設定為 `false`。 如果未設定 `elementType` 屬性，而且 `elementDomElement` 設定為 `true`，IntelliSense 就會在執行陳述式完成時，將陣列中的每個元素視為 `HTMLElement`。

  `elementMayBeNull` 選擇項。 如果 `type` 是 `Array`，會指定陣列中的元素是否可設定為 Null。 設定為 `true` 指出陣列中的元素可設定為 Null；否則設定為 `false`。 預設值是 `false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。

  `locid` 選擇項。 有關參數之當地語系化資訊的識別碼。 該識別項會是成員識別碼，或對應由 OpenAjax 中繼資料所定義訊息包中的 `name` 屬性值。 識別碼類型取決於元素中指定的格式 [\<loc>](../ide/loc-javascript.md) 。

  `parameterArray` 選擇項。 指定是否可以在函式呼叫中重複記載的參數，類似于函式中支援的重複參數 `String.format` 。 如果設定為， `true` 表示可以重複參數; 否則，請將設定為 `false` 。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。

  `optional` 選擇項。 指定在呼叫函式中，記錄的參數是否為選擇性。 設定為， `true` 表示參數為選擇性，否則設定為 `false` 。

  `value` 選擇項。 指定應評估以供 IntelliSense 使用的程式碼，而不是函式程式碼本身。 當參數類型為未定義時，您可以使用這個屬性來提供類型資訊。 例如，您可以使用 `value=’1’` 將參數類型視為數位。

  `description` 選擇項。 參數的描述。

## <a name="remarks"></a>備註
 唯一必要的屬性為 `name` 。 其他所有屬性都是選擇性的。

 用來標注函式的元素（例如 [\<summary>](../ide/summary-javascript.md) 、 [\<param>](../ide/param-javascript.md) 和 [\<returns>](../ide/returns-javascript.md) ）必須放在函式主體中，才能在任何語句之前。

 如果有多個專案 `<param>` 具有相同的名稱，則 `<param>` 會使用其中一個元素，並忽略多餘的元素。 未定義所要使用之元素的行為。 如果 `name` 參考不存在的參數，則會忽略元素。

## <a name="example"></a>範例
 下列程式碼範例示範如何使用 `<param>` 元素。

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

// Uses of <param> with the value attribute.

function calculate(a) {
    /// <param name='a' value='1'/>
    a.    // Completion list for a Number.
}

function calculate(a) {
    /// <param name='a' value='{x:0,y:0}'/>
    a.    // x and y appear in the completion list.
}

```

## <a name="see-also"></a>另請參閱
 [XML 檔批註](../ide/xml-documentation-comments-javascript.md)
