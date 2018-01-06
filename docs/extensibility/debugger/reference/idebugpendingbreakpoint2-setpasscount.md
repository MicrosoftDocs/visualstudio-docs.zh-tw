---
title: "IDebugPendingBreakpoint2::SetPassCount |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ab9a8ceec8c0f3a1b8d6c3c18fcf9c5c2a5b0b91
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
設定或變更暫止中斷點相關聯的密碼計數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```csharp  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bpPassCount`  
 [in]A [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)結構，其中包含傳遞計數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_BP_DELETED`若已刪除中斷點。  
  
## <a name="remarks"></a>備註  
 任何暫止中斷點先前關聯的傳遞計數將會遺失。 暫止中斷點，從這個繫結的所有中斷點會都呼叫以將其傳遞計數設定為`bpPassCount`參數。  
  
## <a name="see-also"></a>請參閱  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)