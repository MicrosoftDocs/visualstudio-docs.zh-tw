---
title: "IDebugBreakpointEvent2::EnumBreakpoints |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBreakpointEvent2:::EnumBreakpoints
helpviewer_keywords: IDebugBreakpointEvent2:::EnumBreakpoints
ms.assetid: 606a9625-ee43-4e84-9a47-af9a50d2d005
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5cf2190586db74fa36927e333641f4a8cf516255
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbreakpointevent2enumbreakpoints"></a>IDebugBreakpointEvent2::EnumBreakpoints
建立目前程式碼位置中引發的所有中斷點的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumBreakpoints(  
  IEnumDebugBoundBreakpoints2** ppEnum  
);  
```  
  
```csharp  
int EnumBreakpoints(  
  out IEnumDebugBoundBreakpoints2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppEnum`  
 [out]傳回[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)列舉與目前的程式碼位置相關聯的所有中斷點的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 並非所有的特定位置的中斷點可能會引發特定的時間 （例如，條件中斷點不會引發直到符合條件為止）。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)