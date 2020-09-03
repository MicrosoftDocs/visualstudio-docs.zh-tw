---
title: IDebugFunctionObject：：評估 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e19baa193bb015056b9e5abde4c7a274f635c0c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179416"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

呼叫函數，並傳回產生的值做為物件。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppParams`  
 在代表輸入參數之 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 物件的陣列。 這些參數都是使用 `Create` [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 介面中的其中一個方法所建立。  
  
 `dwParams`  
 在陣列中的參數數目 `ppParams` 。  
  
 `dwTimeout`  
 在指定從這個方法傳回之前等候的最長時間（以毫秒為單位）。 使用 `INFINITE` 可無限期等候。  
  
 `ppResult`  
 擴展傳回 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ，表示函式的值做為物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會設定並執行 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 物件所代表之函式的呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
