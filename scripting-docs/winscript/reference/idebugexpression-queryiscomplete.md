---
title: IDebugExpression::QueryIsComplete |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.QueryIsComplete
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::QueryIsComplete
ms.assetid: 510d62e5-a316-46fb-b23f-d3ba902b295c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0b4fa4b027f0ee8d848f52c063cbfd1f7679d4a6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087148"
---
# <a name="idebugexpressionqueryiscomplete"></a>IDebugExpression::QueryIsComplete
判斷作業是否完成。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|此方法成功，並表示作業已完成。|  
|`S_FALSE`|此作業仍然是暫止。|  
  
## <a name="remarks"></a>備註  
 這個方法會判斷作業是否完成。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExpression 介面](../../winscript/reference/idebugexpression-interface.md)