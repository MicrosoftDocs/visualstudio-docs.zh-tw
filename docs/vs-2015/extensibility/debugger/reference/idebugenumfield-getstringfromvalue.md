---
title: IDebugEnumField：： GetStringFromValue |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecdd60c363e30afbe4c61e8e18660a17a06a5ce8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189001"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法會根據指定的值來取得列舉常數的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 在要取得列舉常數名稱的值。  
  
 `pbstrValue`  
 擴展傳回列舉常數的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功， `S_OK` 則傳回; 否則， `S_FALSE` 如果值沒有相關聯的名稱，則傳回，否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果有多個與相同值相關聯的名稱，則會傳回列舉中所定義的第一個名稱。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
