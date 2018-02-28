---
title: "IDebugDocumentText::GetText |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentText.GetText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a1006304974fab4959ad6313ffdc26793cdd345
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
擷取字元和/或字元屬性，與字元位置範圍相關聯。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cCharacterPosition`  
 [in]開始位置的字元位置範圍。  
  
 `pcharText`  
 [in、 out]字元的文字緩衝。 緩衝區的大小必須足夠容納`cMaxChars`字元。 這個參數是 NULL，如果方法沒有傳回的字元。  
  
 `pstaTextAttr`  
 [in、 out]字元屬性緩衝區。 緩衝區的大小必須足夠容納`cMaxChars`字元。 如果這個參數是 NULL，方法就不會傳回屬性。  
  
 `pcNumChars`  
 [in、 out]傳回的字元/屬性數目。 這個參數必須設定為零之前呼叫這個方法。  
  
 `cMaxChars`  
 [in]中的字元位置範圍的字元數。 也會指定要傳回字元的數目上限。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會擷取字元及/或字元屬性，與字元位置範圍相關聯。 字元位置範圍是由字元位置和指定的字元數。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE_TEXT_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)