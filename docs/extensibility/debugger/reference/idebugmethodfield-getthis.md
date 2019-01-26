---
title: IDebugMethodField::GetThis |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fdb9e0c1503ad924c642d4f6c70b505a99874b4a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035311"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
取得`this`(`Me`在[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]) 的物件，包含方法的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppClass`  
 [out]傳回[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件，代表"this"指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 在物件導向語言中，有通常是目前的具現化之類別的隱含的指標。 這就所謂`this`在 C# / c + + 和 as`Me`在[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)