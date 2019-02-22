---
title: IActiveScriptSiteDebug::OnScriptErrorDebug |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5680d22ffa5ec648afaced5e98f651e35758f929
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092114"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
可讓智慧主機，以判斷如何處理執行階段錯誤。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pErrorDebug`  
 [in]發生執行階段錯誤  
  
 `pfEnterDebugger`  
 [out]旗標，指出是否要將錯誤傳遞至偵錯工具進行 JIT 偵錯。  
  
 `pfCallOnScriptErrorWhenContinuing`  
 [out]旗標，指出是否要呼叫`IActiveScriptSite::OnScriptError`當使用者決定要繼續而不偵錯。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括但不限於下列資料表中的值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 智慧主機可以使用這個方法，以判斷如何處理執行階段錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSiteDebug 介面](../../winscript/reference/iactivescriptsitedebug-interface.md)