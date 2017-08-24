---
title: IDebugBinder3::FindAlias | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 10
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
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: b4820228074cb4860480e447b836c59e9bbc427c
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
This method locates an alias, given a name. This will search all aliases in the program.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```cs  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pcstrName`  
 [in] Name of alias to find.  
  
 `ppAlias`  
 [out] Alias found (if any) represented by the [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interface.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns `S_FALSE` (if alias is not found) or an error code.  
  
## <a name="remarks"></a>Remarks  
 This method initializes the destination object to null before calling; then it tests for a null value afterward to determine whether or not the alias was found.  
  
## <a name="see-also"></a>See Also  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
