---
title: toJSON 方法 （日期） (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toJSON method
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a131c7b248ca0486ab0b3b02d40e4351136c37c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641288"
---
# <a name="tojson-method-date-javascript"></a>toJSON 方法 (日期) (JavaScript)
使用[JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)方法讓 JavaScript 物件標記法 (JSON) 序列化的物件資料的轉換。  
  
## <a name="syntax"></a>語法  
  
```  
  
objectname.toJSON()  
```  
  
## <a name="parameters"></a>參數  
 `objectname`  
 必要項。 想要的 json 序列化物件。  
  
## <a name="remarks"></a>備註  
 `toJSON`方法由`JSON.stringify`函式。 `JSON.stringify`將序列化[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]為 JSON 文字的值。 如果`toJSON`方法提供來`JSON.stringify`、`toJSON`方法時，會呼叫`JSON.stringify`呼叫。  
  
 `toJSON`方法是內建成員[日期](../../javascript/reference/date-object-javascript.md)[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件。 它會傳回 UTC 時區為準 （後置詞 Z 表示） 的 ISO 格式的日期字串。  
  
 您可以覆寫`toJSON`方法`Date`類型，或定義`toJSON`達到特定的物件型別 JSON 序列化之前的資料轉換的其他物件類型的方法。  
  
## <a name="example"></a>範例  
 下列範例會使用`toJSON`方法，以序列化字串成員值以大寫表示。 `toJSON`方法時，會呼叫`JSON.stringify`呼叫。  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## <a name="example"></a>範例  
 下列範例說明如何使用`toJSON`方法的內建成員[日期](../../javascript/reference/date-object-javascript.md)物件。  
  
```JavaScript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]**適用於：** [日期物件](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [JSON 物件](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse 函式](../../javascript/reference/json-parse-function-javascript.md)   
 [JSON.stringify 函式](../../javascript/reference/json-stringify-function-javascript.md)   
 [JavaScript 方法](../../javascript/reference/javascript-methods.md)