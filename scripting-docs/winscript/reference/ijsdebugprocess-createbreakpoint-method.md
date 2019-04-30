---
title: 'Ijsdebugprocess:: Createbreakpoint 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateBreakPoint
apilocation:
- jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b398b93c2e7b5ad43abd35d385407b39c0c980f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557968"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint 方法
在指定的文件的位置設定中斷點。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
 [in]IDebugDocumentText 的指標。  
  
 `characterOffset`  
 [in]從檔案開頭的字元位移。  
  
 `characterCount`  
 [in]應在其中插入中斷點的文件文字的長度。  
  
 `isEnabled`  
 [in]指定是否啟用中斷點。  
  
 `ppDebugBreakPoint`  
 [out]物件，表示所建立的中斷點。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugProcess 介面](../../winscript/reference/ijsdebugprocess-interface.md)