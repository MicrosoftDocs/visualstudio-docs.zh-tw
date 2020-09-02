---
title: '&lt;&gt; (JavaScript) 的欄位 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a3fc786e4d99d1eaff4a8b152ea9496ce8400ff1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663861"
---
# <a name="ltfieldgt-javascript"></a>&lt;field&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

針對物件上定義的欄位或成員，指定檔資訊，包括描述。

## <a name="syntax"></a>語法

```
<field name="fieldName" static="true|false"
    type="FieldType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    helpKeyword="keyword" locid="descriptionID"
    value="code">description
</field>
```

#### <a name="parameters"></a>參數
 `name` 欄位或成員的名稱。 在函式 `<field>` 函數中使用專案時， `name` 是必要的，而且會定義標記套用的成員。 當專案 `<field>` 直接批註欄位時，會忽略這個屬性，而且 Visual Studio 使用的名稱是原始程式碼中的實際欄位名稱。

 `static` 選擇項。 指定欄位是否為函式函數的成員，或由函式函數傳回之物件的成員。 將設定為， `true` 以將欄位視為函式函數的成員。 設定為，會將 `false` 欄位視為由函式函數所傳回之物件的成員。

 `type` 選擇項。 欄位的資料類型。 類型可以是下列其中之一：

- ECMAScript 5 規格中的 ECMAScript 語言類型，例如 `Number` 和 `Object` 。

- DOM 物件，例如 `HTMLElement`、`Window`和 `Document`。

- JavaScript 建構函式。

  `integer` 選擇項。 如果 `type` 為 `Number` ，則指定欄位是否為整數。 設定為， `true` 表示欄位為整數; 否則設定為 `false` 。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。

  `domElement` 選擇項。 這個屬性已取代為優先於其的 `type` 屬性。 這個屬性會指定記載的欄位是否為 DOM 元素。 設定為， `true` 指定欄位為 DOM 元素; 否則設定為 `false` 。 如果 `type` 屬性未設定且 `domElement` 設定為 `true` ，則 IntelliSense 會 `HTMLElement` 在執行語句完成時，將記載的欄位視為。

  `mayBeNull` 選擇項。 指定記載的欄位是否可以設定為 null。 設定為， `true` 表示欄位可以設定為 null; 否則設定為 `false` 。 預設值是 `false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。

  `elementType` 選擇項。 如果 `type` 是 `Array`，這個屬性會指定陣列中的元素類型。

  `elementInteger` 選擇項。 如果 `type` 是 `Array` 且 `elementType` 是 `Number`，這個屬性會指定陣列中的元素是否為整數。 設定為 `true` 指出陣列中的元素為整數；否則設定為 `false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。

  `elementDomElement` 選擇項。 這個屬性已取代為優先於其的 `elementType` 屬性。 如果 `type` 是 `Array`，這個屬性會指定陣列中的元素是否為 DOM 元素。 設定為 `true` 指定該元素為 DOM 元素；否則設定為 `false`。 如果未設定 `elementType` 屬性，而且 `elementDomElement` 設定為 `true`，IntelliSense 就會在執行陳述式完成時，將陣列中的每個元素視為 `HTMLElement`。

  `elementMayBeNull` 選擇項。 如果 `type` 是 `Array`，會指定陣列中的元素是否可設定為 Null。 設定為 `true` 指出陣列中的元素可設定為 Null；否則設定為 `false`。 預設值是 `false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。

  `helpKeyword` 選擇項。 F1 說明的關鍵字。

  `locid` 選擇項。 有關欄位之當地語系化資訊的識別碼。 該識別項會是成員識別碼，或對應由 OpenAjax 中繼資料所定義訊息包中的 `name` 屬性值。 識別碼類型取決於在標記中指定的格式 [\<loc>](../ide/loc-javascript.md) 。

  `value` 選擇項。 指定應評估以供 IntelliSense 使用的程式碼，而不是函式程式碼本身。 若為，則表示 `<field>` 此屬性支援函式，但不支持對象常值。 當欄位類型未定義時，您可以使用這個屬性來提供類型資訊。 例如，您可以使用 `value=’1’` 將欄位類型視為數位。

  `description` 選擇項。 欄位的描述。

## <a name="remarks"></a>備註
 `name`當您在函式函數中記錄欄位時，需要屬性。 針對其他所有案例，元素的所有屬性 `<field>` 都是選擇性的。

 當您在記錄函式函式時， `<field>` 元素必須緊接在欄位宣告之前出現。 `name`屬性必須符合原始程式碼中使用的功能變數名稱。 對於物件成員而言， `name` 如果專案緊接在物件成員宣告之前，就可以省略屬性 `<field>` 。

## <a name="example"></a>範例
 下列程式碼範例示範如何使用 `<field>` 元素。

```javascript
// Use of <field> in an object definition.
var Rectangle = {
    /// <field type='Number'>The width of the rectangle.</field>
    wid: 5,
    /// <field type='Number'>The length of the rectangle.</field>
    len: 0,
    /// <field type='Number'>Returns the area of the rectangle.</field>
    getArea: function (wid, len) {
        return len * wid;
    }
}

// Use of <field> in a constructor function.
// The name attribute is required.
function Engine() {
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
    this.HorsePower = 150;
}
```

## <a name="example"></a>範例
 下列範例顯示如何使用 `<field>` `static` 屬性設定為的專案 `true` 。

```javascript
function Engine() {
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>
}

Engine.HorsePower = 140;
// IntelliSense on the field is available here.
Engine.

```

## <a name="example"></a>範例
 下列範例顯示如何使用 `<field>` `static` 屬性設定為的專案 `false` 。

```javascript
function Engine() {
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>
}

Engine.HorsePower = 140;
var eng = new Engine();
// IntelliSense on the field is available here.
eng.

```

## <a name="example"></a>範例
 下列範例示範如何使用 `<field>` 具有屬性的元素 `value` 。

```javascript
function calculator(a) {
    /// <field name='f' value='1'/>
}
new calculator().f.   // Completion list for a Number.

```

## <a name="see-also"></a>另請參閱
 [XML 檔批註](../ide/xml-documentation-comments-javascript.md)
