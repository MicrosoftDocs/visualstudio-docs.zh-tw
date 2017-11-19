---
title: "IDebugStackFrame::GetLanguageString |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugStackFrame.GetLanguageString
apilocation: jscript.dll
helpviewer_keywords: IDebugStackFrame::GetLanguageString
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 724ca98278eb8885d29aad1799f822ac57251597
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
傳回的短或長時間的文字描述的語言。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fLong`  
 [in]旗標，其中`TRUE`傳回詳細描述和`FALSE`傳回的簡短描述。  
  
 `pbstrLanguage`  
 [out]語言的描述。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 一般而言，如果`fLong`是`FALSE`，這個方法會提供相關聯的堆疊框架語言的名稱。 當`fLong`是`TRUE`，這個方法可能會提供完整的產品描述。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStackFrame 介面](../../winscript/reference/idebugstackframe-interface.md)