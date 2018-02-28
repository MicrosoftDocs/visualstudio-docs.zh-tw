---
title: "Boolean 物件 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- boolean_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Boolean object
- Boolean data type, Boolean object
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20695376e4935cf6ddc34f30e373df19575ece3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="boolean-object-javascript"></a>Boolean 物件 (JavaScript)
建立新的布林值。  
  
## <a name="syntax"></a>語法  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## <a name="parameters"></a>參數  
 `boolObj`  
 必要項。 要對其指派 `Boolean` 物件的變數名稱。  
  
 `boolValue`  
 選擇項。 新的物件初始的布林值。 如果`boolvalue`省略，或者是`false`、 0、 `null`， `NaN`，或空字串，Boolean 物件的初始值為`false`。 否則，初始的值是`true`。  
  
## <a name="remarks"></a>備註  
 `Boolean`物件是布林資料類型的包裝函式。 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]隱含使用`Boolean`物件每當布林資料類型轉換成`Boolean`物件。  
  
 您很少具現化`Boolean`明確的物件。  
  
## <a name="properties"></a>屬性  
 下表列出 `Boolean` 物件的屬性。  
  
|屬性|說明|  
|--------------|-----------------|  
|[constructor 屬性](../../javascript/reference/constructor-property-boolean.md)|指定建立布林值的函數。|  
|[prototype 屬性](../../javascript/reference/prototype-property-boolean.md)|傳回布林原型的參考。|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>方法  
 下表列出 `Boolean` 物件的方法。  
  
|方法|說明|  
|------------|-----------------|  
|[toString 方法](../../javascript/reference/tostring-method-boolean-1.md)|傳回布林值的字串表示。|  
|[valueOf 方法](../../javascript/reference/valueof-method-boolean.md)|取得布林值的參考。|  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]