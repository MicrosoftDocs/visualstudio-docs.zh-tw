---
title: IDebugApplication：： AddGlobalExpressionCoNtextProvider |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.AddGlobalExpressionContextProvider
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::AddGlobalExpressionContextProvider
ms.assetid: 35db7124-6970-4e45-8f00-ecdf21e9f5cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 429e87def1e17a6abac92ce2d3538960659cfaeb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573467"
---
# <a name="idebugapplicationaddglobalexpressioncontextprovider"></a>IDebugApplication::AddGlobalExpressionContextProvider
將全域運算式內容提供者加入此應用程式。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT AddGlobalExpressionContextProvider(  
   IProvideExpressionContexts*  pdsfs,  
   DWORD_PTR*                   pdwCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdsfs`  
 在要加入此應用程式的全域內容提供者。  
  
 `pdwCookie`  
 脫銷用來從應用程式移除這個全域運算式內容提供者的 cookie。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會將全域運算式內容提供者加入此應用程式。  
  
## <a name="see-also"></a>請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)