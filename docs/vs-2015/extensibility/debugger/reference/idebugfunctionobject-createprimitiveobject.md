---
title: IDebugFunctionObject：： CreatePrimitiveObject |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3531483c113c37587b253bed90a9985541b2e526
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179452"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

建立基本資料物件，例如簡單的整數。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT CreatePrimitiveObject(   
   OBJECT_TYPE    ot,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreatePrimitiveObject(  
   enum_OBJECT_TYPE ot,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ot`  
 在 [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) 列舉中的值，代表要建立的基本類型。  
  
 `ppObject`  
 擴展傳回代表新建立之物件的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 呼叫這個方法，以建立代表基本物件的物件，該物件是 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 介面所代表之函式的參數。 例如，如果運算式字串為 "myString (5) "，則會使用這個方法來建立代表整數5的物件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
