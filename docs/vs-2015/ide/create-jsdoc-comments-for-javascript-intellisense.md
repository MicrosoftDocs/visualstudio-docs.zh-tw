---
title: 建立 JavaScript IntelliSense 的 JSDoc 註解 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 22db62a186c1f1c668a0304a9b586aca85e713c3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758505"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>建立 JavaScript IntelliSense 的 JSDoc 註解
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 中的 IntelliSense 會顯示您使用標準 JSDoc 註解加入指令碼的資訊。 您可以使用 JSDoc 註解來提供程式碼項目 (例如函式、欄位和變數) 的相關資訊。  

## <a name="jsdoc-comment-tags"></a>JSDoc 註解標記  
 下列標準 JSDoc 註解標記是由 IntelliSense 用於顯示您程式碼的相關資訊。  


|  JSDoc 標記   |                       語法                        |                                                     注意                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              @deprecated *description*              |                                   指定取代函式或方法。                                   |
| @description |             @description *description*              |                              指定函式或方法的描述。                               |
|    @param    | @param {*type*} *parameterName*<em>description</em> | 指定函式或方法中之參數的資訊。<br /><br /> TypeScript 也支援@paramTag。 |
|  @property   |          @property {*type*} *propertyName*          |   指定欄位或物件上所定義成員的資訊，包括描述。    |
|   @returns   |                  @returns {*type*}                  |           指定傳回值。<br /><br /> 對於 TypeScript，使用@returnType而不是@returns。           |
|   @summary   |               @summary *description*                |                   指定函式或方法的描述 (與相同@description)。                   |
|    @type     |                   @type {*type*}                    |                                指定常數或變數的類型。                                |
|   @typedef   |         @typedef {*type*} *customTypeName*          |                                            指定自訂類型。                                            |

### <a name="examples"></a>範例  
 下列範例示範使用@description， @param，並@returnJSDoc 標記為函式，名為`getArea`。  

```javascript  
/** @description Determines the area of a circle that has the specified radius parameter.  
 * @param {number} radius The radius of the circle.  
 * @return {number}  
 */  
function getArea(radius) {  
    var areaVal;  
    areaVal = Math.PI * radius * radius;  
    return areaVal;  
}  
```  

 在上述範例中，當您輸入 `getArea` 的左括號時，IntelliSense 會顯示描述、參數和傳回的資訊。  

 ![函式的 IntelliSense 資訊](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")  

 下列範例示範如何使用@typedef標記@property標記。  

```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  

var w = new Weather();  
```  

 下列範例示範使用@typeJSDoc 標記。 如本範例所示，在初始星號配對 (\*\*) 之後不需要單一星號 (*)。  

```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  

```  

 下列範例示範如何使用@deprecatedJSDoc 標記。  

```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```
