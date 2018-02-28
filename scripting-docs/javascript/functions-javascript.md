---
title: "函式 (JavaScript) | Microsoft Docs"
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
- intrinsic JavaScript functions
ms.assetid: e2a72b5a-3edd-43d8-95e8-91721b38c1c1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7275985d07f9f564dac98ba39e5ec31618dcaac4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="functions-javascript"></a>函式 (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 函式會執行動作。它們也可以傳回值。 有時候這些是計算或比較的結果。 函式也稱為「全域方法」。  
  
 函式將數個作業結合在一個名稱之下。 這可讓您簡化程式碼。 您可以寫出一組陳述式、命名，然後呼叫它來執行整個集合，並將它需要的任何資訊傳遞給它。  
  
 將資訊傳遞給函式的方式是將資訊括在函式名稱後面的括號中。 傳遞至函式的資訊片段稱為引數或參數。 某些函式完全不接受任何引數，其他函式則接受一或多個引數。 在有些函式中，引數數目取決於您如何使用該函式。  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 支援兩種函式：內建在語言中的函式，以及您自行建立的函式。  
  
## <a name="built-in-functions"></a>內建函式  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 語言包括數個內建函式。 有些可讓您處理運算式和特殊字元，其他的則將字串轉換為數值。  
  
 如需這些內建函式的資訊，請參閱 [JavaScript 方法](../javascript/reference/javascript-methods.md)。  
  
## <a name="creating-your-own-functions"></a>建立您自己的函式  
 您可以建立自己的函式，並在需要時使用它們。 函式定義包含一個函式陳述式和一個區塊的 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 陳述式。  
  
 下列範例中的 **checkTriplet** 函式會接受三角形側邊的長度作為其引數。 它會從這些引數計算三角形是否為直角三角形，只要檢查三個數字是否形成畢氏三元數 (直角三角形斜邊的長度平方等於其他兩個邊的長度平方總和)。 CheckTriplet 函式呼叫其他兩個函式的其中一個來進行實際測試。  
  
 請注意，在浮點版本的測試中使用了很小的數字 ("epsilon") 做為測試變數。 由於浮點計算中的不確定性和捨入錯誤，直接測試三個數字是否構成畢氏三元數並不實用，除非討論中的三個值全都已知為整數。 由於直接測試較精確，因此此範例中的程式碼會判斷它適合，且如果適合便會使用它。  
  
```JavaScript  
var epsilon = 0.00000000001; // Some very small number to test against.  
  
// The test function for integers.  
function integerCheck(a, b, c)   
{  
   // The test itself.  
   if ( (a*a) == ((b*b) + (c*c)) )     
      return true;  
  
   return false;  
} // End of the integer checking function.  
  
// The test function for floating-point numbers.  
function floatCheck(a, b, c)     
{  
   // Make the test number.  
   var delta = ((a*a) - ((b*b) + (c*c)))  
  
   // The test requires the absolute value  
   delta = Math.abs(delta);  
  
   // If the difference is less than epsilon, then it's pretty close.  
   if (delta < epsilon)     
      return true;  
  
   return false;  
} // End of the floating-poing check function.  
  
// The triplet checker.   
function checkTriplet(a, b, c)  
{   
   // Create a temporary variable for swapping values  
   var d = 0;   
  
   // First, move the longest side to position "a".  
  
   // Swap a and b if necessary  
   if (b > a)  
   {  
      d = a;  
      a = b;  
      b = d;  
   }  
  
   // Swap a and c if necessary  
   if (c > a)  
   {  
      d = a;  
      a = c;  
      c = d;  
   }  
  
   // Test all 3 values. Are they integers?  
   if (((a % 1) == 0) && ((b % 1) == 0) && ((c % 1) == 0))  
   {   
      // If so, use the precise check.  
      return integerCheck(a, b, c);   
   }  
   else  
   {  
      // If not, get as close as is reasonably possible.  
      return floatCheck(a, b, c);   
   }  
} // End of the triplet check function.  
  
// The next three statements assign sample values for testing purposes.  
var sideA = 5;  
var sideB = 5;  
var sideC = Math.sqrt(50.001);  
  
// Call the function. After the call, 'result' contains the result.  
var result = checkTriplet(sideA, sideB, sideC);  
```  
  
<a name="Arrow"></a>   
## <a name="arrow-functions"></a>箭號函式  
 箭號函式的語法 `=>`提供指定匿名函式的簡略方法。 以下是箭號函式語法。  
  
```JavaScript  
([arg] [, arg]) => {  
    statements  
}  
```  
  
 箭號左邊的值，可能以括號括住，指定傳遞給函式的引數。 函式的單一引數不需要括號。 如果不會傳入引數，則需要括號。 箭號右邊的函式定義可以是運算式，例如 `v + 1`，或以大括號 ({}) 括住的陳述式區塊。  
  
> [!IMPORTANT]
>  只有在 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] 支援箭號函式語法。  
  
 您不能使用 `new` 運算子搭配箭號函式。  
  
 下列程式碼範例顯示使用箭號函式，並搭配運算式做為函式定義。 在第一個範例中，v 做為引數傳遞給運算式。 在第二個範例中，v 和 i 做為引數傳遞給運算式。  
  
