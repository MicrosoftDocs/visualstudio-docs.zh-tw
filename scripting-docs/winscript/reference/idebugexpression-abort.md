---
title: IDebugExpression::Abort |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Abort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Abort
ms.assetid: dbdb63c1-6c4a-4cef-bb40-1843495ae167
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 244713cad3cbc67776bd55d657842d0ca70139dd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726518"
---
# <a name="idebugexpressionabort"></a>IDebugExpression::Abort
停止運算式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會採用任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會停止儘早運算式評估。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExpression 介面](../../winscript/reference/idebugexpression-interface.md)   
 [IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)