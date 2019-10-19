---
title: IDebugExpression：： GetResultAsString |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56b8f637744227763f55b7c024745d7ae4448b40
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573518"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
傳回運算式評估的結果做為字串和作業的傳回值。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `phrResult`  
 脫銷作業的傳回值。  
  
 `pbstrResult`  
 脫銷運算式評估的結果。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_PENDING`|作業仍在暫止狀態。|  
  
## <a name="remarks"></a>備註  
 這個方法會將運算式評估的結果當做字串和作業的 `HRESULT` 傳回。  
  
 這個方法會傳回 `S_OK`，而如果 `Abort` 中止作業，`phrResult` 會傳回 `E_ABORT`。  
  
## <a name="see-also"></a>請參閱  
 [IDebugExpression 介面](../../winscript/reference/idebugexpression-interface.md)