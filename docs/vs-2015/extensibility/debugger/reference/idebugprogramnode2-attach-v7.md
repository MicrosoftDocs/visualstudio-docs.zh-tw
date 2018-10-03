---
title: IDebugProgramNode2::Attach_V7 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 375b9d4acffe3747b05c12b50abb65ced86fab4c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500257"
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugProgramNode2::Attach_V7](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramnode2-attach-v7)。  
  
已被取代。 請勿使用。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```csharp  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pMDMProgram`  
 [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)代表要附加至程式的介面。  
  
 `pCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)介面，以用來將偵錯事件傳送到 SDM。  
  
 `dwReason`  
 [in]值，以從[ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)列舉，指定將附加的原因。  
  
## <a name="return-value"></a>傳回值  
 實作應該一律傳回`E_NOTIMPL`。  
  
## <a name="remarks"></a>備註  
  
> [!WARNING]
>  至於[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]，這個方法已不再使用，且應該一律傳回`E_NOTIMPL`。 請參閱[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)介面的替代方法，如果需要指出無法將它附加至 [程式] 節點，或 [程式] 節點只需要設定程式`GUID`。 否則，實作[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。  
  
## <a name="prior-to-visual-studio-2005"></a>Visual Studio 2005 之前  
 這個方法需要 DE 執行正在偵錯之程式的位址空間中時，才實作。 否則，此方法應傳回`S_FALSE`。  
  
 呼叫這個方法時，必須傳送 DE [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)事件物件，如果它沒有已傳送的這個執行個體[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)介面，以及[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)並[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)事件物件。 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)事件物件，便會如果`dwReason`參數是`ATTACH_REASON_LAUNCH`。  
  
 必須先呼叫 DE [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)方法[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)提供的物件[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件物件，並必須儲存該程式的 GUID中的執行個體資料`IDebugProgram2`DE 所實作的物件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)

