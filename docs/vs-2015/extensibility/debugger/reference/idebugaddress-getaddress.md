---
title: IDebugAddress：： GetAddress |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4d3263ca020f491e0c1cf20ee49792cacfbc362
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186680"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

傳回結構，描述物件與其在其範圍或容器內的位置。  
  
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
 [in，out]由這個方法填入的 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 結構。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構會傳遞給這個方法，然後將其填入適當的資訊。 這項資訊的解讀方式取決於傳回的資訊類型，以及符號處理常式本身。 如需詳細資訊，請參閱 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 。  
  
## <a name="see-also"></a>另請參閱  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
