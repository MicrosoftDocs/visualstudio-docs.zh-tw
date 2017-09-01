---
title: "建立物件 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- constructors, including properties and methods
- function constructor
- creating objects, constructor functions
- constructor functions
- prototype objects
- creating objects
- custom objects, creating
- creating objects, about creating objects
- objects, creating [JavaScript]
- creating objects, prototypes
- custom objects
- initializing objects, using constructors
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 359e1eb5df8f19774d352ace631802367b6dd8c9
ms.openlocfilehash: 0ba7962179cc2f0fcb972caee692edabee368c7d
ms.contentlocale: zh-tw
ms.lasthandoff: 08/11/2017

---
# <a name="creating-objects-javascript"></a>建立物件 (JavaScript)
您有數種方式可以使用 JavaScript 建立專屬物件。 您可以直接具現化 [Object 物件](../javascript/reference/object-object-javascript.md)，然後新增專屬屬性和方法。 或者，您可以使用物件常值標記法來定義物件。 您也可以使用建構函式來定義物件。 如需使用建構函式的詳細資訊，請參閱[使用建構函式定義類型](../javascript/advanced/using-constructors-to-define-types.md)。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何具現化物件，以及加入一些屬性。 在此情況下，只有 `pasta` 物件具有 `grain`、`width` 和 `shape` 屬性。  
  
```JavaScript  
const pasta = new Object();  
pasta.grain = "wheat";  
pasta.width = 0.5;  
pasta.shape = "round";  
pasta.getShape = function() {   
    return this.shape;   
};  
document.write(pasta.grain);  
document.write("<br/>");  
document.write(pasta.getShape());  
  
// Output:  
// wheat  
// round  
  
```  
  
## <a name="object-literals"></a>物件常值  
 當您只要想為物件建立一個執行個體時，也可以使用物件常值標記法。 下列程式碼示範如何使用物件常值標記法來具現化物件。  
  
```JavaScript  
const pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 您也可以在建構函式內使用物件常值。  
  
> [!CAUTION]
>  只有 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] 才支援下面所述的功能。  
  
 在 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] 中，您可以使用縮寫語法來建立物件常值。  
  
```JavaScript  
const key = 'a';  
const value = 5;  
  
// Older version  
const obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
const obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 下列範例示範如何使用縮寫語法以在物件常值中定義方法。  
  
```JavaScript  
// Older versions  
const obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
const obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 您也可以在 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] 中於物件常值中動態設定屬性名稱。 下列程式碼範例會使用 set 語法動態建立物件的屬性名稱。  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    value: 0,  
    set [propName](v) {  
        this.value = v;  
    }  
}  
  
console.log(obj.value);  
// Runs the setter property.  
obj.prop_42 = 777;  
console.log(obj.value);  
  
// Output:  
// 0  
// 777  
  
```  
  
 下列程式碼範例會使用 get 語法動態建立物件的屬性名稱。  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 下列程式碼範例會使用[箭號函式語法](../javascript/functions-javascript.md)將 42 附加至屬性名稱來建立計算屬性。  
  
```JavaScript  
const obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```

