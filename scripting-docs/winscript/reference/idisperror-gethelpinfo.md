---
title: "IDispError::GetHelpInfo |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDispError.GetHelpInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17098b4055bb61e9a2f639404edfe2214abc931e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
傳回說明檔的路徑和盡可能說明此錯誤，該主題的內容識別碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrFileName`  
 [out]字串，包含說明檔的完整的路徑。 如果沒有說明檔，或發生錯誤，則傳回值是 NULL。  
  
 `pdwContext`  
 [out]錯誤的說明內容識別碼。 如果沒有說明檔 (如果`pbstrFileName`是 NULL)，此參數沒有任何意義。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|發生提供者特定錯誤。|  
|`E_INVALIDARG`|`pbstrFileName`或`pdwContext`是 null。|  
|`E_OUTOFMEMORY`|提供者無法配置足夠的記憶體，這是要傳回的說明檔案的路徑中。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回說明檔路徑，以及盡可能說明此錯誤，該主題的內容識別碼。  
  
> [!NOTE]
>  這個方法尚未實作。  
  
## <a name="see-also"></a>另請參閱  
 [IDispError 介面](../../winscript/reference/idisperror-interface.md)