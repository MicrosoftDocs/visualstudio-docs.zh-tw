---
title: IDebugEngineProgram2：： Stop |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb74cb2940a91bbc64fa4a06f28d07a828357fc6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431481"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

停止在此程式中執行的所有線程。  
  
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
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 當在多程式環境中進行此程式的偵錯工具時，會呼叫這個方法。 收到來自某個其他程式的停止事件時，會在此程式上呼叫這個方法。 此方法的實值應該是非同步;也就是說，並非所有線程都必須在此方法傳回之前停止。 此方法的實作為在此程式上呼叫 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) 方法，可能會很簡單。  
  
 回應此方法時，不會傳送任何偵錯工具事件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
