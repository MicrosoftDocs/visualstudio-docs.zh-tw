---
title: "IDebugSymbolProvider::GetNamespacesUsedAtAddress |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugSymbolProvider::GetNamespacesUsedAtAddress
helpviewer_keywords: IDebugSymbolProvider::GetNamespacesUsedAtAddress method
ms.assetid: 392de54b-9af0-4567-953b-1b41acd1e05c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ca03fd4430c3cfcb9474cfd4c420ec5ab560aa94
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugsymbolprovidergetnamespacesusedataddress"></a>IDebugSymbolProvider::GetNamespacesUsedAtAddress
這個方法會建立與偵錯位址相關聯的命名空間的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetNamespacesUsedAtAddress(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int GetNamespacesUsedAtAddress(  
   IDebugAddress        pAddress,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pAddress`  
 [in]偵錯的位址。  
  
 `ppEnum`  
 [out]傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)命名空間的列舉值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 可能有數個與指定的偵錯位址，例如，相關聯的命名空間的命名空間或多個巢狀`using`陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)