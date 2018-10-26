---
title: IDebugThread2::GetThreadId |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4968bdd26607f68c8a1e8e4467904939ee0f528d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873444"
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
取得系統執行緒識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetThreadId (   
   DWORD* pdwThreadId  
);  
```  
  
```csharp  
int GetThreadId (   
   out uint pdwThreadId  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwThreadId`  
 [out]傳回系統執行緒識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 執行緒識別碼用來識別處理序中的所有其他執行緒之間的執行緒。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來簡單`CProgram`實作的物件[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)介面。  
  
```cpp  
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {     
   *pdwThreadId = GetCurrentThreadId();    
   return NOERROR;    
}    
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)