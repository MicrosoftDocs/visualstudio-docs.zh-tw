---
title: IDispError::GetHresult |Microsoft Docs
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
ms.openlocfilehash: 6eb4518e39fdab432590601d91b462d869c38e1a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446896"
---
# <a name="idisperrorgethresult"></a>IDispError::GetHresult
擷取的錯誤程式碼`IDispError`物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetHresult(  
   HRESULT*  phr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `phr`  
 [out]指定的錯誤碼。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會擷取來自錯誤碼`IDispError`物件。  
  
> [!NOTE]
> 這個方法尚未實作。  
  
## <a name="see-also"></a>另請參閱  
 [IDispError 介面](../../winscript/reference/idisperror-interface.md)