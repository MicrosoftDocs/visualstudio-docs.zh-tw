---
title: 變數 (JavaScript) | Microsoft Docs
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
- coercion
- case sensitivity, JavaScript variable name
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1d09f634bd4901e4015766bf55f272926a0a31c
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2018
ms.locfileid: "30307265"
---
# <a name="variables-javascript"></a>變數 (JavaScript)
在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，變數包含值，例如 "hello" 或 5。 當您使用變數時，您要參考它代表的資料，例如 `NumberOfDaysLeft = EndDate - TodaysDate`。  
  
 您使用變數來儲存、擷取及操控程式碼中出現的值。 嘗試為變數提供有意義的名稱，以便其他人了解程式碼的功能。  
  
## <a name="declaring-variables"></a>宣告變數  
 變數第一次出現在指令碼中就是它的宣告。 第一次提及的變數會設定在記憶體中，因此您可以稍後在指令碼中參考它。 您應該在使用前宣告變數。 您使用 `var` 關鍵字執行此作業。  
  
```JavaScript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 如果不在 `var` 陳述式中初始化您的變數，它會自動採用值 `undefined`。  
  
## <a name="naming-variables"></a>命名變數  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 是區分大小寫的語言。 這表示 **myCounter** 的變數名稱不同於變數名稱 **MYCounter**。 變數名稱可以是任何長度。 建立合法變數名稱的規則如下：  
  
-   第一個字元必須是 ASCII 字母 (大寫或小寫)、符合 Unicode 準變數命名慣例的字母，或底線 (_) 字元。 請注意，數字不能用作第一個字元。  
  
-   後續的字元必須是字母、數字或底線 (_)。  
  
-   變數名稱絕不能是[保留字](../javascript/reference/javascript-reserved-words.md)。  
  
 以下是一些有效變數名稱的範例：  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 以下是一些無效變數名稱的範例：  
  
```JavaScript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 當您想要宣告並初始化變數，但不想指定任何特定值時，請給它指派值 `null`。 以下是一個範例。  
  
```JavaScript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 如果宣告變數但不指派值給它，它會有值 `undefined`。 以下是一個範例。  
  
```JavaScript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 `null` 值的行為如同數字 0，而 `undefined` 的行為如同特殊值 `NaN` (不是數字)。 如果比較 `null` 值和 `undefined` 值，它們是相等的。  
  
 您可以宣告變數，但宣告中不使用 `var` 關鍵字，並指派值給它。 這是隱含宣告。  
  
```JavaScript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 您無法使用從未宣告過的變數。  
  
```JavaScript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## <a name="coercion"></a>強制型轉  
 相對於 C++ 等強型別語言，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 是鬆散型的語言。 這表示 JavaScript 變數沒有預先決定的類型。 而是變數的類型即是其值的類型。 此行為可讓您將值當成不同的類型。  
  
 在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，您可以對不同類型的值執行作業，卻不會造成例外狀況。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]解譯器會將其中一個資料類型隱含轉換，或「強制轉型」成另一個資料類型，然後執行作業。 強制轉型字串、數字和布林值的規則如下：  
  
-   如果新增數字和字串，數字會強制轉型為字串。  
  
-   如果新增布林值和字串，布林值會強制轉型為字串。  
  
-   如果新增數字和布林值，布林值會強制轉型為數字。  
  
 在下例中，將數字新增到字串會得到字串。  
  
```JavaScript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 字串會自動轉換為相等的數字以進行比較。 若要明確地將字串轉換成整數，請使用 [parseInt 函式](../javascript/reference/parseint-function-javascript.md)。 若要明確地將字串轉換成數字，請使用 [parseFloat 函式](../javascript/reference/parsefloat-function-javascript.md)。