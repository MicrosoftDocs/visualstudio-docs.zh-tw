---
title: 集合 (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 23c26185-6a7b-4b69-9d22-63e1841b4905
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fab554f50f6d2fcdac92c562333e625dc0eb32f6
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/12/2018
ms.locfileid: "27783048"
---
# <a name="collections-javascript"></a>集合 (JavaScript)
您可以使用集合物件 [Map](../../javascript/reference/map-object-javascript.md)、[Set](../../javascript/reference/set-object-javascript.md) 和 [WeakMap](../../javascript/reference/weakmap-object-javascript.md) 來儲存值和物件。 這些物件可提供簡便的方法讓您使用索引鍵或值 (而非使用索引) 來加入和擷取成員。 若要使用索引來存取集合的成員，請使用 `Array` 物件。 如需詳細資訊，請參閱[使用陣列](../../javascript/advanced/using-arrays-javascript.md)。  
  
> [!CAUTION]
>  Internet Explorer 11 之前的瀏覽器版本不支援 `Map`、`Set` 和 `WeakMap`。 如需支援版本的詳細資訊，請參閱[版本資訊](../../javascript/reference/javascript-version-information.md)。  
  
## <a name="using-collections"></a>使用集合  
 `Map` 和 `WeakMap` 物件可儲存索引鍵/值組，並可讓您使用索引鍵來加入、擷取及移除成員。 此索引鍵和值可以屬於任何類型。 `Set` 物件可儲存任何類型的值。  
  
 `Map` 和 `Set` 物件可讓您使用 `forEach` 方法來列舉集合成員，以及讓您使用 `size` 方法來檢查集合的大小。 相反地，`WeakMap` 物件並不具有列舉功能。 這個集合是以弱式的方式保存索引鍵參考。 如果您希望記憶體回收行程能夠判斷應用程式是否必須在記憶體內部保留集合的每個成員，請使用 `WeakMap`。 例如，在快取的物件非常大的快取案例中，因為您不會想要在記憶體內部保存不必要的物件，這可能就會很有用。 在某些情況下，您可以使用此物件來防止發生記憶體遺漏。  
  
 下面範例會示範如何使用 `Map` 物件。 在這個範例中，是使用 `get` 和 `forEach` 來存取成員。 `forEach` 中的回呼函式可以採用多達三個參數，以提供目前集合項目的值、目前項目的索引鍵，和集合物件本身。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
document.write(m.get(2));  
document.write("<br />");  
  
m.forEach(function (value, key, mapObj) {  
    document.write(value.toString() + "<br />");  
});  
  
// Output:  
// red  
  
// black  
// red  
// 2  
// 3  
  
```  
  
 `WeakMap` 的用法與 `Map` 類似，不過您只能使用 `get` 來擷取成員。 如需範例，請參閱 [WeakMap](../../javascript/reference/weakmap-object-javascript.md) 物件。  
  
 下面範例會示範如何使用 `Set` 物件。 在此範例中，回呼函式只採用一個參數，就是目前集合項目的值。  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (value) {  
    document.write(value.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="see-also"></a>請參閱  
 [進階 JavaScript](../../javascript/advanced/advanced-javascript.md)