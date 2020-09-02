---
title: IDebugBinder3：： FindAlias |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47aaaec73d2c364e974b7430335404bf8caf406c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68142968"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法會在指定名稱的情況下尋找別名。 這會搜尋程式中的所有別名。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcstrName`  
 在要尋找的別名名稱。  
  
 `ppAlias`  
 擴展如果 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 介面所代表的任何) ，就會找到別名 (。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則 `S_FALSE` 會傳回 (如果找不到別名) 或錯誤碼。  
  
## <a name="remarks"></a>備註  
 在呼叫之前，這個方法會將目的地物件初始化為 null：然後，它會在之後測試是否有 null 值，以判斷是否找到別名。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
