---
title: IDebugFunctionObject::CreateObject |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b0b9a36dfac48d86963db68c3ab68500d8b8bfba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
建立使用建構函式的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateObject(   
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject(  
   IDebugFunctionObject pConstructor,   
   uint                 dwArgs,   
   IDebugObject[]       pArgs,   
   out IDebugObject     ppObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pConstructor`  
 [in][IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)物件，代表要建立之物件的建構函式。  
  
 `dwArgs`  
 [in]中的參數數目`pArg`陣列。 表示傳遞給建構函式的參數數目。  
  
 `pArg`  
 [in]陣列[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件代表的參數傳遞至建構函式。  
  
 `ppObject`  
 [out]傳回`IDebugObject`代表新建立的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 呼叫這個方法來建立物件，表示類別 （或其他需要的建構函式的複雜型別） 的執行個體也就是由表示的函式的參數[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面。  
  
 如果物件參數不需要建構函式，呼叫[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)方法。  
  
## <a name="see-also"></a>請參閱  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)