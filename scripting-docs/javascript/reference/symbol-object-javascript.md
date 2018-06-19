---
title: 符號物件 (JavaScript) |Microsoft 文件
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
ms.assetid: 2ad059f1-4b7f-4758-882a-c74ce1283ab0
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd755d5b753eb91b89b869645287685a97f8f571
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641298"
---
# <a name="symbol-object-javascript"></a>符號物件 (JavaScript)
可讓您建立唯一識別碼。  
  
## <a name="syntax"></a>語法  
  
```  
obj = Symbol(desc)  
```  
  
#### <a name="parameters"></a>參數  
 `desc`  
 選擇項。 符號的描述。  
  
## <a name="remarks"></a>備註  
 符號物件可將屬性加入現有的物件，而不會干擾現有的物件屬性、不會有非預期的可視性，也不會有其他程式碼未經協調的其他加入。  
  
 符號是基本資料類型。 您無法使用 `new` 運算子建立符號物件。  
  
 若要將符號物件加入全域符號登錄，請使用 `Symbol.for` 和 `Symbol.keyFor` 函式。 如果您將符號序列化為字串，請使用全域符號登錄，以確定特定字串在所有查閱中都會對應到正確符號。  
  
 JavaScript 包含下列可用於全域範圍中的內建符號值。  
  
|符號|說明|  
|------------|-----------------|  
|`Symbol.hasInstance`|這個方法會判斷是否建構函式物件識別為其中一個建構函式的執行個體。 這是 `instanceof` 運算子內部使用的方法。|  
|`Symbol.isConcatSpreadable`|這個屬性會傳回布林值，表示物件是否應該透過 `Array.concat` 以簡維方式呈現到其陣列項目。|  
|`Symbol.iterator`|這個方法會傳回物件的預設 Iterator。 這是 `for...of` 陳述式內部使用的方法。|  
|`Symbol.toPrimitive`|這個方法會將物件轉換成對應的基本值。 這是 `ToPrimitive` 抽象作業內部使用的方法。|  
|`Symbol.toStringTag`|這個屬性會傳回字串值，該值可用來協助您建立物件的預設字串描述。 這是內建方法 `Object.toString` 內部使用的屬性。|  
|`Symbol.unscopables`|這個屬性會傳回其屬性已從關聯物件之 `with` 環境繫結中排除的物件。|  
  
## <a name="functions"></a>函式  
 下表列出 `Symbol` 物件的函式。  
  
|||  
|-|-|  
|屬性|說明|  
|[Symbol.for](../../javascript/reference/symbol-for-function-javascript.md)|傳回指定索引鍵的符號；如果索引鍵不存在，則使用新的索引鍵建立新的符號物件。|  
|[Symbol.keyFor](../../javascript/reference/symbol-keyfor-function-javascript.md)|傳回指定符號的索引鍵。|  
|||  
  
## <a name="example"></a>範例  
  
```JavaScript  
(function() {  
  
    // module-scoped symbol  
    var key = Symbol("description");  
  
    function MyClass(privateData) {  
      this[key] = privateData;  
    }  
  
    MyClass.prototype = {  
      someFunc: function() {  
        return "data: " + this[key];  
      }  
    };  
  
    var c = new MyClass("private data")  
    console.log(key);  
    console.log(c["key"]);  
    console.log(c.someFunc());  
  
})();  
  
// Output:  
// undefined  
// undefined  
// data: private data  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]