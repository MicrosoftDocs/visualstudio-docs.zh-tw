---
title: IDebugPortSupplier2::EnumPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2::EnumPorts
helpviewer_keywords:
- IDebugPortSupplier2::EnumPorts
ms.assetid: 88b57fd2-eba1-44fa-bd34-cf2ad2b1ff87
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 505e9226aed8cb9ef0ba16de0a014766c2b33a5f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55025016"
---
# <a name="idebugportsupplier2enumports"></a>IDebugPortSupplier2::EnumPorts
擷取一份連接埠提供者所提供的所有連接埠。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumPorts(   
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```csharp  
int EnumPorts(   
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppEnum`  
 [out]傳回[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)物件，其中包含提供的連接埠清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)