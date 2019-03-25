---
title: IEnumDebugExpressionContexts::Reset | Microsoft Docs
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
ms.openlocfilehash: 88e6a66f560e778297658a63244eb510967101f2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148083"
---
# <a name="ienumdebugexpressioncontextsreset"></a>IEnumDebugExpressionContexts::Reset
將列舉型別序列重設到開頭。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會將列舉型別序列重設開頭。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugExpressionContexts 介面](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)