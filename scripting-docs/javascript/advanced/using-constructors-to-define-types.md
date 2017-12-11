---
title: "使用建構函式定義類型 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- creating objects, constructor functions
- constructor functions
- functions, constructor functions
- objects, creating [JavaScript]
- constructors, creating
ms.assetid: e869702e-4caf-4513-8dd5-fe690535f8aa
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bff42606fda27e00a537cc227a0b636e016f7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="using-constructors-to-define-types"></a>使用常數定義類型
建構函式是具現化特殊類型[物件](../../javascript/objects-and-arrays-javascript.md)的函式。 您會使用 **new** 關鍵字叫用建構函式。 以下是一些具有內建 JavaScript 物件及自訂物件的建構函式範例。  
  
## <a name="constructor-examples"></a>建構函式範例  
  
```JavaScript  
// Creates a generic object.  
var myObject = new Object();  
// Creates a Date object.  
var myBirthday = new Date(1961, 5, 10);  
// Creates a user defined object.  
var myCar = new Car();  
```  
  
 建構函式包含 **this** 關鍵字，這個關鍵字是新建立空物件的參考。 它會建立屬性並為屬性提供初始值，藉此初始化新的物件。 建構函式會傳回其所建構之物件的參考。  
  
## <a name="writing-constructors"></a>撰寫建構函式  
 若要建立物件，您可以使用 **new** 運算子搭配預先定義的建構函式 (例如 **Object()**、**Date()** 和 **Function()**)。 您也可以建立自訂建構函式來定義一組屬性和方法。 以下是自訂建構函式的範例。  
  
```JavaScript  
function Circle (xPoint, yPoint, radius) {  
    this.x = xPoint;  // The x component of the center of the circle.  
    this.y = yPoint;  // The y component of the center of the circle.  
    this.r = radius;  // The radius of the circle.  
}  
```  
  
 當您叫用 Circle 建構函式時，必須提供值做為圓形的中心點和半徑。 最後您會建立包含三個屬性的 Circle 物件。 以下是具現化 Circle 物件的方式。  
  
```JavaScript  
var aCircle = new Circle(5, 11, 99);  
```  
  
 使用自訂建構函式建立之所有物件的類型都是 `object`。 JavaScript 中只有六種類型：`object`、`function`、`string`、`number`、`boolean` 和 `undefined`。 如需詳細資訊，請參閱 [typeof 運算子](../../javascript/reference/typeof-operator-decrementjavascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用 bind 方法](../../javascript/advanced/using-the-bind-method-javascript.md)