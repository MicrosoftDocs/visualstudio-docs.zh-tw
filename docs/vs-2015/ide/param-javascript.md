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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a8477de8bf84950d778d4ce843522be35b2d7387
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54772377"
---
# <a name="ltparamgt-javascript"></a>&lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在函式或方法指定為參數的文件資訊。  
  
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
 `name`  
 必要項。 參數名稱。  
  
 `type`  
 選擇性。 參數的資料型別。 類型可以是下列其中一項：  
  
- ECMAScript 語言輸入在 ECMAScript 5 規格中，例如`Number`和`Object`。  
  
- DOM 物件，例如`HTMLElement`， `Window`，和`Document`。  
  
- JavaScript 建構函式的函式。  
  
  `integer`  
  選擇性。 如果`type`是`Number`，指定參數是否為整數。 設定為`true`指出參數是整數; 否則設定為`false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
  `domElement`  
  選擇性。 這個屬性已被取代;`type`屬性會優先於此屬性。 這個屬性會指定記錄的參數是否為 DOM 項目。 設定為`true`指定的參數是 DOM 項目; 否則設定為`false`。 如果`type`未設定屬性和`domElement`設為`true`，IntelliSense 會記載的參數視為`HTMLElement`執行陳述式完成時。  
  
  `mayBeNull`  
  選擇性。 指定是否可以設定記錄的參數為 null。 設定為`true`若要表示為 null，否則，可以設定參數，設定為`false`。 預設值為 `false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
  `elementType`  
  選擇性。 如果`type`是`Array`，這個屬性會指定陣列中的項目類型。  
  
  `elementInteger`  
  選擇性。 如果`type`已`Array`並`elementType`是`Number`，這個屬性會指定是否在陣列中的項目都是整數。 設定為`true`來指出陣列中的項目都是整數; 否則設定為`false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
  `elementDomElement`  
  選擇性。 這個屬性已被取代;`elementType`屬性會優先於此屬性。 如果`type`是`Array`，這個屬性會指定陣列中的元素是否 DOM 項目。 設定為`true`指定之項目的 DOM 項目; 否則設定為`false`。 如果`elementType`未設定屬性和`elementDomElement`設為`true`，IntelliSense 會將做為陣列中的每個項目`HTMLElement`執行陳述式完成時。  
  
  `elementMayBeNull`  
  選擇性。 如果`type`是`Array`，指定是否可以設定在陣列中的項目為 null。 設定為`true`若要表示為 null，否則，可以設定在陣列中的項目，設定為`false`。 預設值為 `false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
  `locid`  
  選擇性。 如需參數的當地語系化資訊識別項。 識別項是成員識別碼或其對應至`name`屬性 OpenAjax 中繼資料所定義的訊息組合中的值。 識別項型別取決於所指定的格式[ \<loc >](../ide/loc-javascript.md)項目。  
  
  `parameterArray`  
  選擇性。 指定是否可以在函式呼叫中，類似於重複中支援的參數重複的記錄的參數`String.format`函式。 設定為`true`表示參數可以重複，否則為，設為`false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
  `optional`  
  選擇性。 指定是否已記錄的參數為選擇性呼叫函式。 設定為`true`若要指出參數是選擇性的; 否則，請設定為`false`。  
  
  `value`  
  選擇性。 指定應由 IntelliSense 用於評估，而不是函式程式碼本身的程式碼。 您可以使用這個屬性是未定義的參數類型時，提供型別資訊。 例如，您可以使用`value=’1’`將參數型別，表示為數字。  
  
  `description`  
  選擇性。 參數的描述。  
  
## <a name="remarks"></a>備註  
 唯一必要的屬性是`name`。 所有其他屬性是選擇性的。  
  
 用來標註函式，這類項目[\<摘要 >](../ide/summary-javascript.md)， [ \<param >](../ide/param-javascript.md)，以及[\<傳回 >](../ide/returns-javascript.md)，必須放中任何陳述式之前的函式主體。  
  
 如果有多個`<param>`具有相同的名稱，其中的項目`<param>`用項目，而且會忽略重複的項目。 未定義的行為，決定使用哪個項目。 如果`name`參考到不存在的參數，便會忽略的元素。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用`<param>`項目。  
  
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
  
## <a name="see-also"></a>請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)
