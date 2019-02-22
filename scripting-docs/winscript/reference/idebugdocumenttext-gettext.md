---
title: IDebugDocumentText::GetText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 77cc255bcd04754cbfde4638b67a85f6fdc0a922
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091984"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
擷取字元和/或字元相關聯的屬性中的字元位置範圍。  
  
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
 [in]開始位置的字元位置範圍。  
  
 `pcharText`  
 [in、 out]字元的文字緩衝。 緩衝區必須夠大，無法保存`cMaxChars`字元。 如果此參數為 NULL，此方法沒有傳回字元。  
  
 `pstaTextAttr`  
 [in、 out]字元屬性緩衝區。 緩衝區必須夠大，無法保存`cMaxChars`字元。 如果此參數為 NULL，此方法沒有傳回屬性。  
  
 `pcNumChars`  
 [in、 out]傳回字元/屬性數目。 這個參數必須設定為零之前呼叫這個方法。  
  
 `cMaxChars`  
 [in]字元位置範圍中的字元數。 也會指定要傳回字元的數目上限。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會擷取字元和/或字元相關聯的屬性中的字元位置範圍。 字元位置和字元數所指定的字元位置範圍。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE_TEXT_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)