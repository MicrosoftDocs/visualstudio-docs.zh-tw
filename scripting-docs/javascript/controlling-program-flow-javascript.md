---
title: 控制程式流程 (JavaScript) | Microsoft Docs
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
helpviewer_keywords:
- Boolean values, program flow
- continue statement
- break statement
- control flow, about control flow
ms.assetid: 4ef58c82-e5d6-4b09-9458-cf0aa3b39bf5
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20c256d26c6991067d7c25c0c835eda6e5e5aac6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569708"
---
# <a name="controlling-program-flow-javascript"></a>控制程式流程 (JavaScript)
通常，在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 指令碼中的陳述式會以其撰寫的順序逐一執行。 這稱為循序執行，也是程式流程的預設方向。  
  
 除了循序執行外，有一種替代方案可以轉換程式流程，以執行指令碼的其他部分。 也就是說，不依原本順序執行下一個陳述式，而是執行其他陳述式。  
  
 您必須透過邏輯方法來轉換控制，才能讓指令碼發揮最大效用。 是否要轉換程式控制是取決於一個決定，其結果就是真實陳述式 (傳回布林值 **true** 或 **false**)。 您要建立運算式再測試它的結果是否為 true。 有兩種主要的程式結構可以達成這個目的。  
  
 第一種是選取結構。 用來指定程式流程的替代過程，在程式中建立一個分歧點 (像叉路一樣)。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中有四種可用的選取結構。  
  
-   單一選取結構 (**if**)、  
  
-   雙重選取結構 (**if/else**)、  
  
-   內嵌三元運算子 `?:`  
  
-   多重選取結構 (`switch`)  
  
 第二種程式控制結構為重複結構， 用來指定某些條件只要成立就要重複動作。 在滿足了控制陳述式的條件時 (通常是在重複過特定次數後)，控制會被傳遞到重複結構之外的下一個陳述式中。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中有四種可用的重複結構。  
  
-   在迴圈頂端測試運算式 (`while`)  
  
-   在迴圈底部測試運算式 (**do/while**)、  
  
-   針對每個物件的屬性進行運算 (**for/in**)。  
  
-   計算器受控制重複次數 (**for**)。  
  
 藉由以巢狀和堆疊方式撰寫選取和重複控制結構，您就能建立相當複雜的指令碼。  
  
 第三種形式的結構化程式流程是由例外狀況處理功能提供，本文件並未涵蓋此功能。  
  
## <a name="using-conditional-statements"></a>使用條件陳述式  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 支援 **if** 和 [if...else](../javascript/reference/if-dot-dot-dot-else-statement-javascript.md) 條件陳述式。 **if** 陳述式會測試條件，如果條件滿足測試，就會執行相關的 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 程式碼。 在 `if...else` 陳述式中，如果條件未通過測試，則會執行不同的程式碼。 最簡單的 **if** 陳述式格式可以被寫成一行，但是多行的 **if** 和 `if...else` 陳述式更為普遍。  
  
 下列範例說明您可以使用的 **if** 和 `if...else` 陳述式語法。 第一個範例顯示最簡單的一種布林值測試。 如果 (只限下列情況) 括弧之間的項目判定為 (或可以強制轉型為) **true** 時，則會執行 **if** 之後的陳述式或陳述式區塊。  
  
```JavaScript  
function GetReaction(newShip, color, texture, dayOfWeek)  
{  
   // The test succeeds if the newShip Boolean value is true.  
   if (newShip)  
   {  
      return "Champagne Bottle";  
   }  
  
   // The test succeeds if both conditions are true.  
   if (color == "deep yellow" && texture == "large and small wrinkles")  
   {  
      return "Is it a crenshaw melon?";  
   }  
  
   // The test succeeds if either condition is true.  
   if ((dayOfWeek == "Saturday") || (dayOfWeek == "Sunday"))  
   {  
      return "I'm off to the beach!";  
   }  
   else  
   {  
      return "I'm going to work.";  
   }  
}  
  
var reaction = GetReaction(false, "deep yellow", "smooth", "Sunday");  
document.write(reaction);  
  
// Output: I'm off to the beach!  
```  
  
