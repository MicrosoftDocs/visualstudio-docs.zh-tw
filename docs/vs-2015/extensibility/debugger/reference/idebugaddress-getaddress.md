---
title: IDebugAddress::GetAddress |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4a469ba1e6f85a1ac83ba06efa45ba2b6c4fcbc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496725"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugAddress::GetAddress](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugaddress-getaddress)。  
  
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

