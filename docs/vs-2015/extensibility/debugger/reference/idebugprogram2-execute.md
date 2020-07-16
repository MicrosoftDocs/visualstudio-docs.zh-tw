---
title: IDebugProgram2：： Execute |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 676a3a7d184c1f34cafcfc2b2a4dd7a1c3f81a95
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387326"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

從停止狀態繼續執行此程式。 任何先前的執行狀態（例如步驟）都會清除，且程式會再次開始執行。  
  
> [!NOTE]
> 此方法已被取代。 請改用[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。  
  
## <a name="remarks"></a>備註  
 當使用者從其他程式的執行緒中的已停止狀態開始執行時，會在此程式上呼叫這個方法。 當使用者從 IDE 中的 [**調試**] 功能表選取 [**啟動**] 命令時，也會呼叫這個方法。 這個方法的執行方式就像是在程式的目前線程上呼叫[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)方法一樣簡單。  
  
> [!WARNING]
> 在處理這個呼叫時，請勿傳送停止事件或立即（同步）事件給[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md);否則偵錯工具可能會停止回應。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [發生](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [繼續](../../../extensibility/debugger/reference/idebugthread2-resume.md)
