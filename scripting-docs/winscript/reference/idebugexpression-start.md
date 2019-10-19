---
title: IDebugExpression：： Start |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Start
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Start
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c8c3666adfc83f3ad60b942cd3f7fe9eedfccba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576435"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
開始評估運算式。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdecb`  
 在回呼，表示運算式評估完成的時間。 如果 `NULL` 此參數，則不會引發任何事件，而且用戶端必須使用 `QueryIsComplete` 輪詢運算式狀態。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會開始評估運算式。  
  
## <a name="see-also"></a>請參閱  
 [IDebugExpression：： Abort](../../winscript/reference/idebugexpression-abort.md)    
 [IDebugExpression 介面](../../winscript/reference/idebugexpression-interface.md)