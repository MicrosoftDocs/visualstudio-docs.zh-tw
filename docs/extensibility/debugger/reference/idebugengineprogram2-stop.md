---
title: IDebugEngineProgram2::Stop |Microsoft Docs
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
ms.openlocfilehash: 17919b42f97d2255325c1ceae119014521325c7b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860821"
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