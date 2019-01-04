---
title: IDebugPortSupplier2::AddPort |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9db20f2034e1c094beb69a3397261c3522589a6c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867848"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
新增連接埠。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT AddPort(   
   IDebugPortRequest2* pRequest,  
   IDebugPort2**       ppPort  
);  
```  
  
```csharp  
int AddPort(   
   IDebugPortRequest2 pRequest,  
   out IDebugPort2    ppPort  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRequest`  
 [in][IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)物件，描述要加入的連接埠。  
  
 `ppPort`  
 [out]傳回[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)物件，表示連接埠。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法實際上會建立要求的通訊埠，以及將它新增至作用中的連接埠的連接埠提供者的內部清單。 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)可以先呼叫方法，以避免可能耗費時間的延遲。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)