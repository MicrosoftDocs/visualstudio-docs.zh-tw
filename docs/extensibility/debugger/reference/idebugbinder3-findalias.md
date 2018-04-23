---
title: IDebugBinder3::FindAlias |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e68038f6e00c2a04f4c96f5f9d93fc4919d2fd09
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
這個方法會找出的指定名稱的別名。 這會在程式中搜尋所有別名。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcstrName`  
 [in]若要尋找的別名名稱。  
  
 `ppAlias`  
 [out]找到 （如果有的話） 別名由[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`（如果找不到別名） 或錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會初始化為 null，然後再呼叫; 的目的地物件然後它會測試之後若要判斷已找到別名有 null 值。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)