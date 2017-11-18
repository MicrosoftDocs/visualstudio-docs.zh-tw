---
title: "class 陳述式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: bf45ebad-4678-4062-88df-55d32b603c69
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e828ae86c3f8f585179e3b097d98b3449c3f3b45
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="class-statement-javascript"></a>class 陳述式 (JavaScript)
宣告新的類別。  
  
## <a name="syntax"></a>語法  
  
```  
class classname () [extends object] {    [constructor([arg1 [,... [,argN]]]) {        statements    }]    [[static] method([arg1 [,... [,argN]]]) {        statements    }]}  
```  
  
#### <a name="parameters"></a>參數  
 `classname`  
 必要項。 類別的名稱。  
  
 `object`  
 選擇項。 物件或類別，新的類別會從中繼承屬性和方法。  
  
 `constructor`  
 選擇項。 初始化新的類別執行個體之建構函式。  
  
 `arg1...argN`  
 選擇項。 此函式了解的引數之選擇性的逗號分隔清單。  
  
 `statements`  
 選擇項。 一或多個 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 陳述式。  
  
 `static`  
 選擇項。 指定靜態方法。  
  
 `method`  
 選擇項。 一或多個 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 執行個體或靜態方法，可在類別執行個體上呼叫。  
  
## <a name="remarks"></a>備註  
 可讓您使用以原型為基礎的繼承、建構函式、執行個體方法和靜態方法建立新物件的類別。 您可以在類別建構函式或類別方法內使用 `super` 物件，呼叫父類別或物件中相同的建構函式或方法。 (選擇性) 在類別名稱後使用 `extends` 陳述式指定類別或物件，新的類別會從中繼承方法。  
  
## <a name="example"></a>範例  
  
```JavaScript  
class Spelunking extends EXPERIENCE.Outdoor {  
  constructor(name, location) {  
    super(name, location);  
  
    this.minSkill = Spelunking.defaultSkill();  
    //...  
  }  
  update(minSkill) {  
    //...  
    super.update(minSkill);  
  }  
  static defaultSkill() {  
    return new EXPERIENCE.Level3();  
  }  
}  
```  
  
## <a name="example"></a>範例  
 您也可以建立類別之計算的屬性名稱。 下列程式碼範例會使用 `set` 語法，建立計算的屬性名稱。  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    set [propName](v) {  
        this.value = v;  
    }  
};  
  
var s = new Spelunking();  
console.log(s.value);  
s.prop_42 = 42;  
console.log(s.value);  
  
// Output:  
// undefined  
// 42  
  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用 `get` 語法，動態建立類別的屬性名稱。  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    get [propName]() {  
        return 777;  
    }  
}  
  
var s = new Spelunking();  
console.log(s.prop_42);  
  
// Output:  
// 777  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12exp](../../javascript/reference/includes/jsv12exp-md.md)]