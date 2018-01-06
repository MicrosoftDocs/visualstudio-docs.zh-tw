---
title: "IDebugAlias::GetICorDebugValue |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAlias::GetICorDebugValue
helpviewer_keywords: IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4e23641f246d064dc65c01788bdfb780c0f09869
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>請參閱  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)