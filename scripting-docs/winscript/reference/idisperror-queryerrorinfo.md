---
title: IDispError：： QueryErrorInfo |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.QueryErrorInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::QueryErrorInfo
ms.assetid: e7e71a14-77e2-4331-9ffc-1dace041fa84
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ccfcb020faf25fbe1723a384ff08aefcf55b56d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573085"
---
# <a name="idisperrorqueryerrorinfo"></a>IDispError::QueryErrorInfo
抓取特定類型的錯誤資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT QueryErrorInfo(  
   GUID  guidErrorType,  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>參數  
 `guidErrorType`  
 在指定錯誤類型的 GUID。  
  
 `ppde`  
 脫銷指定 IDispError 物件。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 @No__t_0 方法會抓取特定類型的錯誤資訊。  
  
> [!NOTE]
> 這個方法尚未實作。  
  
## <a name="see-also"></a>請參閱  
 [IDispError 介面](../../winscript/reference/idisperror-interface.md)