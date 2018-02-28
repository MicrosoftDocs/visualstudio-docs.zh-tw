---
title: "ICanHandleException::CanHandleException |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ICanHandleException.CanHandleException
apilocation:
- scrobj.dll
helpviewer_keywords:
- ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15612330f160f694202bb2158f970e0633fe53bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
決定是否指令碼引擎的呼叫端可以處理指定的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pExcepInfo`  
 [in]指標`EXCEPINFO`結構，其中包含找到任何例外狀況處理常式會報告的資訊。  
  
 `pvar`  
 [in]與例外狀況，例如，所擲回的值相關聯的值`throw`陳述式。 此參數可以是 `NULL`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|呼叫端可以處理的例外狀況|  
|`E_FAIL`|呼叫端無法處理此例外狀況。|  
  
## <a name="remarks"></a>備註  
 如果呼叫`IDispatchEx::InvokeEx`，或類似的方法，會導致例外狀況，支援的指令碼的呼叫鏈結中的呼叫端的指令碼引擎檢查`ICanHandleException`介面，並表示它可以處理此例外狀況。 如果沒有呼叫端可以處理的例外狀況，便會中止指令碼引擎。  
  
## <a name="see-also"></a>另請參閱  
 [ICanHandleException 介面](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)