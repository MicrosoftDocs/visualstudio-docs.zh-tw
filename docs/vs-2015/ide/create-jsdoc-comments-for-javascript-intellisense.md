---
title: 建立 JavaScript IntelliSense 的 JSDoc 註解 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e24338a75dd631cee86ea8ac81e774e81732bba5
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2018
ms.locfileid: "48878988"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>建立 JavaScript IntelliSense 的 JSDoc 註解
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[Visual Studio 2017 文件](/visualstudio/)。  
  
Visual Studio 中的 IntelliSense 會顯示您使用標準 JSDoc 註解加入指令碼的資訊。 您可以使用 JSDoc 註解來提供程式碼項目 (例如函式、欄位和變數) 的相關資訊。  
  
## <a name="jsdoc-comment-tags"></a>JSDoc 註解標記  
 下列標準 JSDoc 註解標記是由 IntelliSense 用於顯示您程式碼的相關資訊。  
  
|JSDoc 標記|語法|注意|  
|---------------|------------|-----------|  
|@deprecated|@deprecated *描述*|指定取代函式或方法。|  
|@description|@description *描述*|指定函式或方法的描述。|  
|@param|@param {*型別*} *parameterName * * 描述*|指定函式或方法中之參數的資訊。<br /><br /> TypeScript 也支援@paramTag。|  
|@property|@property {*型別*} *propertyName*|指定欄位或物件上所定義成員的資訊，包括描述。|  
|@returns|@returns {*型別*}|指定傳回值。<br /><br /> 對於 TypeScript，使用@returnType而不是@returns。|  
|@summary|@summary *描述*|指定函式或方法的描述 (與相同@description)。|  
|@type|@type {*型別*}|指定常數或變數的類型。|  
|@typedef|@typedef {*型別*}*自訂類型名稱*|指定自訂類型。|  
  
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
  
 下列範例示範使用@typeJSDoc 標記。 此範例所示，單一星號 （*），請遵循在初始星號配對 (\*\*) 不需要。  
  
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



