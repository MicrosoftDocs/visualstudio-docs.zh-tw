---
title: IDebugEngineProgram2::Stop |Microsoft Docs
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
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29067ce022150f53612ba053cee5ce20c2c96fa6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499634"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugEngineProgram2::Stop](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengineprogram2-stop)。  
  
停止執行此程式中的所有執行緒。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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

