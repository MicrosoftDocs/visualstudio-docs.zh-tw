---
title: Adddeferredtext |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ba6f945e6c7fa4df83a5e301d73b3fc0bb9da92b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096079"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
指定的文字可用，但它不提供的字元，請告知協助專家。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cChars`  
 [in]若要新增的 (Unicode) 字元數。  
  
 `dwTextStartCookie`  
 [in]主應用程式定義的 cookie，代表文字的開始位置。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|方法失敗。|  
  
## <a name="remarks"></a>備註  
 這個方法可讓主應用程式延後提供的字元加入，直到它們所需，同時允許協助專家產生精確的通知和大小資訊。 `dwTextStartCookie`參數是 cookie 中，定義由主應用程式，表示文字的開始位置。 後續呼叫`IDebugDocumentText::GetText`必須提供此 cookie。 比方說，在主應用程式在 DBCS 中的文字表示，cookie 可能是位元組位移。  
  
 它假設呼叫一次`IDebugDocumentText::GetText`可以從多個呼叫中取得字元`AddDeferredText`。 協助程式類別可能也會要求針對相同的延後的字元範圍一次以上。  
  
> [!NOTE]
>  若要呼叫`AddDeferredText`不應混用來呼叫`AddUnicodeText`或`AddDBCSText`。 如果發生這種情況，`E_FAIL`會傳回。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Idebugdocumenthelper:: Addunicodetext](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [Idebugdocumenthelper:: Adddbcstext](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)