---
title: IDebugAddress::GetAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e91b90fd54ea70aed729707e927ad2394d756139
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917675"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
傳回描述物件和它的位置，其範圍或容器內的結構。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pAddress`  
 [in、 out]A [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構，這個方法會填入。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構傳遞給這個方法，然後將它填滿的適當資訊。 這項資訊的解譯方式取決於傳回的資訊和符號處理常式本身的類型。 請參閱[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)