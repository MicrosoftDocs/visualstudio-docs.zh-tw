---
title: IDebugFunctionObject：： CreateObjectNoConstructor |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ea00035eb220ccd08590ceaea6db98944f4657a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179465"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

建立沒有任何函式的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT CreateObjectNoConstructor(   
   IDebugField*   pClassObject,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateObjectNoConstructor(  
   IDebugField      pClassField,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pClassObject`  
 在 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件，代表要建立之物件的類型。  
  
 `ppObject`  
 擴展傳回代表新建立之物件的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 呼叫這個方法來建立物件，該物件代表結構或複雜型別的實例， (不需要函式) ，也就是 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 介面所代表的函式的參數。  
  
 如果物件參數需要函式，請呼叫 [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) 方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
