---
title: IDispError：： GetNext |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetNext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetNext
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81186e6eba7983a1210e5de5bca5d83dd77089da
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573100"
---
# <a name="idisperrorgetnext"></a>IDispError::GetNext
抓取下一個 `IDispError` 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppde`  
 脫銷指定下一個 `IDispError` 物件。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會抓取下一個 `IDispError` 物件。 如果這是最後一個 `IDispError` 物件，這個方法會傳回 Null。  
  
> [!NOTE]
> 這個方法尚未實作。  
  
## <a name="see-also"></a>請參閱  
 [IDispError 介面](../../winscript/reference/idisperror-interface.md)