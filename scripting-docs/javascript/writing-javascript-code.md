---
title: "撰寫 JavaScript 程式碼 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.htmldesigner.html
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- code, JavaScript syntax
- comments, JavaScript code
- JavaScript code
ms.assetid: dde28266-0d0f-4460-a819-f931cf0911ad
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e50bc25f818724b59d9adda51f97d76ae14de2b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="writing-javascript-code"></a>撰寫 JavaScript 程式碼
就像許多其他程式設計語言一樣，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 會組織成陳述式、包含相關陳述式集的區塊，以及註解。 您可以在陳述式內使用變數、字串、數字和運算式。  
  
## <a name="statements"></a>陳述式  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 程式是陳述式的集合。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 陳述式會以執行一個完整工作的方式來合併運算式。  
  
 陳述式包含一或多個運算式、關鍵字或運算子 (符號)。 一般而言，雖然陳述式可以寫入為兩行或多行，但會將一個陳述式寫入為一行。 此外，可以在同一行寫入兩個或多個陳述式，並以分號分隔。 一般而言，每個新行都會開始一個新的陳述式。 最好明確終止陳述式。 您可以使用分號 (;) (即 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 陳述式終止字元) 來執行這項作業。  
  
 以下是兩個 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 陳述式範例。 // 字元後面的句子是「註解」，其為程式中的說明性備註。  
  
```JavaScript  
var aBird = "Robin"; // Assign the text "Robin" to the variable aBird.  
var today = new Date(); // Assign today's date to the variable today.  
```  
  
 一組以大括弧 ({}) 括住的 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 陳述式稱為「區塊」。 群組成區塊的陳述式通常會視為單一陳述式。 這表示您可以在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 預期單一陳述式的大部分位置使用區塊。 需要注意的例外狀況包含 **for** 和 `while` 迴圈的標頭。 請注意，區塊內的單一陳述式以分號結束，但區塊本身不是。  
  
 一般而言，會在函式和條件中使用區塊。 請注意，與 C++ 和一些其他語言不同，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 不會將區塊視為新範圍；只有函式才能建立新範圍。  
  
 在下列範例中，`else` 子句包含以大括弧括住的兩個陳述式區塊。 區塊會視為單一陳述式。 此外，函式本身包含以大括弧括住的陳述式區塊。 此函式下方的陳述式是在區塊外部，因此不是函式定義的一部分。  
  
```JavaScript  
function inchestometers(inches)  
   {  
   if (inches < 0)  
      return -1;  
   else  
      {  
      var meters = inches / 39.37;  
      return meters;  
      }  
   }  
  
var inches = 12;  
var meters = inchestometers(inches);  
document.write("the value in meters is " + meters);  
```  
  
## <a name="comments"></a>註解  
 單行 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 註解的開頭是成對的正斜線 (//)。 以下是單行註解範例。  
  
```JavaScript  
var aGoodIdea = "Comment your code thoroughly."; // This is a single-line comment.  
```  
  
 多行 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 註解的開頭是一個正斜線和星號 (/*)，結尾則是反向項目 (\*/)。  
  
```JavaScript  
/*  
This is a multiline comment that explains the preceding code statement.  
  
The statement assigns a value to the aGoodIdea variable. The value,   
which is contained between the quote marks, is called a literal. A   
literal explicitly and directly contains information; it does not   
refer to the information indirectly. The quote marks are not part   
of the literal.  
*/  
```  
  
> [!NOTE]
>  如果您嘗試將一個多行註解內嵌到另一個多行註解內，則 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 會非預期的方式解譯產生的多行註解。 標示內嵌多行註解結尾的 */ 會解譯為整個多行註解的結尾。 這表示，不會註銷內嵌多行註解後面的文字；相反地，它會解譯為 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 程式碼，並產生語法錯誤。  
  
 建議您將所有註解寫入為單行註解區塊。 這可讓您稍後註銷具有多行註解的大型程式碼區段。  
  
```JavaScript  
// This is another multiline comment, written as a series of single-line comments.  
// After the statement is executed, you can refer to the content of the   
// aGoodIdea variable by using its name.  
var extendedIdea = aGoodIdea + " You never know when you'll have to figure out what it does.";  
```  
  
## <a name="assignments-and-equality"></a>指派和相等  
 等號 (=) 是用在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 陳述式中，以將值指派給變數：這是指派運算子。 = 運算子的左運算元一律是左值。 左值範例如下：  
  
-   變數、  
  
-   陣列項目、  
  
-   物件屬性。  
  
 = 運算子的右運算元一律是右值。 右值可以是任何類型的任意值 (包含運算式的值)。 以下是 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 指派陳述式範例。  
  
```JavaScript  
var anInteger = 3;  
```  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 編譯器會將此陳述式解譯為下列意義：「將值 3 指派給變數 **anInteger**」或「**anInteger** 接受值 3」。  
  
 確定您了解 = 運算子 (指派) 與 == 運算子 (相等) 之間的差異。 如果您想要比較兩個值，以找出它們是否相等，則請使用兩個等號 (==)。 [控制程式流程](../javascript/controlling-program-flow-javascript.md)會詳細討論這項作業。  
  
## <a name="expressions"></a>運算式  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 運算式值可以是任何有效的 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 類型 - 數字、字串、物件等等。 最簡單的運算式是常值。 以下是一些 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 常值運算式範例。  
  
```JavaScript  
3.9                       // numeric literal  
"Hello!"                  // string literal  
false                     // boolean literal  
null                      // literal null value  
{x:1, y:2}                // Object literal  
[1,2,3]                   // Array literal  
function(x){return x*x;}  // function literal  
```  
  
 更複雜的運算式可以包含變數、函式呼叫和其他運算式。 您可以合併運算式，以使用運算子來建立複雜運算式。 運算子範例如下：`+` (加)、`-` (減)、`*` (乘) 和 `/` (除)。  
  
 以下是一些 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 複雜運算式範例。  
  
```JavaScript  
var anExpression = 3 * (4 / 5) + 6;  
var aSecondExpression = Math.PI * radius * radius;  
var aThirdExpression = aSecondExpression + "%" + anExpression;  
var aFourthExpression = "(" + aSecondExpression + ") % (" + anExpression + ")";  
```