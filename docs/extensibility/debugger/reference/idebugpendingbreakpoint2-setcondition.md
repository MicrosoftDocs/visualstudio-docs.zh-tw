---
title: IDebugPendingBreakpoint2::SetCondition |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2bc50ad1d763f196944e6246f891c5b4ed3893da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
設定或變更暫止中斷點具有相關聯的條件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```csharp  
int SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bpCondition`  
 [in]A [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)結構，指定要設定的條件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 暫止中斷點先前關聯的任何條件將會遺失。 若要設定其條件中指定的值稱為 「 暫止中斷點，從這個繫結的所有中斷點`bpCondition`參數。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)