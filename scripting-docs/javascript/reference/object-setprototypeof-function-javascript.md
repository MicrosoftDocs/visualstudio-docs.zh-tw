---
title: Object.setPrototypeOf Function (JavaScript) | Microsoft Docs
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
ms.assetid: a2609f6e-aeee-4c13-b7cf-c31ddf58ff35
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a2ae28420893cd49691c1a6ac50fe5896700947
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
ms.locfileid: "29900834"
---
# <a name="objectsetprototypeof-function-javascript"></a>Object.setPrototypeOf 函式 (JavaScript)
設定物件的原型。  
  
## <a name="syntax"></a>語法  
  
```  
Object.setPrototypeOf(obj, proto);  
```  
  
#### <a name="parameters"></a>參數  
 `obj`  
 必要。 您要為其設定原型的物件。  
  
 `proto`  
 必要。 新的原型物件。  
  
## <a name="remarks"></a>備註  
  
> [!WARNING]
>  在對於原型已變更之物件具有存取權的所有 JavaScript 程式碼上，設定此原型可能會降低效能。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何設定物件的原型。  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(Object.getPrototypeOf(rec) === Rectangle.prototype);  // Returns true  
    Object.setPrototypeOf(rec, Object.prototype);  
    console.log(Object.getPrototypeOf(rec) === Rectangle.prototype);  // Returns false  
}  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何透過將屬性新增至原則，以將屬性新增至物件。  
  
```JavaScript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
Object.setPrototypeOf(obj, proto);  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例會將屬性新增至 `String` 物件，方法是對此物件設定新原型。  
  
```JavaScript  
var stringProp = { desc: "description" };  
  
Object.setPrototypeOf(String, stringProp);  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    Object.setPrototypeOf(s1, String); // Can't be set.  
    Object.setPrototypeOf(s2, String);  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
