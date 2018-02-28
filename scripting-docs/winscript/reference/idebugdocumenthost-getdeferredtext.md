---
title: "IDebugDocumentHost::GetDeferredText |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHost.GetDeferredText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ace3bdbfef143a3307d81455788a1e81788cb50b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
傳回已加入使用的字元範圍`IDebugDocumentHelper::AddDeferredText`方法，在原始的主機文件。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in]主應用程式定義的 cookie，表示文字的開始位置。  
  
 `pcharText`  
 [in、 out]字元的文字緩衝。 這個方法不會傳回字元，如果這個參數是`NULL`。  
  
 `pstaTextAttr`  
 [in、 out]字元屬性緩衝區。 這個方法不會傳回屬性，如果這個參數是`NULL`。  
  
 `pcNumChars`  
 [in、 out]表示傳回的字元/屬性的實際數目。 這個參數必須設定為零之前呼叫這個方法。  
  
 `cMaxChars`  
 [in]要傳回的字元數目上限。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|未實作方法。|  
  
## <a name="remarks"></a>備註  
 這個方法可能會傳回`E_NOTIMPL`，如果主機不會呼叫`IDebugDocumentHelper::AddDeferredText`。  
  
> [!NOTE]
>  這個方法會傳回原始文件的文字。 主機不會不追蹤的編輯或文件的其他變更。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentHost 介面](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE_TEXT_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)