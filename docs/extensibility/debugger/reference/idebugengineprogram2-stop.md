---
title: IDebugEngineProgram2::Stop |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab5bec65dc3f53681d40743bea694295ff69944b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113851"
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
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 此程式在多個程式的環境中偵錯時，會呼叫這個方法。 收到停止事件，從某些其他程式時，於這個程式會呼叫這個方法。 這個方法的實作應該是非同步的;也就是說，並非所有的執行緒應該需要這個方法會傳回前，先停止。 這個方法的實作可能會只要呼叫[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)於這個程式的方法。  
  
 這個方法的回應以傳送沒有偵錯事件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)