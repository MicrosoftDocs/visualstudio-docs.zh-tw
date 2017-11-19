---
title: "Object.assign 函式 (Object) (JavaScript) |Microsoft 文件"
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c156369299e58eac556d43a87476de2ce09173e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="objectassign-function-object-javascript"></a>Object.assign 函式 (物件) (JavaScript)
將值從一或多個來源物件複製到目標物件。  
  
## <a name="syntax"></a>語法  
  
```  
Object.assign(target, ...sources );  
```  
  
#### <a name="parameters"></a>參數  
 `target`  
 必要項。 將可列舉屬性複製到其中的物件。  
  
 `...sources`  
 必要項。 從中複製可列舉屬性的一或多個物件。  
  
## <a name="exceptions"></a>例外狀況  
 如果發生終止複製作業的指派錯誤，則此函式會擲回 `TypeError`。 如果目標屬性不可寫入，則會擲回 `TypeError`。  
  
## <a name="remarks"></a>備註  
 此函式會傳回目標物件。 只有*可列舉自己*屬性都會從來源物件複製到目標物件。 您可以使用此函式來合併或複製物件。  
  
 `null` 或 `undefined` 來源會被視為空物件，而且不會提供任何項目給目標物件。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用 `Object.assign` 合併物件。  
  
```JavaScript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 `Object.assign` 複製物件。  
  
```JavaScript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]