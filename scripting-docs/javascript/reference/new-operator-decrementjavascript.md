---
title: new 運算子 (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- new_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- new operator in JavaScript
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ad004abb534d69bed1a1bd9bbd2ae96755544b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638578"
---
# <a name="new-operator-javascript"></a>new 運算子 (JavaScript)
建立新的物件。  
  
## <a name="syntax"></a>語法  
  
```  
new constructor ([arguments])   
```  
  
## <a name="parameters"></a>參數  
 `constructor`  
 必要項。 物件的建構函式。 如果建構函式沒有引數，則可以省略括號。  
  
 `arguments`  
 選擇項。 任何要傳遞給新的物件建構函式的引數。  
  
## <a name="remarks"></a>備註  
 `new`運算子會執行下列工作：  
  
-   它沒有任何成員建立的物件。  
  
-   它會呼叫建構函式，該物件，將指標傳遞至新建立的物件做為`this`指標。  
  
-   建構函式，然後初始化根據傳遞至建構函式的引數的物件。  
  
 這些是有效的用法的範例**新**運算子。  
  
```JavaScript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [function 陳述式](../../javascript/reference/function-statement-javascript.md)