---
title: IDebugApplication：： RemoveGlobalExpressionCoNtextProvider |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.RemoveGlobalExpressionContextProvider
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::RemoveGlobalExpressionContextProvider
ms.assetid: ace638a3-ed34-4d20-8404-45c684aaaf1a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4b948cea02d696b6c176e925adf9c95913be2cd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571148"
---
# <a name="idebugapplicationremoveglobalexpressioncontextprovider"></a>IDebugApplication::RemoveGlobalExpressionContextProvider
移除這個應用程式中的全域運算式內容提供者。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT RemoveGlobalExpressionContextProvider(  
   DWORD_PTR  dwCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwCookie`  
 在加入全域內容提供者時，`AddGlobalExpressionContextProvider` 方法傳回的 cookie。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 `RemoveGlobalExpressionContextProvider` 方法會移除此應用程式中的全域運算式內容提供者。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication：： AddGlobalExpressionCoNtextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)   
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)