---
title: IDispError：： GetHelpInfo |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHelpInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a84e57e97bb781ad3ea0be1ac6766fd94f6f5c30
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573129"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
如果可能的話，會傳回說明檔的路徑，以及描述錯誤之主題的內容識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrFileName`  
 脫銷包含說明檔完整路徑的字串。 如果沒有說明檔或發生錯誤，則傳回值為 Null。  
  
 `pdwContext`  
 脫銷錯誤的說明內容識別碼。 如果沒有說明檔（如果 `pbstrFileName` 為 Null），則此參數沒有意義。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|發生提供者特定的錯誤。|  
|`E_INVALIDARG`|`pbstrFileName` 或 `pdwContext` 是 Null。|  
|`E_OUTOFMEMORY`|提供者無法配置足夠的記憶體來傳回說明檔路徑。|  
  
## <a name="remarks"></a>備註  
 如果可能的話，這個方法會傳回說明檔的路徑，以及描述錯誤之主題的內容識別碼。  
  
> [!NOTE]
> 這個方法尚未實作。  
  
## <a name="see-also"></a>請參閱  
 [IDispError 介面](../../winscript/reference/idisperror-interface.md)