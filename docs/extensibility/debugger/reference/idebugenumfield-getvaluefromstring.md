---
title: IDebugEnumField::GetValueFromString | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 9def9e56e0896d11c10bfebfd5c2defe3fb52da8
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
This method returns the value associated with the name of an enumeration constant.  
  
## <a name="syntax"></a>Syntax  
  
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
  
#### <a name="parameters"></a>Parameters  
 `pszValue`  
 [in] A string specifying the name for which to get the value. Note that for C++, this is a wide character string.  
  
 `pValue`  
 [out] Returns the associated numerical value.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns `S_FALSE`, if the name is not part of the enumeration, or an error code.  
  
## <a name="remarks"></a>Remarks  
 This method is case-sensitive. If a case-insensitive search is needed (for example, in a language such as Visual Basic where names are not case sensitive), use [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).  
  
## <a name="see-also"></a>See Also  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