```  
var evens = [2, 4, 6, 8];  
  
// Using standard syntax.  
var odds = evens.map(function(v) { return v + 1; });  
  
// Using arrow function syntax.  
// Add one to each value to produce output.  
var odds = evens.map(v => v + 1);  
  
// The following line of code adds the index value to the passed  
// in value to produce output.  
// Note: the second argument to the callback function in the map   
// method is the index value (i).  
var nums = evens.map((v, i) => v + i);  
  
console.log(odds);  
console.log(nums);  
  
// Output:  
// [object Array] [3, 5, 7, 9]  
// [object Array] [2, 5, 8, 11]  
```  
  
 下列程式碼範例顯示使用箭號函式，並搭配陳述式區塊。  
  
```JavaScript  
var fives = new Array();  
  
// Statement block, re-using nums array from previous example.  
// Note: The first argument to the callback function in forEach  
// is the value of the array element (v).  
nums.forEach(v => {  
  if (v % 5 === 0)  
    fives.push(v);  
});  
  
console.log(fives);  
  
// Output:  
// [object Array] [5]  
```  
  
 不同於標準函式，箭號函式與周圍的程式碼會共用相同的語彙 `this` 物件，這可用來消除因應措施的需要，例如 `var self = this;`。  
  
 下列範例顯示箭號函式中 `this` 物件的值與周圍的程式碼相同 (它仍然是指 `bob` 變數。  
  
```JavaScript  
var bob = {  
  _name: "Bob",  
  _friends: ["Pete", "Joe", "Larry"],  
  printFriends() {  
    this._friends.forEach(f =>  
      console.log(this._name + " knows " + f));  
  }  
}  
  
// Output:  
// Bob knows Pete  
// Bob knows Joe  
// Bob knows Larry  
```  
  
 箭號函式也會與周圍的程式碼共用相同語彙 `arguments` 物件 (就像 `this` 物件)。  
  
<a name="Default"></a>   
## <a name="default-parameters"></a>預設參數  
 您可以藉由指派一個初始值，在函式中指定參數的預設值。 預設值可能是常值或運算式。  
  
> [!IMPORTANT]
>  只有在 [!INCLUDE[jsv12textExp](../javascript/includes/jsv12textexp-md.md)] 才支援預設參數。  
  
 在下列範例中，y 的預設值是 10，而 z 的預設值是 20。 函式會使用 10 做為 y 的值，除非呼叫端傳遞相異值 (或未定義) 做為第二個引數。 函式會使用 20 做為 z 的值，除非呼叫端傳遞相異值 (或未定義) 做為第三個引數。  
  
```JavaScript  
var val = 20;  
  
function f(x, y=10, z=val) {  
  return x + y + z;  
}  
  
console.log(f(3));  
console.log(f(3, 3));  
console.log(f(3, 3, 3));  
  
// Output:  
// 33  
// 26  
// 9  
```  
  
<a name="Rest"></a>   
## <a name="rest-parameters"></a>剩餘參數  
 剩餘參數 (由 spread 運算子 `...` 所指定) 可讓您將函式呼叫中連續的引數轉為陣列。  
  
 剩餘參數不需要 `arguments` 物件。 剩餘參數與 `arguments` 物件有數點不同，例如：  
  
-   剩餘參數是實際的陣列執行個體，因此支援可以在陣列上執行的作業。  
  
-   剩餘參數只包含未當做獨立的 (具名) 引數傳入的連續引數 (相反地，`arguments` 物件包含傳入函式的所有引數)。  
  
> [!IMPORTANT]
>  只有在 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] 才支援剩餘參數和 spread 運算子。  
  
 在下列程式碼範例中，"hello"和 true 會當做陣列值傳入，並儲存在 y 參數。 剩餘參數必須是函式的最後一個參數。  
  
```JavaScript  
function f(x, ...y) {  
  // y is an array.  
  return x * y.length;  
}  
  
console.log(f(3, "hello", true));  
  
// Output:  
// 6  
  
```  
  
 如需 spread 運算子的其他用法，請參閱 [Spread 運算子](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md)。  
  
## <a name="see-also"></a>請參閱  
 [JavaScript 語言參考](../javascript/javascript-language-reference.md)