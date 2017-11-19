---
title: "IDebugAddress::GetAddress |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAddress::GetAddress
helpviewer_keywords: IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ed14b69dbc116514b191aadf58d209b4d39e458
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
傳回結構描述和其位置，其範圍或容器內的物件。  
  
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
 [in、 out]A [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)填入這個方法的結構。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構傳遞至這個方法，然後使用適當的資訊填入它。 這項資訊的解譯方式取決於傳回的資訊和符號處理常式本身的種類。 請參閱[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)