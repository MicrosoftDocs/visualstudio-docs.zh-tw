---
title: IDebugThread2::GetLogicalThread |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: aa776afaeaec4056417c211c260ae27123a590ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
偵錯引擎不會實作這個方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetLogicalThread(   
   IDebugStackFrame2*     pStackFrame,  
   IDebugLogicalThread2** ppLogicalThread  
);  
```  
  
```csharp  
int GetLogicalThread(   
   IDebugStackFrame2        pStackFrame,  
   out IDebugLogicalThread2 ppLogicalThread  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pStackFrame`  
 [in][IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)物件，代表堆疊框架。  
  
 `ppLogicalThread`  
 [out]傳回`IDebugLogicalThread2`代表相關聯的邏輯執行緒的介面。 偵錯引擎實作應該設定為 null 的值。  
  
## <a name="return-value"></a>傳回值  
 偵錯引擎實作一律會傳回`E_NOTIMPL`。  
  
## <a name="see-also"></a>請參閱  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)