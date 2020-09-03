---
title: '&lt;&gt; (JavaScript) 的值 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aefe710cc730d5624abc01bbdfc54d9961788787
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656391"
---
# <a name="ltvaluegt-javascript"></a>&lt;&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

針對 `get` ECMAScript 3 屬性的和函數指定檔資訊 `set` 。

## <a name="syntax"></a>語法

```
<value type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID">description
</value>
```

#### <a name="parameters"></a>參數
 `type` 選擇項。 屬性的資料型別。 類型可以是下列其中之一：

- ECMAScript 5 規格中的 ECMAScript 語言類型，例如 `Number` 和 `Object`。

- DOM 物件，例如 `HTMLElement`、`Window`和 `Document`。

- JavaScript 建構函式。

  `integer` 選擇項。 如果 `type` 為 `Number` ，則指定屬性是否為整數。 設定為， `true` 表示此屬性為整數，否則設定為 `false` 。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。

  `domElement` 選擇項。 這個屬性已取代為優先於其的 `type` 屬性。 這個屬性會指定記載的屬性是否為 DOM 元素。 設定為， `true` 以指定屬性為 DOM 元素; 否則設定為 `false` 。 如果 `type` 屬性未設定且 `domElement` 設定為 `true` ，IntelliSense 會在 `HTMLElement` 執行語句完成時，將記載的屬性視為。

  `mayBeNull` 選擇項。 指定記載的屬性是否可以設定為 null。 設定為， `true` 表示屬性可以設定為 null，否則設定為 `false` 。 預設值是 `false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。

  `elementType` 選擇項。 如果 `type` 是 `Array`，這個屬性會指定陣列中的元素類型。

  `elementInteger` 選擇項。 如果 `type` 是 `Array` 且 `elementType` 是 `Number`，這個屬性會指定陣列中的元素是否為整數。 設定為 `true` 指出陣列中的元素為整數；否則設定為 `false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。

  `elementDomElement` 選擇項。 這個屬性已取代為優先於其的 `elementType` 屬性。 如果 `type` 是 `Array`，這個屬性會指定陣列中的元素是否為 DOM 元素。 設定為 `true` 指定該元素為 DOM 元素；否則設定為 `false`。 如果未設定 `elementType` 屬性，而且 `elementDomElement` 設定為 `true`，IntelliSense 就會在執行陳述式完成時，將陣列中的每個元素視為 `HTMLElement`。

  `elementMayBeNull` 選擇項。 如果 `type` 是 `Array`，會指定陣列中的元素是否可設定為 Null。 設定為 `true` 指出陣列中的元素可設定為 Null；否則設定為 `false`。 預設值是 `false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。

  `locid` 選擇項。 有關屬性之當地語系化資訊的識別碼。 該識別項會是成員識別碼，或對應由 OpenAjax 中繼資料所定義訊息包中的 `name` 屬性值。 識別碼類型取決於元素中指定的格式 [\<loc>](../ide/loc-javascript.md) 。

  `description` 選擇項。 屬性的描述。

## <a name="remarks"></a>備註
 ECMAScript 5 屬性使用 [\<summary>](../ide/summary-javascript.md) 元素。

 在或函式 `<value>` 之前使用 `get` 元素 `set` 。

## <a name="example"></a>範例
 下列程式碼範例示範如何使用函式 `<value>` 上的元素 `get` 。

```javascript
function Sys$CancelEventArgs$get_cancel() {
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>
    if (arguments.length !== 0) throw Error.parameterCount();
    return this._cancel();
}
```

## <a name="see-also"></a>另請參閱
 [XML 檔批註](../ide/xml-documentation-comments-javascript.md)
