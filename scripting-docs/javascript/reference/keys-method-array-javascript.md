---
title: keys 方法 （陣列） (JavaScript) |Microsoft 文件
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
ms.assetid: fc5b6a30-642c-4bd7-ad31-a42667af2f3f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f600facc91dd10219196f580abd0f52537010dfd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637418"
---
# <a name="keys-method-array-javascript"></a>keys 方法 (陣列) (JavaScript)
傳回迭代器，它會傳回陣列的索引值。  
  
## <a name="syntax"></a>語法  
  
```  
arrayObj.keys();  
```  
  
#### <a name="parameters"></a>參數  
 `arrayObj`  
 必要項。 陣列物件。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列範例會顯示如何取得陣列的機碼值。  
  
```JavaScript  
var k = ["a", "b", "c"].keys();  
// k.next().value == 0  
// k.next().value == 1  
// k.next().value == 2   
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]