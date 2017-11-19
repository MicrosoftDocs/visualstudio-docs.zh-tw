---
title: "IDebugExpression::GetResultAsString |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExpression.GetResultAsString
apilocation: jscript.dll
helpviewer_keywords: IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 557fe65859d1e3046d64884982070ad233e12559
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
傳回運算式評估為字串和作業的傳回值的結果。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `phrResult`  
 [out]作業的傳回值。  
  
 `pbstrResult`  
 [out]運算式評估的結果。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_PENDING`|作業仍然是暫止。|  
  
## <a name="remarks"></a>備註  
 這個方法傳回的運算式評估為字串和作業的結果`HRESULT`。  
  
 這個方法會傳回`S_OK`和`phrResult`傳回`E_ABORT`如果`Abort`中止作業。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExpression 介面](../../winscript/reference/idebugexpression-interface.md)