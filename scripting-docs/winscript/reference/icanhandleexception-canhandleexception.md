---
title: ICanHandleException：： CanHandleException |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ICanHandleException.CanHandleException
apilocation:
- scrobj.dll
helpviewer_keywords:
- ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c536d35dcb9f0faca8b033ecd39aec520a2e260a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575714"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
判斷腳本引擎的呼叫端是否可以處理指定的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pExcepInfo`  
 在@No__t_0 結構的指標，其中包含如果找不到例外狀況處理常式時，將會報告的資訊。  
  
 `pvar`  
 在與例外狀況相關聯的值，例如 `throw` 語句所擲回的值。 此參數可以是 `NULL`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|呼叫端可以處理例外狀況|  
|`E_FAIL`|呼叫端無法處理例外狀況。|  
  
## <a name="remarks"></a>備註  
 如果 `IDispatchEx::InvokeEx` 的呼叫或類似的方法導致例外狀況，則腳本引擎會檢查腳本的呼叫端鏈中是否有支援 `ICanHandleException` 介面的呼叫者，並指出它可以處理例外狀況。 如果沒有呼叫端可以處理例外狀況，腳本引擎就會停止。  
  
## <a name="see-also"></a>請參閱  
 [ICanHandleException 介面](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)