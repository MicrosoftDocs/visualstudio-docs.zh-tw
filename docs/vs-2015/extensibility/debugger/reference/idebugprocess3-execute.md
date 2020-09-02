---
title: IDebugProcess3：： Execute |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f9b70deabd4cb7996d76373c6216057678c0bd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386169"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

從停止狀態繼續執行此進程。 任何先前的執行狀態 (（例如步驟) ）都會清除，而且進程會再次開始執行。  
  
> [!NOTE]
> 應該使用這個方法，而不是 [執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pThread`  
 在代表要執行之執行緒的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 當使用者從其他進程的執行緒中的停止狀態開始執行時，會在這個進程上呼叫這個方法。 當使用者從 IDE 中的 [**調試**程式] 功能表選取 [**啟動**] 命令時，也會呼叫這個方法。 這種方法的執行方式，可以像在進程中的目前線程上呼叫 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) 方法一樣簡單。  
  
> [!WARNING]
> 在處理此呼叫時，請勿將停止事件或立即 (同步) 事件傳送到 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ;否則，偵錯工具可能會停止回應。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [恢復](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
