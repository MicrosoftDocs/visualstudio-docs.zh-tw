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
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54799138"
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
 選擇性。 屬性的資料類型。 類型可以是下列其中一項：  
  
- 是在 ECMAScript 5 規格中，例如 ECMAScript 語言型別`Number`和`Object`。  
  
- DOM 物件，例如`HTMLElement`， `Window`，和`Document`。  
  
- JavaScript 建構函式的函式。  
  
  `integer`  
  選擇性。 如果`type`是`Number`，指定屬性是否為整數。 設定為`true`表示此屬性是整數; 否則設定為`false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
  `domElement`  
  選擇性。 這個屬性已被取代;`type`屬性會優先於此屬性。 這個屬性指定的 DOM 項目是否包含文件的屬性。 設定為`true`指定的屬性是 DOM 項目; 否則設定為`false`。 如果`type`未設定屬性和`domElement`設為`true`，IntelliSense 會將文件的屬性視為`HTMLElement`執行陳述式完成時。  
  
  `mayBeNull`  
  選擇性。 指定是否可以設定 [記錄] 屬性設為 null。 設定為`true`若要指出，屬性可以設定為 null，否則，請設定為`false`。 預設值為 `false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
  `elementType`  
  選擇性。 如果`type`是`Array`，這個屬性會指定陣列中的項目類型。  
  
  `elementInteger`  
  選擇性。 如果`type`已`Array`並`elementType`是`Number`，這個屬性會指定是否在陣列中的項目都是整數。 設定為`true`來指出陣列中的項目都是整數; 否則設定為`false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
  `elementDomElement`  
  選擇性。 這個屬性已被取代;`elementType`屬性會優先於此屬性。 如果`type`是`Array`，這個屬性會指定陣列中的元素是否 DOM 項目。 設定為`true`指定之項目的 DOM 項目; 否則設定為`false`。 如果`elementType`未設定屬性和`elementDomElement`設為`true`，IntelliSense 會將做為陣列中的每個項目`HTMLElement`執行陳述式完成時。  
  
  `elementMayBeNull`  
  選擇性。 如果`type`是`Array`，指定是否可以設定在陣列中的項目為 null。 設定為`true`若要表示為 null，否則，可以設定在陣列中的項目，設定為`false`。 預設值為 `false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
  `locid`  
  選擇性。 如需屬性的當地語系化資訊識別項。 識別項是成員識別碼或其對應至`name`屬性 OpenAjax 中繼資料所定義的訊息組合中的值。 識別項型別取決於所指定的格式[ \<loc >](../ide/loc-javascript.md)項目。  
  
  `description`  
  選擇性。 屬性的描述。  
  
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
  
## <a name="see-also"></a>請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)
