---
title: IDebugQueryEngine2::GetEngineInterface |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 65f40bf3e0e110a6d945921d06443f0c8a608d20
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
取得自訂偵錯引擎 (DE) 介面。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 [out]傳回`IUnknown`物件代表的偵錯引擎 (DE)，而這可以查詢其他 DE 與相關聯的有效介面 (例如[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)或[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md))。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 產生的介面應該使用時請務必小心，因為呼叫這個方法所擷取的介面規避工作階段偵錯管理員處理，而且可能會導致 SDM 進入不正常的狀態，或者偵錯時產生錯誤。  
  
## <a name="see-also"></a>請參閱  
 [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)