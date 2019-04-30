---
title: IActiveScriptSiteDebug32::GetDocumentContextFromPosition |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9a52abcfa4defb49526f944469c95a2247f5d85c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992521"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
語言引擎用來委派`IDebugCodeContext::GetSourceContext`。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwSourceContext`  
 [in]來源內容提供給`ParseScriptText`或`AddScriptlet`。  
  
 `uCharacterOffset`  
 [in]相對於指令碼區塊的程式碼片段的開頭位移的字元。  
  
 `uNumChars`  
 [in]在此內容中的字元數。  
  
 `ppsc`  
 [out]文件內容對應至這個字元位置範圍。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 語言引擎會使用這個方法來委派`IDebugCodeContext::GetSourceContext`。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSiteDebug32 介面](../../winscript/reference/iactivescriptsitedebug32-interface.md)