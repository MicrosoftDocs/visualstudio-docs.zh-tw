---
title: IDebugEnumField：： GetValueFromString |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188946"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法會傳回與列舉常數名稱相關聯的值。  
  
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
 在字串，指定要取得其值的名稱。 請注意，在 c + + 中，這是寬字元字串。  
  
 `pValue`  
 擴展傳回相關聯的數值。  
  
## <a name="return-value"></a>傳回值  
 如果成功， `S_OK` 則傳回; 否則， `S_FALSE` 如果名稱不是列舉的一部分或錯誤碼，則會傳回。  
  
## <a name="remarks"></a>備註  
 這個方法會區分大小寫。 如果需要不區分大小寫的搜尋 (例如，在 Visual Basic 名稱不區分大小寫) 的語言中，請使用 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
