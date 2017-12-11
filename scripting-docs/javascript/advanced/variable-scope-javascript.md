---
title: "變數範圍 (JavaScript) | Microsoft Docs"
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
- scope, JavaScript
- variable scope [JavaScript]
- variables, scope [JavaScript]
ms.assetid: a811a9a6-856f-46e9-8be3-f2d22a0c245f
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5afc99bf3d1006b68e1d6c4c8d5bbcfc90eb776f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="variable-scope-javascript"></a>變數範圍 (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 有兩個範圍：全域和區域。 在函式定義之外宣告的變數就是全域變數，其值可在整個程式中存取和修改。 在函式定義內宣告的變數則是區域變數。 每次執行函式時，就會建立區域變數再予以摧毀，而且函式之外的所有程式碼都不能存取這個變數。 除了區塊範圍變數這種特殊案例外，JavaScript 並不支援區塊範圍 (使用一組大括弧 `{. . .}` 定義新的範圍)。  
  
## <a name="scope-in-javascript"></a>JavaScript 中的範圍  
 區域變數可以與全域變數使用相同的名稱，但是兩者是各自獨立的，變更其中一個變數的值並不會影響另一個變數。 區域變數只有在宣告該變數本身的函式內部才有意義。  
  
```JavaScript  
// Global definition of aCentaur.  
var aCentaur = "a horse with rider,";  
  
// A local aCentaur variable is declared in this function.  
function antiquities(){  
  
   var aCentaur = "A centaur is probably a mounted Scythian warrior";  
}  
  
antiquities();  
aCentaur += " as seen from a distance by a naive innocent.";  
  
document.write(aCentaur);  
  
// Output: "a horse with rider, as seen from a distance by a naive innocent."  
```  
  
 在 JavaScript 中評估變數時，就好像是在變數所在的範圍的開頭宣告變數一般。 有時，這會產生非預期的行為，如下所示。  
  
```JavaScript  
var aNumber = 100;  
tweak();  
  
function tweak(){  
  
    // This prints "undefined", because aNumber is also defined locally below.  
    document.write(aNumber);  
  
    if (false)  
    {  
        var aNumber = 123;    
    }  
}  
```  
  
 當 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 執行函式時，會先尋找所有變數宣告 (例如 `var someVariable;`)， 接著會建立變數並指派其初始值為 `undefined`。 如果宣告變數時就已經指派值 (例如 `var someVariable = "something";`)，則該變數一開始的值仍然是 `undefined`，當程式執行到包含宣告內容的那一行程式碼時，該變數才會使用所宣告的值。  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 在執行任何程式碼之前，會先處理所有變數宣告，無論宣告是否位於條件式區塊或其他建構內都一樣。 只要 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 找到所有變數，它就會執行函式中的程式碼。 如果變數是在函式內部以隱含方式宣告 (也就是如果變數是出現在指派運算式的左側，但尚未使用 `var` 來宣告)，就會將它建立為全域變數。  
  
 在 JavaScript 中，內部 (巢狀) 函式會儲存和函式本身位於相同範圍的區域變數的參考 (即使在函式傳回之後也一樣)。 這一組參考就稱為 Closure。 在下面範例中，因為外部函式的輸入參數 (`name`) 是儲存在內部函式的 Closure 中的區域變數，所以對內部函式的第二個呼叫會輸出和第一個呼叫相同的訊息 ("Hello Bill")。  
  
```JavaScript  
function send(name) {  
    // Local variable 'name' is stored in the closure  
    // for the inner function.  
    return function () {  
        sendHi(name);  
    }  
}  
  
function sendHi(msg) {  
    console.log('Hello ' + msg);  
}  
  
var func = send('Bill');  
func();  
// Output:  
// Hello Bill  
sendHi('Pete');  
// Output:  
// Hello Pete  
func();  
// Output:  
// Hello Bill  
```  
  
## <a name="block-scoped-variables"></a>區塊範圍變數  
 Internet Explorer 11 開始支援 [let](../../javascript/reference/let-statement-javascript.md) 和 [const](../../javascript/reference/const-statement-javascript.md)，這些都是區塊範圍變數。 針對這些變數，大括弧 `{. . .}` 會定義新的範圍。 當您將其中一個這種變數設為特定值時，該值只會套用至設定它時所在的範圍。  
  
 下面範例會示範 `let` 和區塊範圍的用法。  
  
> [!NOTE]
>  下面程式碼受到 Internet Explorer 11 標準模式和以後版本的支援。  
  
```JavaScript  
let x = 10;  
var y = 10;  
{  
    let x = 5;  
    var y = 5;  
    {  
        let x = 2;  
        var y = 2;  
        document.write("x: " + x + "<br/>");  
        document.write("y: " + y + "<br/>");  
        // Output:  
        // x: 2  
        // y: 2  
    }  
    document.write("x: " + x + "<br/>");  
    document.write("y: " + y + "<br/>");  
    // Output:  
    // x: 5  
    // y: 2  
}  
  
document.write("x: " + x + "<br/>");  
document.write("y: " + y + "<br/>");  
// Output:  
// x: 10  
// y: 2  
```