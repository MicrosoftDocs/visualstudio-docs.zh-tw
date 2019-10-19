---
title: IDebugDocumentHost：： GetDeferredText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetDeferredText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 273b4eb52b7263d34c347dff3a00479945b809df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569432"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
傳回在原始主控制項檔中，使用 `IDebugDocumentHelper::AddDeferredText` 方法新增的字元範圍。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwTextStartCookie`  
 在主機定義的 cookie，代表文字的開始位置。  
  
 `pcharText`  
 [in、out]字元文本緩衝區。 如果 `NULL` 此參數，則這個方法不會傳回字元。  
  
 `pstaTextAttr`  
 [in、out]字元屬性緩衝區。 如果 `NULL` 此參數，則這個方法不會傳回屬性。  
  
 `pcNumChars`  
 [in、out]表示傳回的實際字元/屬性數目。 呼叫這個方法之前，必須將這個參數設定為零。  
  
 `cMaxChars`  
 在要傳回的最大字元數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|未執行方法。|  
  
## <a name="remarks"></a>備註  
 如果主機未呼叫 `IDebugDocumentHelper::AddDeferredText`，這個方法可能會傳回 `E_NOTIMPL`。  
  
> [!NOTE]
> 這個方法會傳回原始檔案中的文字。 主機不會追蹤檔的編輯或其他變更。  
  
## <a name="see-also"></a>請參閱  
 [IDebugDocumentHost 介面](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper：： AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [SOURCE_TEXT_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)