---
title: IDebugEnumField::GetValueFromString |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f553b7f019dd89af771e057a46a11b1affed1308
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188946"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法傳回的列舉常數名稱相關聯的值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in]字串，指定要取值的名稱。 請注意，針對C++，這是寬字元字串。  
  
 `pValue`  
 [out]傳回相關聯的數值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`，如果名稱不屬於列舉型別，則為錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會區分大小寫。 如果需要的不區分大小寫的搜尋時 （例如，在 Visual Basic 名稱不區分大小寫之類的語言），使用[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
