---
title: "IDebugEngineLaunch2::CanTerminateProcess |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords: IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 78b5a55f79c0f7d6e30574c1bfff954566c500b2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
決定是否可以終止處理程序。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CanTerminateProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```csharp  
int CanTerminateProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pProcess`  
 [in][IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)物件，表示終止程序。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 傳回`S_FALSE`如果引擎無法結束處理序，例如，因為存取被拒。  
  
## <a name="remarks"></a>備註  
 如果此方法傳回`S_OK`，然後它[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)實際結束這個處理序可以呼叫方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)