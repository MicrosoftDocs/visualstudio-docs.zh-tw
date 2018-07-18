---
title: IDebugAlias::GetICorDebugValue |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bfe0d8e4734c0d836b2dc6009fdedfa264720778
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099047"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
擷取的 managed 程式碼介面，表示與此別名相關聯的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppUnk`  
 [out]`IUnknown`介面，表示與此別名相關聯的值。 這個介面可以查詢`ICorDebugValue`介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法只適用於受管理的值 (`ICorDebugValue`是一種介面中可用[!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)]而定義在[!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)]SDK cordebug.idl 檔案中的)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)