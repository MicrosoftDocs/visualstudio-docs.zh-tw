---
title: IEnumDebugExpressionCoNtexts：： Next |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExpressionContexts.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugExpressionContexts::Next
ms.assetid: aa223b0b-f7c1-4368-a59e-677e60133baf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95314c7497a9b11be51d1e64df0310323300d281
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577154"
---
# <a name="ienumdebugexpressioncontextsnext"></a>IEnumDebugExpressionContexts::Next
抓取列舉序列中指定數目的區段。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Next(  
   ULONG                      celt,  
   IDebugExpressionContext**  ppdec,  
   ULONG*                     pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 在要取出的區段數目。  
  
 `ppdec`  
 脫銷傳回 `IDebugExpressionContext` 介面的陣列，表示要抓取的區段。  
  
 `pceltFetched`  
 脫銷列舉值所提取的實際區段數目。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會抓取列舉序列中指定數目的區段。  
  
## <a name="see-also"></a>請參閱  
 [IEnumDebugExpressionContexts 介面](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)