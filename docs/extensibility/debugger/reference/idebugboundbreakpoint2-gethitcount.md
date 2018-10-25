---
title: IDebugBoundBreakpoint2::GetHitCount |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBoundBreakpoint2::GetHitCount
helpviewer_keywords:
- GetHitCount method
- IDebugBoundBreakpoint2::GetHitCount method
ms.assetid: 23481f37-047c-41d2-8286-4da1f4084961
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bcd12b3e0995e3e285dd166feb8b0ba3febd04fe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49927303"
---
# <a name="idebugboundbreakpoint2gethitcount"></a>IDebugBoundBreakpoint2::GetHitCount
取得此繫結中斷點目前叫用的次數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetHitCount(   
   DWORD* pdwHitCount  
);  
```  
  
```csharp  
int GetHitCount(   
   out uint pdwHitCount  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwHitCount`  
 [out]傳回叫用的次數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_BP_DELETED`如果繫結的中斷點物件的狀態設為`BPS_DELETED`(屬於[BP_STATE](../../../extensibility/debugger/reference/bp-state.md)列舉型別)。  
  
## <a name="remarks"></a>備註  
 叫用的次數是此中斷點已在目前工作階段的執行期間引發的次數。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)