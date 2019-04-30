---
title: IActiveScriptDebug::EnumCodeContextsOfPosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::EnumCodeContextsOfPosition
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c364d00941a65272b4d22cc7674a0f0e6178f099
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009738"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
智慧主機用來委派`IDebugDocumentContext::EnumCodeContexts`方法。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwSourceContext`  
 [in]來源內容提供給`IActiveScriptParse::ParseScriptText`或`IActiveScriptParse::AddScriptlet`。  
  
 `uCharacterOffset`  
 [in]相對於指令碼文字開頭位移的字元。  
  
 `uNumChars`  
 [in]在此內容中的字元數。  
  
 `ppescc`  
 [out]指定的範圍內的程式碼內容列舉值。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 智慧主機會使用這個方法來委派`IDebugDocumentContext::EnumCodeContexts`方法。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptDebug 介面](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)