---
title: entries 方法 （陣列） (JavaScript) |Microsoft 文件
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
ms.assetid: 9bc46afb-74d2-4f99-8c95-f46475acf21d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff1e32ba0782d637ea1418daf5b3a56203d7e34b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636318"
---
# <a name="entries-method-array-javascript"></a>項目方法 (陣列) (JavaScript)
傳回會傳回陣列之機碼值組的迭代器。  
  
## <a name="syntax"></a>語法  
  
```  
arrayObj.entries();  
```  
  
#### <a name="parameters"></a>參數  
 `arrayObj`  
 必要項。 陣列物件。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列範例顯示如何取得陣列的機碼值組。  
  
```JavaScript  
var entries = ["a", "b", "c"].entries();  
// entries.next().value == [0, "a"]  
// entries.next().value == [1, "b"]  
// entries.next().value == [2, "c"]   
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]