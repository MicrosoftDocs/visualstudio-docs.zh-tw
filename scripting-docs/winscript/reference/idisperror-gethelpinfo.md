---
title: IDispError::GetHelpInfo | Microsoft Docs
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
ms.openlocfilehash: fa831ff511ea507e03ca858b93383ff38ead9039
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446906"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
傳回說明檔路徑，以及說明錯誤，可能的話，本主題的內容識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrFileName`  
 [out]字串，包含說明檔的完整的路徑。 如果沒有說明檔或發生錯誤，則傳回的值會是 NULL。  
  
 `pdwContext`  
 [out]錯誤的說明內容識別碼。 如果沒有說明檔 (如果`pbstrFileName`是 NULL)，此參數沒有任何意義。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|發生提供者特定錯誤。|  
|`E_INVALIDARG`|`pbstrFileName` 或`pdwContext`是 NULL。|  
|`E_OUTOFMEMORY`|提供者無法配置足夠的記憶體，在其中傳回的說明檔案的路徑。|  
  
## <a name="remarks"></a>備註  
 這個方法傳回的說明檔路徑，以及說明錯誤，可能的話，本主題的內容識別碼。  
  
> [!NOTE]
> 這個方法尚未實作。  
  
## <a name="see-also"></a>另請參閱  
 [IDispError 介面](../../winscript/reference/idisperror-interface.md)