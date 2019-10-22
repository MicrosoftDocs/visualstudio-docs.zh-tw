---
title: IDebugStackFrame：： GetLanguageString |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetLanguageString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetLanguageString
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83abb038cd8bc018d84cd0c5ddd2a413f8a02248
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576762"
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
傳回語言的簡短或長文字描述。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fLong`  
 在旗標，其中 `TRUE` 會傳回完整的描述，而 `FALSE` 會傳回簡短的描述。  
  
 `pbstrLanguage`  
 脫銷語言的描述。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 一般來說，如果 `FALSE` `fLong`，這個方法只會提供與堆疊框架相關聯的語言名稱。 當 `fLong` `TRUE` 時，這個方法可能會提供完整的產品描述。  
  
## <a name="see-also"></a>請參閱  
 [IDebugStackFrame 介面](../../winscript/reference/idebugstackframe-interface.md)