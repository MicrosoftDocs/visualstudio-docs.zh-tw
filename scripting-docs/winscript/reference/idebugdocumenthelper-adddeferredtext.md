---
title: IDebugDocumentHelper：： AddDeferredText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDeferredText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1aae73e44059b1f07fa4cb54f40cdcd12e564a8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577046"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
通知 helper，指定的文字可以使用，但未提供字元。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cChars`  
 在要加入的（Unicode）字元數。  
  
 `dwTextStartCookie`  
 在主機定義的 cookie，代表文字的開始位置。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|方法失敗。|  
  
## <a name="remarks"></a>備註  
 這個方法可讓主機延後提供要新增的字元，直到需要它們為止，同時允許 helper 產生精確的通知和大小資訊。 @No__t_0 參數是由主機定義的 cookie，代表文字的開始位置。 後續對 `IDebugDocumentText::GetText` 的呼叫必須提供此 cookie。 例如，在代表 DBCS 中文字的主控制項中，cookie 可以是位元組位移。  
  
 假設 `IDebugDocumentText::GetText` 的單一呼叫可以從 `AddDeferredText` 的多個呼叫中取得字元。 Helper 類別也可能會要求超過一次相同的延後字元範圍。  
  
> [!NOTE]
> @No__t_0 的呼叫不應該與 `AddUnicodeText` 或 `AddDBCSText` 的呼叫混合使用。 如果發生這種情況，則會傳回 `E_FAIL`。  
  
## <a name="see-also"></a>請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper：： AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)    
 [IDebugDocumentHelper：： AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)    
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)