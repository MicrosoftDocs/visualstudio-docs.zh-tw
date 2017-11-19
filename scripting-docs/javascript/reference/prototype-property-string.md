---
title: "prototype 屬性 （字串） |Microsoft 文件"
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
ms.assetid: 437ce478-9c45-45f7-8952-bd71856cfcd8
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df8c6abbd64fce9172d805c2e22dee51f4fbbee4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-string"></a>prototype 屬性 (字串)
傳回的字串類別的原型參考。  
  
## <a name="syntax"></a>語法  
  
```  
  
string.prototype  
```  
  
## <a name="remarks"></a>備註  
 `string`引數是字串的名稱。  
  
 `prototype` 屬性可用來提供某類別物件的一組基本功能。 物件的新執行個體會「繼承」指派給該物件之原型的行為。  
  
 例如，若要將方法加入`String`物件可傳回字串的最後一個項目的值，宣告函式，將它加入至`String.prototype`，然後使用它。  
  
```JavaScript  
function string_last( ){  
    return this.charAt(this.length - 1);  
}  
String.prototype.last = string_last;  
var myString = new String("every good boy does fine");  
document.write(myString.last());  
  
// Output:  
// e  
```  
  
 所有內建[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件具有`prototype`是唯讀的屬性。 屬性和方法可能會加入原型，但該物件可能未獲指派不同的原型。 不過，使用者定義的物件可能會指派新的原型。  
  
 語言參考中的每個內建函式物件的方法和屬性清單會指出哪些屬於物件的原型，但並不是。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]