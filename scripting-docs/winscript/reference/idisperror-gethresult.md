---
title: IDispError：： GetHresult |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHresult
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHresult
ms.assetid: a14d566e-473f-497b-a2f9-85331433e6c9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62661e14c36881ca83763c277dbfd5385f192fb6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573121"
---
# <a name="idisperrorgethresult"></a>IDispError::GetHresult
抓取來自 `IDispError` 物件的錯誤碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetHresult(  
   HRESULT*  phr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `phr`  
 脫銷指定錯誤碼。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會從 `IDispError` 物件中抓取錯誤碼。  
  
> [!NOTE]
> 這個方法尚未實作。  
  
## <a name="see-also"></a>請參閱  
 [IDispError 介面](../../winscript/reference/idisperror-interface.md)