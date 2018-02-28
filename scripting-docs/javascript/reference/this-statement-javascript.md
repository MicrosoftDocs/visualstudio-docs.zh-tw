---
title: "這個陳述式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- this_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- this statement
- constructors, referring to current object
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4afed1bd978d1985c151efa77873c93e699f0b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="this-statement-javascript"></a>this 陳述式 (JavaScript)
參考目前的物件。  
  
## <a name="syntax"></a>語法  
  
```  
this.property  
```  
  
## <a name="remarks"></a>備註  
 必要的 `property` 引數是目前物件的其中一個屬性  
  
 `this` 關鍵字可以在物件建構函式中用來參考目前的物件。  
  
## <a name="example"></a>範例  
 在下列範例中，**這**指的是新建立的 Car 物件，並將值指派給三個屬性：  
  
```JavaScript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 **這**關鍵字通常是指**視窗**物件，如果在任何其他物件的範圍之外使用。 不過，在事件處理常式內部，`this` 會參考引發事件的 DOM 項目。  
  
 在下列程式碼 (適用於 Internet Explorer 9 (含) 以後版本) 中，事件處理常式會列印 ID 為 "clicker" 之按鈕的字串版本。  
  
```JavaScript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ew 運算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [使用 bind 方法](../../javascript/advanced/using-the-bind-method-javascript.md)