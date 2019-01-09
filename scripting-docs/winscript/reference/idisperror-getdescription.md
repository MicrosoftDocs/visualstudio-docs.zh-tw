---
title: IDispError::GetDescription |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: fa0c837be9a98829551b9c7820faf154779479e4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096950"
---
# <a name="idisperrorgetdescription"></a>IDispError::GetDescription
傳回此錯誤的文字描述。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDescription(  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrDescription`  
 [out]字串，包含錯誤的簡短描述。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 文字會傳入的地區設定識別碼 (LCID) 傳遞給所指定的語言`IDispatchEx::InvokeEx`發生錯誤的方法。  
  
> [!NOTE]
>  這個方法尚未實作。  
  
## <a name="see-also"></a>另請參閱  
 [IDispError 介面](../../winscript/reference/idisperror-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)