## <a name="conditional-operator"></a>條件運算子  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 也支援隱含的條件形式。 它會在要測試的條件後面使用問號，而不是在條件前面放置 **if**。 它還會指定兩個替代項目，一個在條件符合時使用，另一個在不符合時使用。 您必須以冒號分隔這些替代文字。  
  
```JavaScript  
var AMorPM = (theHour >= 12) ? "PM" : "AM";  
```  
  
 如果要同時測試幾項條件，而且您知道哪一項條件可能比其他條件更易通過或失敗，就可以使用一種名為「最少運算評估」(Short Circuit Evaluation) 的功能，加速指令碼的執行。 當 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 評估邏輯運算式時，會依取得結果所需，決定其要評估多少子運算式。  
  
 例如 ((x == 123) && (y == 6)) 這類 AND 運算式，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 會先檢查 x 是否為 123。 如果不是，即使 y 等於 6，整個運算式的結果也不會是 true， 因此，永不進行對 y 的測試，而且 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 會傳回 **false** 值。  
  
 同樣地，如果多項條件中只有一項必須是 **true** (使用 &#124;&#124; 運算子)，那麼只要有任何一個條件符合測試，測試就會停止。 如果要測試的條件牽涉到執行函式呼叫或其他複雜的運算式，這種方式就十分有效。 了解這點之後，在您撰寫 Or 運算式時，請將最有可能為 **true** 的條件放在最前面。 撰寫 And 運算式時，請將最有可能為 **false** 的條件放在最前面。  
  
 下面範例可看出以這種方式設計指令碼的優點，如果 **runfirst()** 傳回 0，**runsecond()** 就不會執行。  
  
```JavaScript  
if ((runfirst() == 0) || (runsecond() == 0)) {  
    // some code  
}  
```  
  
## <a name="using-loops"></a>使用迴圈  
 您可以使用數種方式重複執行陳述式或陳述式區塊。 一般而言，重複執行稱為「迴圈處理」或「反覆項目」。 重複項目只是單一迴圈的執行， 它通常是由變數的測試來控制，其值會在每次執行迴圈時變更。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 支援四種迴圈：[for](../javascript/reference/for-statement-javascript.md) 迴圈、[for...in](../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) 迴圈、[while](../javascript/reference/while-statement-javascript.md) 迴圈、[do...while](../javascript/reference/do-dot-dot-dot-while-statement-javascript.md) 迴圈。  
  
## <a name="using-for-loops"></a>使用 for 迴圈  
 **for** 陳述式會指定計數器變數、測試條件和更新計數器的動作。 在每次迴圈重複前，會先測試條件。 如果測試成功，會執行迴圈內部的程式碼。 如果測試不成功，就不會執行迴圈內部的程式碼，而且程式會立即執行緊接在迴圈之後的第一行程式碼。 迴圈執行過後，會下個重複項目開始之前更新計數器變數。  
  
 如果迴圈處理的條件從來都沒有符合過，就永遠不會執行迴圈。 如果一直符合測試條件，便會造成無限迴圈。 雖然在某些情況下可能希望得到前面的結果，但極少人會希望得到後面的結果，所以在撰寫迴圈條件時要十分謹慎。  
  
```JavaScript  
// The update expression ("icount++" in the following examples)  
// is executed at the end of the loop, after the block of  
// statements that forms the body of the loop is executed, and  
// before the condition is tested.  
  
// Set a limit of 10 on the loop.  
var howFar = 10;  
  
// Create an array called sum with 10 members, 0 through 9.  
var sum = new Array(howFar);  
sum[0] = 0;  
  
// Iterate from 0 through 9.  
var theSum = 0;  
for(var icount = 0; icount < howFar; icount++)  
{  
   theSum += icount;  
   sum[icount] = theSum;  
}  
  
// This code is not executed at all, because icount is not greater than howFar.  
var newSum = 0;  
for(var icount = 0; icount > howFar; icount++)  
{  
   newSum += icount;  
}  
  
// This is an infinite loop.  
var sum = 0;  
for(var icount = 0; icount >= 0; icount++)  
{  
   sum += icount;  
}  
```  
  
## <a name="using-forin-loops"></a>使用 for...in 迴圈  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 提供特殊類型的迴圈，用來逐步執行[物件](../javascript/objects-and-arrays-javascript.md)的所有使用者定義屬性或陣列的所有項目。 `for...in` 迴圈中的迴圈計數器是字串而非數字， 其中包含目前屬性的名稱，或目前陣列元素的索引。  
  
```JavaScript  
// Create an object with some properties  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 1234";  
  
// Enumerate (loop through)_all the properties in the object  
for (var prop in myObject)  
{  
    // This displays "The property 'name' is James", etc.  
    document.write("The property '" + prop + "' is " + myObject[prop]);  
    // New line.  
    document.write("<br />");    
}  
```  
  
 雖然 `for...in` 迴圈類似 VBScript 的 `For Each...Next` 迴圈，但是運作方式卻不同。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]**for...in 迴圈**會逐一查看 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 物件的屬性。 VBScript 的 **For Each...Next** 迴圈會逐一查看集合中的項目。 若要在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中使用迴圈處理集合，您必須使用[列舉程式物件](../javascript/reference/enumerator-object-javascript.md)物件或集合物件的 `forEach` 方法 (如果有的話)。 雖然某些物件 (例如 Internet Explorer 中的物件) 同時支援 VBScript **For Each...Next** 迴圈和 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]**for...in** 迴圈，但是大部分物件並非如此。  
  
