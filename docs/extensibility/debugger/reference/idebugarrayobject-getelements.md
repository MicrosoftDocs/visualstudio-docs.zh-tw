---
title: IDebugArrayObject::GetElements |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7693c4ed3442cf86a0e310a6e2dd6d75655fcb69
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904722"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
取得陣列的所有項目的列舉程式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```csharp  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppEnum`  
 [out]傳回[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)物件，可讓您列舉所有的項目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 或者，使用[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)並[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)方法來逐一查看項目。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)