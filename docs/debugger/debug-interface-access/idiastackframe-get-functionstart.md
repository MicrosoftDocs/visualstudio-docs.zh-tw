---
title: IDiaStackFrame::get_functionStart |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_functionStart
ms.assetid: e3e6e88b-0594-4d82-9457-480239a2e85a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 214f62788c77ea5a15d6065a1661213201d1a341
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827883"
---
# <a name="idiastackframegetfunctionstart"></a>IDiaStackFrame::get_functionStart
擷取指出區塊是否包含函式的進入點的旗標。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_functionStart (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]會傳回`TRUE`堆疊框架包含進入點函式; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`不支援的屬性。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)