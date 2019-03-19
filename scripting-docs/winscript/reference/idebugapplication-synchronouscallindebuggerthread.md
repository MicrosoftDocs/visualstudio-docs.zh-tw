---
title: IDebugApplication::SynchronousCallInDebuggerThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.SynchronousCallInDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::SynchronousCallInDebuggerThread
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5460efaa3448c7812707e0baa7b2f5afe1d27a0
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154021"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
提供一個機制，讓呼叫者在偵錯工具執行緒中執行程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pptc`  
 [in]要呼叫的物件。  
  
 `dwParam1`  
 [in]第一個參數傳遞至`IDebugThreadCall::ThreadCallHandler`方法。  
  
 `dwParam2`  
 [in]第二個參數傳遞至`IDebugThreadCall::ThreadCallHandler`方法。  
  
 `dwParam3`  
 [in]要傳遞給第三個參數`IDebugThreadCall::ThreadCallHandler`方法。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 語言引擎和主機通常使用這個方法來實作單一執行緒實作之上的無限制執行緒物件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugThreadCall 介面](../../winscript/reference/idebugthreadcall-interface.md)