## <a name="using-while-loops"></a>使用 while 迴圈  
 `while` 迴圈類似 **for** 迴圈。 差別在於 `while` 迴圈沒有內建計數器變數，也沒有更新運算式。 如果您想要控制陳述式或陳述式區塊內容的重複執行，但需要比「執行這個程式碼 n 次」更複雜的規則，請使用 `while` 迴圈。 下面範例會使用 Internet Explorer 物件模型和 `while` 迴圈，詢問使用者簡單的問題。  
  
```JavaScript  
var x = 0;  
while ((x != 5) && (x != null))  
{  
    x = window.prompt("What is my favorite number?", x);  
}  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
> [!NOTE]
>  因為 `while` 迴圈沒有明確的內建計數器變數，所以它們比其他類型的迴圈更容易形成無限的迴圈處理。 再者，由於不一定能輕易地找出更新迴圈條件的位置及時間，所以撰寫條件永遠不會被更新的 `while` 迴圈頗為容易。 基於這個原因，在設計 `while` 迴圈時應該要小心。  
  
 如前所述，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中也有類似 while 迴圈的 **do...while** 迴圈，差異在於因為後者是在迴圈結束 (而不是開頭) 時測試條件，所以一定會執行迴圈內容一次。 例如，上面的迴圈可以重新撰寫如下：  
  
```JavaScript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
} while ((x != 5) && (x != null));  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
## <a name="using-break-and-continue-statements"></a>使用 break 和 continue 陳述式  
 在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，如果符合某項條件，[break](../javascript/reference/break-statement-javascript.md) 陳述式會用來停止執行迴圈  (請注意，**break** 也用來結束 `switch` 區塊)。 如果迴圈是 **for** 或 `for...in`，則在更新計數器變數時，可以使用 [continue](../javascript/reference/continue-statement-javascript.md) 陳述式立即跳到下一個重複項目，以略過程式碼區塊其他的部分。  
  
 下面範例會以先前的範例為基礎，使用 **break** 和 **continue** 陳述式控制迴圈。  
  
```JavaScript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
  
    // Did the user cancel? If so, break out of the loop  
    if (x == null)  
        break;  
  
    // Did they enter a number?  
    // If so, no need to ask them to enter a number.  
    if (Number(x) == x)  
        continue;  
  
    // Ask user to only enter in numbers  
    window.alert("Please only enter in numbers!");  
  
} while (x != 5)  
  
if (x != 5)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```