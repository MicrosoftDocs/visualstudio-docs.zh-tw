---
title: IDebugDocumentHelper::AddDeferredText |Microsoft 文件
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
ms.openlocfilehash: c92909874429075bebc6a1f0a252573d049584e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728538"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
指定的文字，但不提供字元會告知協助專家。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cChars`  
 [in]若要加入 (Unicode) 字元數。  
  
 `dwTextStartCookie`  
 [in]主應用程式定義的 cookie，表示文字的開始位置。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|此方法失敗。|  
  
## <a name="remarks"></a>備註  
 這個方法可讓主應用程式延後提供的字元加入，直到所需之同時允許協助專家產生精確的通知和大小資訊。 `dwTextStartCookie`參數會以 cookie，由主應用程式，代表文字的開始位置。 後續呼叫`IDebugDocumentText::GetText`必須提供此 cookie。 例如，在主控件，表示文字在 DBCS 中的，cookie 可能是位元組位移。  
  
 假設的單一呼叫`IDebugDocumentText::GetText`可以取得字元從多次呼叫`AddDeferredText`。 協助程式類別可能也會要求的相同字元範圍的延後一次以上。  
  
> [!NOTE]
>  呼叫`AddDeferredText`不應混用呼叫`AddUnicodeText`或`AddDBCSText`。 如果發生這種情況，`E_FAIL`傳回。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)