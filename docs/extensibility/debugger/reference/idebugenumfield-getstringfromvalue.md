---
title: IDebugEnumField::GetStringFromValue |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b142d8687927ec9951c25b35af1637e52b54486d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945836"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
這個方法會取得指定其值的列舉常數名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```csharp  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `value`  
 [in]要取得的列舉型別名稱的常值。  
  
 `pbstrValue`  
 [out]傳回列舉常數的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`值沒有相關聯的名稱，則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果有多個相同的值相關聯的名稱，將會傳回定義列舉中的第一個名稱。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)