---
title: "Ijsdebugprocess:: Createbreakpoint 方法 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugProcess.CreateBreakPoint
apilocation: jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10d734f32d092d341dbb1b02a5cc7a0c127223a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint 方法
在指定的文件的位置設定中斷點。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>參數  
 `documentId`  
 [in]IDebugDocumentText 指標。  
  
 `characterOffset`  
 [in]從檔案開頭的字元位移。  
  
 `characterCount`  
 [in]應該在其中插入中斷點的文件文字的長度。  
  
 `isEnabled`  
 [in]指定是否啟用中斷點。  
  
 `ppDebugBreakPoint`  
 [out]物件，表示已建立的中斷點。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugProcess 介面](../../winscript/reference/ijsdebugprocess-interface.md)