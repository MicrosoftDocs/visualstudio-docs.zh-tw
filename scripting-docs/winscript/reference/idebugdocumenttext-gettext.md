---
title: IDebugDocumentText：： GetText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6472c40802fff4dad6e5ecc8f2729c95459e09f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572076"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
抓取字元和（或）與字元位置範圍相關聯的字元屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
 在字元位置範圍的開始位置。  
  
 `pcharText`  
 [in、out]字元文本緩衝區。 緩衝區必須夠大，才能容納 `cMaxChars` 個字元。 如果此參數為 Null，則方法不會傳回字元。  
  
 `pstaTextAttr`  
 [in、out]字元屬性緩衝區。 緩衝區必須夠大，才能容納 `cMaxChars` 個字元。 如果此參數為 Null，則方法不會傳回屬性。  
  
 `pcNumChars`  
 [in、out]傳回的字元/屬性數目。 呼叫這個方法之前，必須將這個參數設定為零。  
  
 `cMaxChars`  
 在字元位置範圍中的字元數。 也會指定要傳回的最大字元數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會抓取字元和（或）與字元位置範圍相關聯的字元屬性。 字元位置範圍是由字元位置和數個字元所指定。  
  
## <a name="see-also"></a>請參閱  
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE_TEXT_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)