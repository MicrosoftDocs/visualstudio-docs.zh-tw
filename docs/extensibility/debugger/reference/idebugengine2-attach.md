---
title: IDebugEngine2::Attach |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fb45d2196a9f84b8f956b8ede665df6e3ed249c2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
將偵錯引擎 (DE) 附加至程式或程式。 工作階段的偵錯管理員 (SDM) 執行同處理序以 SDM DE 時呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```csharp  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pProgram`  
 [in]陣列[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)代表要附加至程式的物件。 這些是連接埠的程式。  
  
 `rgpProgramNodes`  
 [in]陣列[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)代表程式節點，一個用於每個程式的物件。 此陣列中的程式節點代表做為中的相同程式`pProgram`。 指定程式節點，以供 DE 識別附加至程式。  
  
 `celtPrograms`  
 [in]程式和/或程式中的節點數目`pProgram`和`rgpProgramNodes`陣列。  
  
 `pCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)来用來偵錯事件傳送至 SDM 物件。  
  
 `dwReason`  
 [in]中的值[ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)列舉，指定可附加這些程式的原因。 如需詳細資訊，請參閱＜備註＞一節。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 有三個理由附加至程式中，如下：  
  
-   `ATTACH_REASON_LAUNCH`指出 DE 附加到程式，因為使用者已啟動包含該處理序。  
  
-   `ATTACH_REASON_USER`表示使用者已明確要求 DE 附加至程式 （或包含程式的處理序）。  
  
-   `ATTACH_REASON_AUTO`指出 DE 附加到特定的程式，因為它已經偵錯其他程式的特定處理程序。 這也稱為自動附加。  
  
 呼叫這個方法時，DE 必須傳送這些事件順序：  
  
1.  [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) （如果它已經尚未傳送的偵錯引擎的特定執行個體）  
  
2.  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3.  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
 此外，如果附加的原因是`ATTACH_REASON_LAUNCH`，需要傳送給 DE [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)事件。  
  
 一次 DE 取得[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件對應於所偵錯程式可供查詢的任何私用介面。  
  
 所給定陣列中呼叫程式節點的方法之前`pProgram`或`rgpProgramNodes`，模擬，如果需要上, 應該啟用`IDebugProgram2`代表程式節點的介面。 一般來說，不過，這個步驟並非必要。 如需詳細資訊，請參閱[安全性問題](../../../extensibility/debugger/security-issues.md)。  
  
## <a name="see-also"></a>請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)