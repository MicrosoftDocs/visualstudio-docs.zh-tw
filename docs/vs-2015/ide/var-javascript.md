---
title: '&lt;var&gt; (JavaScript) |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <var> JavaScript XML tag
- var JavaScript XML tag
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d66c6a001d077fc68e99e479ac3352c8113f0c4e
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880392"
---
# <a name="ltvargt-javascript"></a>&lt;var&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[Visual Studio 2017 文件](/visualstudio/)。  
  
指定變數的文件資訊。  
  
## <a name="syntax"></a>語法  
  
```  
<var type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID">description  
</var>   
```  
  
#### <a name="parameters"></a>參數  
 `type`  
 選擇性。 變數的資料型別。 類型可以是下列其中一項：  
  
-   是在 ECMAScript 5 規格中，例如 ECMAScript 語言型別`Number`和`Object`。  
  
-   DOM 物件，例如`HTMLElement`， `Window`，和`Document`。  
  
-   JavaScript 建構函式的函式。  
  
 `integer`  
 選擇性。 如果`type`是`Number`，指定變數是否為整數。 設定為`true`來表示變數是整數; 否則設定為`false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
 `domElement`  
 選擇性。 這個屬性已被取代;`type`屬性會優先於此屬性。 這個屬性會指定所記錄的變數是否是 DOM 項目。 設定為`true`指定的變數是 DOM 項目; 否則設定為`false`。 如果`type`未設定屬性和`domElement`設為`true`，IntelliSense 會記載的變數視為`HTMLElement`執行陳述式完成時。  
  
 `mayBeNull`  
 選擇性。 指定是否可以設定記錄的變數為 null。 設定為`true`表示，可為 null，否則會設定這個變數，設為`false`。 預設值是 `false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
 `elementType`  
 選擇性。 如果`type`是`Array`，這個屬性會指定陣列中的項目類型。  
  
 `elementInteger`  
 選擇性。 如果`type`已`Array`並`elementType`是`Number`，這個屬性會指定是否在陣列中的項目都是整數。 設定為`true`來指出陣列中的項目都是整數; 否則設定為`false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
 `elementDomElement`  
 選擇性。 這個屬性已被取代;`elementType`屬性會優先於此屬性。 如果`type`是`Array`，這個屬性會指定陣列中的元素是否 DOM 項目。 設定為`true`指定之項目的 DOM 項目; 否則設定為`false`。 如果`elementType`未設定屬性和`elementDomElement`設為`true`，IntelliSense 會將做為陣列中的每個項目`HTMLElement`執行陳述式完成時。  
  
 `elementMayBeNull`  
 選擇性。 如果`type`是`Array`，指定是否可以設定在陣列中的項目為 null。 設定為`true`若要表示為 null，否則，可以設定在陣列中的項目，設定為`false`。 預設值是 `false`。 這個屬性不是由 Visual Studio 提供 IntelliSense 資訊。  
  
 `helpKeyword`  
 選擇性。 F1 說明關鍵字。  
  
 `locid`  
 選擇性。 如需變數的當地語系化資訊識別項。 識別項是成員識別碼或其對應至`name`屬性 OpenAjax 中繼資料所定義的訊息組合中的值。 識別項型別取決於所指定的格式[ \<loc >](../ide/loc-javascript.md)標記。  
  
 `description`  
 選擇性。 變數的描述。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用`<var>`項目。  
  
```javascript  
/// <var>A rectangle that has a width of 5.</var>  
var Rectangle = {  
    /// <field type = 'Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type = 'Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)



