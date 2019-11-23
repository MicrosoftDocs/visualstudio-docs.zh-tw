---
title: IDispError：： GetDescription |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetDescription
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetDescription
ms.assetid: 04deaea6-0265-4e34-952e-634edba0e923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d1bb1c3516c2601707e1a0bcd69f4f8409514fe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573150"
---
# <a name="idisperrorgetdescription"></a>IDispError::GetDescription
傳回錯誤的文字描述。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDescription(  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrDescription`  
 脫銷包含錯誤簡短描述的字串。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 文字會以地區設定識別碼（LCID）所指定的語言傳回，而該識別元會傳遞給發生錯誤之方法的 `IDispatchEx::InvokeEx`。  
  
> [!NOTE]
> 這個方法尚未實作。  
  
## <a name="see-also"></a>另請參閱  
 [IDispError 介面](../../winscript/reference/idisperror-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)