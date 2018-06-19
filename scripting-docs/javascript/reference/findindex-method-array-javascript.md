---
title: findIndex 方法 （陣列） (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 3a200cf0-db67-4c7b-89f8-5e9f5dc1a926
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c8da475b776e1c04e4fe5bfc7062318cfec952c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636578"
---
# <a name="findindex-method-array-javascript"></a>findIndex 方法 (陣列) (JavaScript)
傳回第一個陣列項目的索引值，而此陣列項目符合回呼函式中所指定的測試準則。  
  
## <a name="syntax"></a>語法  
  
```  
arrayObj.findIndex(callbackfn [, thisArg]);  
```  
  
#### <a name="parameters"></a>參數  
 `arrayObj`  
 必要項。 陣列物件。  
  
 `callbackfn`  
 必要項。 測試陣列中每一個項目的回呼函式。  
  
 `thisArg`  
 選擇項。 在回呼函式中，指定 `this` 物件。 如果未指定，則未定義 `this` 物件。  
  
## <a name="remarks"></a>備註  
 除非項目傳回 `true`，否則 `findIndex` 會針對陣列中的每一個項目，依遞增順序呼叫一次回呼函式。 項目傳回 true 時，`findIndex` 會立即傳回可傳回 true 之項目的索引值。 如果陣列中沒有項目傳回 true，則 `findIndex` 會傳回 -1。  
  
 `findIndex` 不會變更 array 物件。  
  
## <a name="callback-function-syntax"></a>回呼函式語法  
 回呼函式的語法如下：  
  
 `function callbackfn(value, index, thisArg)`  
  
 您最多可以使用三個參數宣告回呼函式。  
  
 回呼函式參數如下所示。  
  
|回呼引數|定義|  
|-----------------------|----------------|  
|`value`|陣列元素的值。|  
|`index`|陣列元素的數值索引。|  
|`arrayObj`|要周遊的 array 物件。|  
  
## <a name="example"></a>範例  
 在下列範例中，回呼函式會測試陣列中的每個項目是否等於 2。  
  
```JavaScript  
[1,2,3].findIndex(function(x) { x == 2; });  
// Returns an index value of 1.  
  
```  
  
## <a name="example"></a>範例  
 下列範例使用箭號語法來測試每個項目。 在此範例中，不會有任何項目傳回 `true`，而 `findIndex` 傳回 -1。  
  
```  
[1,2,3].findIndex(x => x == 4);  
// Returns an index value of -1.   
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]