---
title: "IDebugThreadCall::ThreadCallHandler |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugThreadCall.ThreadCallHandler
apilocation: jscript.dll
helpviewer_keywords: IDebugThreadCall::ThreadCallHandler
ms.assetid: c6d5d9db-bfed-44ec-90bc-46637f7de0ab
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2b7a22026090c8b3b8b7ded4c960ebf92689cd4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugthreadcallthreadcallhandler"></a>IDebugThreadCall::ThreadCallHandler
如何處理到另一個執行緒中執行程式碼呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ThreadCallHandler(  
   DWORD_PTR  dwParam1,  
   DWORD_PTR  dwParam2,  
   DWORD_PTR  dwParam3  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwParam1`  
 [in]第一個參數。  
  
 `dwParam2`  
 [in]第二個參數中。  
  
 `dwParam3`  
 [in]第三個參數中。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會處理在偵錯工具執行緒中執行程式碼呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugThreadCall 介面](../../winscript/reference/idebugthreadcall-interface.md)   
 [IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)   
 [IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)