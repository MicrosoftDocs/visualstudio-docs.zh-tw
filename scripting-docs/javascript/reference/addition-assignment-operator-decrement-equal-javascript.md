---
title: 加法指派運算子 （+ =） (JavaScript) |Microsoft 文件
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
- +=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- addition assignment operator (+=)
- += operator
- assignment operators, JavaScript
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38d86c537dda90dd7f44923b97384b3609dad5ba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633628"
---
# <a name="addition-assignment-operator--javascript"></a>加法指派運算子 (+=) (JavaScript)
將運算式的值加入此變數的值，然後將結果指派給此變數。  
  
## <a name="syntax"></a>語法  
  
```  
  
result += expression   
```  
  
## <a name="parameters"></a>參數  
 `result`  
 任何變數。  
  
 `expression`  
 任何運算式。  
  
## <a name="remarks"></a>備註  
 使用此運算子是完全如同指定： `result = result + expression`。  
  
 兩個運算式的型別決定的行為`+=`運算子。  
  
|如果|然後|  
|--------|----------|  
|這兩個運算式都是數值或布林值|新增|  
|這兩個運算式都是字串|串連|  
|一個運算式為數值，另一個是字串|串連|  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [加法運算子 （+）](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)