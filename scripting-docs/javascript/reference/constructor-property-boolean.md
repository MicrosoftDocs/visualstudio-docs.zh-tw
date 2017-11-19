---
title: "constructor 屬性 （布林值） |Microsoft 文件"
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
ms.assetid: b67ca875-23c6-4687-a5ce-1cdd25d1c923
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 091da5342c4713c8eba646a8bd78c315a6a0fa48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-boolean"></a>constructor 屬性 (布林值)
指定建立布林值的函數。  
  
## <a name="syntax"></a>語法  
  
```  
  
boolean.constructor([[value])  
```  
  
#### <a name="parameters"></a>參數  
 `boolean`  
 布林值的名稱。  
  
 `value`  
 選擇項。 指定布林的值。 這可以是 1 或 0，數字或字串"true"false"。  
  
## <a name="remarks"></a>備註  
 `constructor`屬性包含布林值物件的執行個體的建構函式的參考。  
  
## <a name="example"></a>範例  
 下列範例說明如何使用建構函式屬性。  
  
```JavaScript  
var x = new Boolean("true");  
  
if (x.constructor == Boolean)  
    document.write("Object is a Boolelan.");  
  
// Output:  
// Object is a Boolean.  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]