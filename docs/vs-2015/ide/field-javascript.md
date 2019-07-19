---
title: '&lt;欄位&gt;(JavaScript) |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b2fe09070261460b7b83f54de44a07cf96d40cf2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181266"
---
# <a name="ltfieldgt-javascript"></a>&lt;field&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定文件資訊，包括描述欄位或物件定義的成員。  
  
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
 `name`  
 欄位或成員的名稱。 當`<field>`項目會在建構函式，`name`是必要的會定義要套用標記的成員。 當`<field>`項目直接標註 欄位中，會忽略此屬性，和 Visual Studio 所使用的名稱是在原始程式碼中的實際欄位名稱。  
  
 `static`  
 選擇性。 指定欄位是建構函式的成員或建構函式函數所傳回之物件的成員。 若要設定`true`將欄位視為建構函式的成員。 若要設定`false`將欄位視為建構函式所傳回之物件的成員。  
  
 `type`  
 選擇性。 欄位資料型別。 類型可以是下列其中之一：  
  
- ECMAScript 語言輸入在 ECMAScript 5 規格中，例如`Number`和`Object`。  
  
- DOM 物件，例如 `HTMLElement`、`Window`和 `Document`。  
  
- JavaScript 建構函式。  
  
  `integer`  
  選擇性。 如果`type`是`Number`，指定欄位是否為整數。 設定為`true`，表示欄位是整數; 否則設定為`false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。  
  
  `domElement`  
  選擇性。 這個屬性已取代為優先於其的 `type` 屬性。 這個屬性指定的 DOM 項目是否包含記錄的欄位。 設定為`true`若要指定欄位是 DOM 項目; 否則設定為`false`。 如果`type`未設定屬性和`domElement`設為`true`，IntelliSense 會將記錄的欄位視為`HTMLElement`執行陳述式完成時。  
  
  `mayBeNull`  
  選擇性。 指定是否可以設定 [記錄] 欄位為 null。 設定為`true`若要表示的欄位設定為 null，否則將為`false`。 預設值為 `false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。  
  
  `elementType`  
  選擇性。 如果 `type` 是 `Array`，這個屬性會指定陣列中的元素類型。  
  
  `elementInteger`  
  選擇性。 如果 `type` 是 `Array` 且 `elementType` 是 `Number`，這個屬性會指定陣列中的元素是否為整數。 設定為 `true` 指出陣列中的元素為整數；否則設定為 `false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。  
  
  `elementDomElement`  
  選擇性。 這個屬性已取代為優先於其的 `elementType` 屬性。 如果 `type` 是 `Array`，這個屬性會指定陣列中的元素是否為 DOM 元素。 設定為 `true` 指定該元素為 DOM 元素；否則設定為 `false`。 如果未設定 `elementType` 屬性，而且 `elementDomElement` 設定為 `true`，IntelliSense 就會在執行陳述式完成時，將陣列中的每個元素視為 `HTMLElement`。  
  
  `elementMayBeNull`  
  選擇性。 如果 `type` 是 `Array`，會指定陣列中的元素是否可設定為 Null。 設定為 `true` 指出陣列中的元素可設定為 Null；否則設定為 `false`。 預設值為 `false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。  
  
  `helpKeyword`  
  選擇性。 F1 說明的關鍵字。  
  
  `locid`  
  選擇性。 如需欄位的當地語系化資訊識別項。 該識別項會是成員識別碼，或對應由 OpenAjax 中繼資料所定義訊息包中的 `name` 屬性值。 識別項類型會依據在 [\<loc>](../ide/loc-javascript.md) 標籤中指定的格式而有所不同。  
  
  `value`  
  選擇性。 指定應由 IntelliSense 用於評估，而不是函式程式碼本身的程式碼。 針對`<field>`，這個屬性支援的建構函式，但是不支援物件常值。 您可以使用這個屬性是未定義的欄位型別時，提供類型資訊。 例如，您可以使用`value=’1’`將欄位型別，表示為數字。  
  
  `description`  
  選擇性。 欄位描述。  
  
## <a name="remarks"></a>備註  
 `name`屬性是必要的當您要加入註解的建構函式中的欄位。 對於所有其他案例中，所有屬性，如`<field>`是選擇性的項目。  
  
 當您要加入註解的建構函式，`<field>`項目必須出現之前欄位宣告。 `name`屬性必須符合在原始程式碼中使用的欄位名稱。 物件成員`name`可以省略屬性，如果`<field>`之前物件成員宣告的項目會出現。  
  
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
 下列範例示範如何使用`<field>`具有項目`static`屬性設為`true`。  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`<field>`具有項目`static`屬性設為`false`。  
  
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
 下列範例示範如何使用`<field>`具有項目`value`屬性。  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)
