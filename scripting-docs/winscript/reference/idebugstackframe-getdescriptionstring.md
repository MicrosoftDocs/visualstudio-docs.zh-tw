---
title: IDebugStackFrame：： GetDescriptionString |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetDescriptionString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetDescriptionString
ms.assetid: a2ddc069-c440-4dee-98dc-ab7c78773b94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7eb29574d240a02073721046cec65bdf483b3eb0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576751"
---
# <a name="idebugstackframegetdescriptionstring"></a>IDebugStackFrame::GetDescriptionString
傳回堆疊框架的簡短或長文字描述。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fLong`  
 在旗標，其中 `TRUE` 會傳回完整的描述，而 `FALSE` 會傳回簡短的描述。  
  
 `pbstrDescription`  
 脫銷堆疊框架的描述。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 一般來說，如果 `FALSE` `fLong`，這個方法只會提供與堆疊框架相關聯之函式的名稱。 當 `fLong` `TRUE` 時，這個方法也可以提供函式參數和其他相關資訊。  
  
## <a name="see-also"></a>請參閱  
 [IDebugStackFrame 介面](../../winscript/reference/idebugstackframe-interface.md)