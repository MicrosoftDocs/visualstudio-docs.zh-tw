---
title: IDebugThread2::GetName |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e75fe48ee3974857de0acd4e3af99c0c3ea16314
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
取得執行緒的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName (   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrName`  
 [out]傳回執行緒的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 擷取的名稱永遠可以顯示的名稱，而且此名稱會說明執行緒。 執行緒名稱可能會衍生自執行階段架構支援將具名的執行緒，或可能被衍生自的偵錯引擎的名稱。 或者，設定執行緒名稱，由呼叫[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)方法。  
  
## <a name="see-also"></a>請參閱  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)