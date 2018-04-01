---
title: IDebugFunctionObject::CreatePrimitiveObject |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c72dd6d804c37496d2615ccd086ee095c75510d6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
建立基本資料的物件，例如簡單的整數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 [in]中的值[OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md)列舉型別代表類型的基本項目來建立。  
  
 `ppObject`  
 [out]傳回[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)代表新建立的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 呼叫這個方法來建立物件，表示的基本物件是由表示的函式的參數[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面。 例如，如果運算式字串為"myString(5)"，這個方法會用於建立物件，表示 5 的整數。  
  
## <a name="see-also"></a>請參閱  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)