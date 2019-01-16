---
title: 'Idiaframedata:: Execute |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6be6c631f9ea0db47829f305f90bd1c296de2f28
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958734"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
執行堆疊回溯，並傳回結果的堆疊查核行程框架介面中。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>參數  
 `frame`  
 [in][IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)保留狀態的畫面格暫存器的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 下表顯示可能的傳回值，這個方法。  
  
|值|說明|  
|-----------|-----------------|  
|E_DIA_INPROLOG|無法執行序言程式碼中的堆疊框架。|  
|E_DIA_SYNTAX|剖析 畫面格程式中發生錯誤。|  
|E_DIA_FRAME_ACCESS|無法存取暫存器或記憶體。|  
|E_DIA_VALUE|在 值 （例如，除數為零） 的計算錯誤。|  
  
## <a name="remarks"></a>備註  
 回溯堆疊偵錯期間，會呼叫這個方法。 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)用戶端應用程式接收到暫存器的更新，並提供所使用的方法實作物件`execute`方法。  
  
## <a name="see-also"></a>請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)