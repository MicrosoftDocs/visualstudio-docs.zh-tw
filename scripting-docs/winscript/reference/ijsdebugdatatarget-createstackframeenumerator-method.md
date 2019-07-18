---
title: 'Ijsdebugdatatarget:: Createstackframeenumerator 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.CreateStackFrameEnumerator
apilocation:
- jscript9diag.dll
ms.assetid: cda172e5-18d0-43c5-81d8-432ab30ee70d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8103ac689ac812aee2037f0f2e89f1d3a7448c6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583076"
---
# <a name="ijsdebugdatatargetcreatestackframeenumerator-method"></a>IJsDebugDataTarget::CreateStackFrameEnumerator 方法
建立堆疊框架的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CreateStackFrameEnumerator(  
   DWORD threadId,  
   IEnumJsStackFrames **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a>參數  
 `threadId`  
 [in]目標處理序中執行的執行緒。  
  
 `ppEnumerator`  
 [out]堆疊框架的列舉值。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)