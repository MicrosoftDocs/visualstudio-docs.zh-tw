---
title: IDebugStackFrame2::GetThread |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame2::GetThread
helpviewer_keywords:
- IDebugStackFrame2::GetThread
ms.assetid: cbeef85b-3dd7-4f97-adc2-c4d197d979fc
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 70713a4f686b9edd14446f8c5c7dce7594609d29
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugstackframe2getthread"></a>IDebugStackFrame2::GetThread
取得與堆疊框架關聯的執行緒。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetThread (   
   IDebugThread2** ppThread  
);  
```  
  
```csharp  
int GetThread (   
   out IDebugThread2 ppThread  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppThread`  
 [out]傳回[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，代表在執行緒。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)