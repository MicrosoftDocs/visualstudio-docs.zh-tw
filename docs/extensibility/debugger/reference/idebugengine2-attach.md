---
title: IDebugEngine2::Attach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d08ceb5db30b23d9e8df77bec12c0f9cb1c2c77
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854239"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
將偵錯引擎 (DE) 附加至程式或程式。 執行同處理序以 SDM DE 時，由工作階段的偵錯管理員 (SDM) 呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```csharp  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pProgram`  
 [in]陣列[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)代表要附加至程式的物件。 這些是連接埠的程式。  
  
 `rgpProgramNodes`  
 [in]陣列[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)代表程式節點，一個用於每個程式的物件。 此陣列中的程式節點代表相同的程式中`pProgram`。 程式節點會提供，以供 DE 識別所要附加至的程式。  
  
 `celtPrograms`  
 [in]程式和/或程式中的節點數目`pProgram`和`rgpProgramNodes`陣列。  
  
 `pCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)来用來將偵錯事件傳送到 SDM 物件。  
  
 `dwReason`  
 [in]值，以從[ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)列舉，指定附加這些程式的原因。 如需詳細資訊，請參閱＜備註＞一節。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 有三個，如下所示附加至程式中，原因：  
  
- `ATTACH_REASON_LAUNCH` 表示 DE 附加至程式，因為使用者啟動包含它的處理序。  
  
- `ATTACH_REASON_USER` 表示使用者已明確要求 DE 附加至程式 （或包含程式的處理序）。  
  
- `ATTACH_REASON_AUTO` 表示 DE 附加到特定的程式，因為它已經偵錯其他程式中特定的處理程序。 這也稱為自動附加。  
  
  呼叫這個方法時，DE 必須傳送這些事件順序：  
  
1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) （如果它沒有已傳送的偵錯引擎的特定執行個體）  
  
2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
   此外，如果是因為附加`ATTACH_REASON_LAUNCH`，需要傳送 DE [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)事件。  
  
   一次 DE 取得[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件對應至要偵錯之程式的任何私用介面可供查詢。  
  
   之前呼叫程式節點的方法中所指定的陣列`pProgram`或是`rgpProgramNodes`，模擬，如有需要上, 應該啟用`IDebugProgram2`介面，表示程式節點。 一般來說，不過，此步驟不需要。 如需詳細資訊，請參閱 <<c0> [ 安全性問題](../../../extensibility/debugger/security-issues.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)