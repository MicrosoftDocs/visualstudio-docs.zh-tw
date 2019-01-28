---
title: IDebugClassField::GetEnclosingClass |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37dcb0eb23cf216b604d927309cd395252d59792
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040862"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
取得包含這個類別的類別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppClassField`  
 [out]傳回[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件，表示封入類別。 如果沒有封入類別，則傳回 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果類別以表示這[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件是巢狀的類別，則`ppClassField`參數會傳回`IDebugClassField`物件，表示封入類別。 例如，假設此類別定義：  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 呼叫`GetEnclosingClass`方法`IDebugClassField`物件，代表`NestedClass`類別會傳回`IDebugClassField`物件，表示類別`RootClass`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)