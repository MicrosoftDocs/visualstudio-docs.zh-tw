---
title: IDebugApplication::RemoveStackFrameSniffer | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.RemoveStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::RemoveStackFrameSniffer
ms.assetid: 00304b88-e435-4b87-a331-44e7492eb32d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1462ff1382f3ccb844ccc98c6e6eec676a86c669
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990777"
---
# <a name="idebugapplicationremovestackframesniffer"></a>IDebugApplication::RemoveStackFrameSniffer
移除此應用程式中的堆疊框架的列舉值提供者。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT RemoveStackFrameSniffer(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwCookie`  
 [in]傳回的 cookie`AddStackFrameSniffer`堆疊框架的列舉值提供者已新增的方法。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 `RemoveStackFrameSniffer`方法會移除此應用程式中的堆疊框架的列舉值提供者。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)   
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugStackFrameSniffer 介面](../../winscript/reference/idebugstackframesniffer-interface.md)