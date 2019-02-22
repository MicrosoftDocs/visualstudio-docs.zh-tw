---
title: IDebugEnumField::GetValueFromString |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe0947158a93885278b2dbd4191d5ebb169aecee
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987930"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
這個方法傳回的列舉常數名稱相關聯的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromString(  
   string    pszValue,  
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszValue`  
 [in]字串，指定要取值的名稱。 請注意，對於 c + +，這是寬字元字串。  
  
 `pValue`  
 [out]傳回相關聯的數值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`，如果名稱不屬於列舉型別，則為錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會區分大小寫。 如果需要的不區分大小寫的搜尋時 （例如，在 Visual Basic 名稱不區分大小寫之類的語言），使用[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)