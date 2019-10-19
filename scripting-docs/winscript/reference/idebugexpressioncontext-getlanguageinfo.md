---
title: IDebugExpressionCoNtext：： GetLanguageInfo |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.GetLanguageInfo
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::GetLanguageInfo
ms.assetid: 35e25662-0b2a-4c3f-bce4-f01726bc04a8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e6dd3d3bb254cd91f411da3b6b587bc37c3a777
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576402"
---
# <a name="idebugexpressioncontextgetlanguageinfo"></a>IDebugExpressionContext::GetLanguageInfo
傳回擁有此內容之語言的名稱和 GUID。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetLanguageInfo(  
   BSTR*  pbstrLanguageName,  
   GUID*  pLanguageID  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrLanguageName`  
 脫銷語言的名稱。  
  
 `pLanguageID`  
 脫銷語言的唯一識別碼。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回擁有此內容之語言的名稱和 GUID。  
  
## <a name="see-also"></a>請參閱  
 [IDebugExpressionContext 介面](../../winscript/reference/idebugexpressioncontext-interface.md)