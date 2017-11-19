---
title: "IDebugBinder3::FindAlias |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3::FindAlias
helpviewer_keywords: IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f209829e3b6c76571a53370c11c6d6d7343b088c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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