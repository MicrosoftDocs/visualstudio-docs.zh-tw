---
title: IDebugDocumentHelper::SetTextAttributes |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bef4ae1ccff730d6865e00174ec73e991245bd43
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096495"
---
# <a name="idebugdocumenthelpersettextattributes"></a>IDebugDocumentHelper::SetTextAttributes
在某個範圍的文字，覆寫對該文字其他屬性上設定的屬性。  
  
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
 [in]文字範圍的開始位置。  
  
 `cChars`  
 [in]範圍中的字元數。  
  
 `pstaTextAttr`  
 [in]來源文字的文字範圍的屬性。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 它會呼叫錯誤`SetTextAttributes`上該文字新增至文件之前的文字範圍。 呼叫`AddDBCSText`， `AddUnicodeText`，或`AddDeferredText`將文字加入文件的方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Idebugdocumenthelper:: Addunicodetext](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [Idebugdocumenthelper:: Adddbcstext](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [Adddeferredtext](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE_TEXT_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)