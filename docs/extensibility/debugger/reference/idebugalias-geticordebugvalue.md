---
title: IDebugAlias::GetICorDebugValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38debf5be309a97367f9a14c5f07ec3db6e7b666
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005939"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
擷取的 managed 程式碼介面，表示與此別名相關聯的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppUnk`  
 [out]`IUnknown`介面，表示與此別名相關聯的值。 這個介面可以查詢`ICorDebugValue`介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法只適用於受管理的值 (`ICorDebugValue`是一種介面中可用[!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)]且定義在[!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)]SDK cordebug.idl 檔案中的)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)