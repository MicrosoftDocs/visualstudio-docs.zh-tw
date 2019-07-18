---
title: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c643478da37b5a66c22b201ef8f8248df02e4ec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992347"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
通知主機有關指令碼執行階段錯誤時的處理序偵錯管理員找不到 Just In Time 指令碼偵錯工具。  
  
 若要實作偵錯工具在您的主機，您應該處理[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)。 根據使用者動作，主機可以連接偵錯工具並傳回，或傳回 OnScriptErrorDebug 中偵錯工具啟動`pfEnterDebugger`參數。 您也應該實作這個介面來取得執行階段錯誤的相關通知，即使有可以處理序偵錯管理員解譯任何外部偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pErrorDebug`  
 [in]發生執行階段錯誤。  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 [out]是否要呼叫[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)如果使用者決定要繼續而不偵錯。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 您也應該實作這個介面來取得通知。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSiteDebugEx 介面](../../winscript/reference/iactivescriptsitedebugex-interface.md)