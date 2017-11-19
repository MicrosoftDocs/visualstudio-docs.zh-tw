---
title: "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e428f12b3d199603ac341a5e069fcc5ce5d36f93
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
通知主機有關指令碼執行階段錯誤時的處理序偵錯 Manager 找不到剛好在時間指令碼偵錯工具。  
  
 若要在主機中實作偵錯工具，您應該處理[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)。 根據使用者的動作，主機可以連接偵錯工具並傳回，或傳回 OnScriptErrorDebug 中偵錯工具的啟動`pfEnterDebugger`參數。 您也應該實作這個介面來取得有關執行階段錯誤的通知，即使解譯的程序進行偵錯管理員沒有外部偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 您也應該實作這個介面，以取得通知。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSiteDebugEx 介面](../../winscript/reference/iactivescriptsitedebugex-interface.md)