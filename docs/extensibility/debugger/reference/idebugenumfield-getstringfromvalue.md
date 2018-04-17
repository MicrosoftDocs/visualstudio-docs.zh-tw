---
title: IDebugEnumField::GetStringFromValue |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 5
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 695c35e6d849806911aaf9cb293b53e66dbbca0e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
這個方法會取得指定其值的列舉常數的名稱。  
  
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
 [in]為其取得其名稱的列舉常數的值。  
  
 `pbstrValue`  
 [out]傳回列舉常數的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`值沒有相關聯的名稱，則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果有一個以上名稱相同的值相關聯，則將傳回的列舉型別中定義的第一個名稱。  
  
## <a name="see-also"></a>請參閱  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)