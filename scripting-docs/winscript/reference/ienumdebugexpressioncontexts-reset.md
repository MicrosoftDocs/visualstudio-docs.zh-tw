---
title: IEnumDebugExpressionCoNtexts：： Reset |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExpressionContexts.Reset
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugExpressionContexts::Reset
ms.assetid: b471954f-d3b5-4c99-88e1-1de3e3f72c7f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c86f7095cb242f96737e4744f5056f9fb36d384
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577133"
---
# <a name="ienumdebugexpressioncontextsreset"></a>IEnumDebugExpressionContexts::Reset
將列舉序列重設為開頭。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法不接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會將列舉序列重設為開頭。  
  
## <a name="see-also"></a>請參閱  
 [IEnumDebugExpressionContexts 介面](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)