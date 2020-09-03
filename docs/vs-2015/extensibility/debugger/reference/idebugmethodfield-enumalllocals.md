---
title: IDebugMethodField：： EnumAllLocals |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2f0f89c3fee45d6d56b845753958d697e41ab11f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190882"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

建立方法的所有區域變數的列舉值，包括編譯器內部產生的變數。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pAddress`  
 在 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 物件，代表方法內的 debug 位址，指向特定範圍或內容。  
  
 `ppLocals`  
 擴展傳回 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 物件，代表指定範圍中所有區域變數的清單。否則，會傳回 null 值，表示沒有區域變數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK，如果沒有任何區域變數，則傳回 S_FALSE。 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 只會列舉區塊內定義的變數，其中包含指定的 debug 位址。 此方法包含任何編譯器產生的區域變數。 如果所需的全部都是來源中明確定義的區域變數，請呼叫 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) 方法。  
  
 方法可以包含多個範圍內容或區塊。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
