---
title: IDebugEngineProgram2::Stop |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e60b328ee13a47df9d7656c992f81e63cbbd2ed
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983777"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
停止執行此程式中的所有執行緒。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Stop(   
   void   
);  
```  
  
```csharp  
int Stop();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 在多重程式環境中，正在偵錯此程式時，會呼叫這個方法。 收到停止 」 事件從一些其他程式時，此方法稱為這個方案。 此方法的實作應該是非同步的;也就是並非所有的執行緒應該需要這個方法會傳回之前，先停止。 此方法的實作可能會非常簡單，像是呼叫[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)此方案的方法。  
  
 沒有偵錯事件是傳送以回應這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)