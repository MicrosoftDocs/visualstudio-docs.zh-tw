---
title: IDebugDocumentHelper：： SetTextAttributes |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetTextAttributes
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetTextAttributes
ms.assetid: 31657738-9e4c-436a-be61-23f4185d452e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cc5e5955652fd8b59d4c502e68d97a729ded141
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569468"
---
# <a name="idebugdocumenthelpersettextattributes"></a>IDebugDocumentHelper::SetTextAttributes
設定文字範圍的屬性，覆寫該文字上的其他屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetTextAttributes(  
   ULONG              ulCharOffset,  
   ULONG              cChars,  
   SOURCE_TEXT_ATTR*  pstaTextAttr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ulCharOffset`  
 在文字範圍開頭的位置。  
  
 `cChars`  
 在範圍中的字元數。  
  
 `pstaTextAttr`  
 在文字範圍的來源文字屬性。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 在將文字加入檔之前，先在文字範圍上呼叫 `SetTextAttributes` 是錯誤的。 呼叫 `AddDBCSText`、`AddUnicodeText`或 `AddDeferredText` 方法，將文字新增至檔。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper：： AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper：： AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper：： AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE_TEXT_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)