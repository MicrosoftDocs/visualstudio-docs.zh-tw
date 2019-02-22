---
title: '&lt;傳回&gt;(JavaScript) |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 81a9a42a104adb2a9d9a9aba483e2588d7332868
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54801772"
---
# <a name="ltreturnsgt-javascript"></a>&lt;returns&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定函式或方法呼叫的結果文件資訊。  
  
## <a name="syntax"></a>語法  
  
```  
<returns type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID" value="code">description  
</returns>  
```  
  
#### <a name="parameters"></a>參數  
 `type`  
 選擇性。 傳回值的資料型別。 類型可以是下列其中一項：  
  
- ECMAScript 語言輸入在 ECMAScript 5 規格中，例如`Number`和`Object`。  
  
- DOM 物件，例如`HTMLElement`， `Window`，和`Document`。  
  
- JavaScript 建構函式的函式。  
  
  `integer`  
  選擇性。 如果`type`是`Number`，指定傳回的值是否為整數。 設定為`true`表示傳回的值是整數; 否則設定為`false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
  `domElement`  
  選擇性。 這個屬性已被取代;`type`屬性會優先於此屬性。 這個屬性會指定所記錄的傳回值是否是 DOM 項目。 設定為`true`以指定的傳回值是 DOM 項目; 否則設定為`false`。 如果`type`未設定屬性和`domElement`設為`true`，IntelliSense 會記載的傳回值視為`HTMLElement`執行陳述式完成時。  
  
  `mayBeNull`  
  選擇性。 指定是否記錄傳回值可以設定為 null。 設定為`true`表示，傳回的值可以設定為 null，否則設定為`false`。 預設值為 `false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
  `elementType`  
  選擇性。 如果`type`是`Array`，這個屬性會指定陣列中的項目類型。  
  
  `elementInteger`  
  選擇性。 如果`type`已`Array`並`elementType`是`Number`，這個屬性會指定是否在陣列中的項目都是整數。 設定為`true`來指出陣列中的項目都是整數; 否則設定為`false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
  `elementDomElement`  
  選擇性。 這個屬性已被取代;`elementType`屬性會優先於此屬性。 如果`type`是`Array`，這個屬性會指定陣列中的元素是否 DOM 項目。 設定為`true`指定之項目的 DOM 項目; 否則設定為`false`。 如果`elementType`未設定屬性和`elementDomElement`設為`true`，IntelliSense 會將做為陣列中的每個項目`HTMLElement`執行陳述式完成時。  
  
  `elementMayBeNull`  
  選擇性。 如果`type`是`Array`，指定是否可以設定在陣列中的項目為 null。 設定為`true`若要表示為 null，否則，可以設定在陣列中的項目，設定為`false`。 預設值為 `false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
  `locid`  
  選擇性。 如需傳回值的當地語系化資訊識別項。 識別項是成員識別碼或其對應至`name`屬性 OpenAjax 中繼資料所定義的訊息組合中的值。 識別項型別取決於所指定的格式[ \<loc >](../ide/loc-javascript.md)標記。  
  
  `value`  
  選擇性。 指定應由 IntelliSense 用於評估，而不是函式程式碼本身的程式碼。 例如，您可以使用這個屬性提供 IntelliSense 的非同步回呼，例如`Promise`。 使用`value`屬性搭配`<returns>`項目可以改善 IntelliSense 效能，藉由略過執行冗長的程式碼。  
  
  `description`  
  選擇性。 傳回值的描述。  
  
## <a name="remarks"></a>備註  
 `<returns>`項目必須放在任何陳述式之前的函式主體。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用`<returns>`項目。  
  
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
  
// The following examples use the <remarks> element with a value attribute.  
  
function getJson(complete) {   
    /// <returns value='complete("")' ></returns>  
    var r = new XMLHttpRequest();   
    // . . .   
}   
  
getJson(function (json) {   
    json.  // IntelliSense for a String object is   
           // available here.  
});  
  
function calculate(x) {  
    /// <returns value='1'/>  
}  
calculate().  // Completion list for a Number.  
  
```  
  
## <a name="see-also"></a>請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)
