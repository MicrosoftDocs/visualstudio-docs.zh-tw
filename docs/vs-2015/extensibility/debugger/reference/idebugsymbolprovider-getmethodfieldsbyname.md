---
title: IDebugSymbolProvider：： GetMethodFieldsByName |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName
helpviewer_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName method
ms.assetid: 1f781320-81ef-4037-b068-f1864b271258
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eb26d7382c9c501a1c3235153c2364b2a3e677fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421171"
---
# <a name="idebugsymbolprovidergetmethodfieldsbyname"></a>IDebugSymbolProvider::GetMethodFieldsByName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法會取得代表完整方法名稱的欄位。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetMethodFieldsByName(   
   LPCOLESTR          pszFullName,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int GetMethodFieldsByName(  
   string               pszFullName,   
   NAME_MATCH           nameMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszFullName`  
 在方法名稱。  
  
 `nameMatch`  
 在選取相符的類型，例如區分大小寫。  
  
 `ppEnum`  
 擴展傳回與這個方法相關聯之欄位的 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 列舉值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 例如，如果多個欄位有多載，則方法可以與多個欄位相關聯。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
