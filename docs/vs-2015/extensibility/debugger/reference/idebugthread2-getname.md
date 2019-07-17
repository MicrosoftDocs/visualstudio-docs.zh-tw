---
title: IDebugThread2::GetName |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 509db8c30aabd8a4163ea433bb06a99d4bfa2fb9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153045"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得執行緒的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 擷取的名稱一律可以顯示的名稱，而且此名稱描述執行緒。 執行緒名稱可能會衍生自執行階段架構支援將具名的執行緒，或可能被衍生自的偵錯引擎的名稱。 或者，設定執行緒名稱，藉由呼叫[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
