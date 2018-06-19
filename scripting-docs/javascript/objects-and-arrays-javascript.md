---
title: 物件和陣列 (JavaScript) | Microsoft Docs
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
- arrays [JavaScript]
- arrays [JavaScript], objects
ms.assetid: f5106284-1240-4f47-8c3b-5a45e227e5e1
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6776701ba108ae0ecefc2331c2b12272e0c1be19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569338"
---
# <a name="objects-and-arrays-javascript"></a>物件和陣列 (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 物件是屬性和方法的集合。 方法是物件的函式成員。 屬性 (Property) 是一個值或一系列的值 (以陣列或物件的格式存在)，它是物件的成員。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 支援四種物件：  
  
-   內建物件，例如 `Array` 和 `String`。  
  
-   您建立的物件。  
  
-   主物件，例如 `window` 和 `document`。  
  
-   ActiveX 物件。  
  
## <a name="expando-properties-and-methods"></a>Expando 屬性和方法  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中的所有物件都支援可在執行階段加入和移除的 expando 屬性和方法。 這些屬性和方法可以有任何名稱，而且可以藉由數字來識別。 如果屬性或方法的名稱是簡單識別碼，可以將它寫在加上句號的物件名稱之後，例如下列程式碼中的 `myObj.name`、`myObj.age` 和 `myObj.getAge`：  
  
```JavaScript  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.age = 42;  
  
myObj.getAge =   
    function () {  
        return this.age;  
    };  
  
document.write(myObj.name);  
document.write("<br/>");  
document.write(myObj.age);  
document.write("<br/>");  
document.write(myObj.getAge());  
  
// Output:  
// Fred  
// 42  
// 42  
  
```  
  
 如果屬性或方法的名稱不是簡單識別碼，或者在您撰寫指令碼時為未知，您可以在方括號內使用運算式來建立屬性的索引。 在將 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 的所有 expando 屬性名稱加入物件之前，會先將屬性名稱轉換為字串。  
  
```JavaScript  
var myObj = new Object();  
  
// Add two expando properties that cannot be written in the  
// object.property syntax.  
// The first contains invalid characters (spaces), so must be  
// written inside square brackets.  
myObj["not a valid identifier"] = "This is the property value";  
  
// The second expando name is a number, so it also must  
// be placed inside square brackets  
myObj[100] = "100";  
```  
  
 如需從定義建立物件的資訊，請參閱[建立物件](../javascript/creating-objects-javascript.md)。  
  
## <a name="arrays-as-objects"></a>陣列當做物件  
 在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，由於陣列只是一種特殊的物件，因此物件和陣列幾乎是以相同的方式處理。 物件和陣列都可以有屬性和方法。  
  
 陣列有 `length` 屬性，但是物件沒有。 當您將值指派給陣列的項目，但是其索引大於陣列的長度 (例如，`myArray[100] = "hello"`) 時，`length` 屬性會自動增加至新的長度。 同樣地，如果您讓 `length` 屬性變得較小，就會刪除其索引落在陣列長度之外的所有項目。  
  
```JavaScript  
// An array with three elements  
var myArray = new Array(3);  
  
// Add some data  
myArray[0] = "Hello";  
myArray[1] = 42;  
myArray[2] = new Date(2000, 1, 1);  
  
document.write("original length is: " + myArray.length);  
document.write("<br/>");  
// Add some expando properties  
myArray.expando = "JavaScript!";  
myArray["another Expando"] = "Windows";  
  
// This will still display 3, since the two expando properties  
// don't affect the length.  
document.write("new length is : " + myArray.length);  
  
// Output:  
// original length is: 3  
// new length is : 3  
  
```  
  
 陣列提供逐一查看和管理成員的方法。 下面範例會示範如何取得儲存於陣列之物件的屬性。  
  
```JavaScript  
var myArray = new Array(3);  
  
// Add some data  
for(var i = 1; i <= 3; i++) {  
    myArray[i] = new Date(2000 + i, 1, 1);  
}  
  
myArray.forEach(function (item) {  
    document.write(item.getFullYear());  
});  
  
// Output:  
// 2001  
// 2002  
// 2003  
```  
  
## <a name="multi-dimensional-arrays"></a>多維陣列  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 不直接支援多維陣列，但是您可以將陣列儲存在另一個陣列的項目中，以獲得多維陣列的行為  (您可以將任何類型的資料儲存在陣列元素中，包括其他陣列)。例如，下面程式碼會建立最大數字為 5 的乘法表。  
  
```JavaScript  
// The size of the table.  
var iMaxNum = 5;  
// Loop counters.  
var i, j;  
  
// Set the length of the array to iMaxNum + 1.   
// The first array index is zero, not 1.  
var MultiplicationTable = new Array(iMaxNum + 1);  
  
// Loop for each major number (each row in the table)  
for (i = 1; i <= iMaxNum; i++)  
{  
    // Create the columns in the table  
    MultiplicationTable[i] = new Array(iMaxNum + 1);  
  
    // Fill the row with the results of the multiplication  
    for (j = 1; j <= iMaxNum; j++)  
    {  
        MultiplicationTable[i][j] = i * j;  
    }  
}  
  
document.write(MultiplicationTable[3][4]);  
document.write("<br/>");   
document.write(MultiplicationTable[5][2]);  
document.write("<br/>");  
document.write(MultiplicationTable[1][4]);  
  
// Output:  
// 12  
// 10  
// 4  
  
```