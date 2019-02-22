---
title: IDebugExpression::GetResultAsDebugProperty |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsDebugProperty
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aebe983c33416d1c3d12d18c272fd1e4de27467
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093102"
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
傳回做為偵錯屬性和作業的傳回值的運算式評估的結果。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>參數  
 `phrResult`  
 [out]作業的傳回值。  
  
 `ppdp`  
 [out]運算式 [偵錯] 屬性中。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_PENDING`|此作業仍然是暫止。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回做為運算式評估的結果`IDebugProperty`和作業的`HRESULT`。  
  
 這個方法會傳回`S_OK`並`phrResult`會傳回`E_ABORT`如果`Abort`中止作業。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExpression 介面](../../winscript/reference/idebugexpression-interface.md)   
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)