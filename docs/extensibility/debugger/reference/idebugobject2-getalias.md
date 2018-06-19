---
title: IDebugObject2::GetAlias |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5917e0f78a2872cbd684830c8a03b1156a83734
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112365"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
如果有的話，取得與這個物件相關聯的別名。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int GetAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppAlias`  
 [out]傳回[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)表示此物件的別名的物件; 否則會傳回 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 物件的別名會透過呼叫[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)