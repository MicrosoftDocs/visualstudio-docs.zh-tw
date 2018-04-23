---
title: IDebugObject2::GetBackingFieldForProperty |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7729f55c93274796d3c81f280618653b873bc40b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
取得變數的欄位 （如果有的話），可能會支援這個物件所表示的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppObject`  
 [out][IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)物件描述的支援欄位。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)物件代表 managed 程式碼類別屬性，也就是使用 get 方法和 （或) set 存取子。 這類屬性通常會需要包含操作的屬性值的變數。 這個變數就是所謂的支援欄位。 如果沒有任何物件的支援欄位，然後確定傳回的 null 值： 某些呼叫端可能不會注意到傳回的值，但會改為查看中如果傳回了 null 值`ppObject`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)