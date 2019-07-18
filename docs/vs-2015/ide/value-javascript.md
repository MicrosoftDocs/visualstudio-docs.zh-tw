---
title: '&lt;值&gt;(JavaScript) |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ac74dde41a2d6cea0a768cfc89838cc34ce41afd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179316"
---
# <a name="ltvaluegt-javascript"></a>&lt;&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定文件資訊`get`和`set`ECMAScript 3 屬性的函式。  
  
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
 `type`  
 選擇性。 屬性的資料類型。 類型可以是下列其中之一：  
  
- ECMAScript 5 規格中的 ECMAScript 語言類型，例如 `Number` 和 `Object`。  
  
- DOM 物件，例如 `HTMLElement`、`Window`和 `Document`。  
  
- JavaScript 建構函式。  
  
  `integer`  
  選擇性。 如果`type`是`Number`，指定屬性是否為整數。 設定為`true`表示此屬性是整數; 否則設定為`false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。  
  
  `domElement`  
  選擇性。 這個屬性已取代為優先於其的 `type` 屬性。 這個屬性指定的 DOM 項目是否包含文件的屬性。 設定為`true`指定的屬性是 DOM 項目; 否則設定為`false`。 如果`type`未設定屬性和`domElement`設為`true`，IntelliSense 會將文件的屬性視為`HTMLElement`執行陳述式完成時。  
  
  `mayBeNull`  
  選擇性。 指定是否可以設定 [記錄] 屬性設為 null。 設定為`true`若要指出，屬性可以設定為 null，否則，請設定為`false`。 預設值為 `false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。  
  
  `elementType`  
  選擇性。 如果 `type` 是 `Array`，這個屬性會指定陣列中的元素類型。  
  
  `elementInteger`  
  選擇性。 如果 `type` 是 `Array` 且 `elementType` 是 `Number`，這個屬性會指定陣列中的元素是否為整數。 設定為 `true` 指出陣列中的元素為整數；否則設定為 `false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。  
  
  `elementDomElement`  
  選擇性。 這個屬性已取代為優先於其的 `elementType` 屬性。 如果 `type` 是 `Array`，這個屬性會指定陣列中的元素是否為 DOM 元素。 設定為 `true` 指定該元素為 DOM 元素；否則設定為 `false`。 如果未設定 `elementType` 屬性，而且 `elementDomElement` 設定為 `true`，IntelliSense 就會在執行陳述式完成時，將陣列中的每個元素視為 `HTMLElement`。  
  
  `elementMayBeNull`  
  選擇性。 如果 `type` 是 `Array`，會指定陣列中的元素是否可設定為 Null。 設定為 `true` 指出陣列中的元素可設定為 Null；否則設定為 `false`。 預設值為 `false`。 Visual Studio 未使用這個屬性來提供 IntelliSense 資訊。  
  
  `locid`  
  選擇性。 如需屬性的當地語系化資訊識別項。 該識別項會是成員識別碼，或對應由 OpenAjax 中繼資料所定義訊息包中的 `name` 屬性值。 識別項類型會依據在 [\<loc>](../ide/loc-javascript.md) 元素中指定的格式而有所不同。  
  
  `description`  
  選擇性。 屬性的說明。  
  
## <a name="remarks"></a>備註  
 ECMAScript 5 屬性使用[\<摘要 >](../ide/summary-javascript.md)項目。  
  
 使用`<value>`項目之前，立即`get`或`set`函式。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用`<value>`上的項目`get`函式。  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)
