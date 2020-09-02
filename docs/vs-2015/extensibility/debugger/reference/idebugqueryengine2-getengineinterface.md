---
title: IDebugQueryEngine2：： GetEngineInterface |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12bdcf9de9731095a224f394cab13f3833f126de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158118"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得自訂的 debug engine (DE) 介面。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetEngineInterface(   
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetEngineInterface(   
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppUnk`  
 擴展傳回 `IUnknown` 物件，表示 debug engine (DE) ，而且可以查詢與 DE (相關聯的任何其他有效介面，例如 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 或 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)) 。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 產生的介面應謹慎使用，因為透過這個方法所抓取的介面呼叫會規避會話 debug manager 的處理，而且可能會導致 SDM 進入不正常的狀態，或在進行偵錯工具時產生錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
